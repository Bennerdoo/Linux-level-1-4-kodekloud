# Question

xFusionCorp Industries has planned to set up a common email server in Stork DC. After several meetings and recommendations they have decided to use postfix as their mail transfer agent and dovecot as an IMAP/POP3 server. We would like you to perform the following steps:


1. Install and configure postfix on Stork DC mail server.

2. Create an email account `javed@stratos.xfusioncorp.com` identified by `TmPcZjtRQx`.

3. Set its mail directory to `/home/javed/Maildir`.

4. Install and configure dovecot on the same server.

# Step-by-Step Solution

Ensure you are logged into the Stork DC mail server (stmail01) as the root user before beginning. If you are on the jump host, you can access it and switch to root using:Bash

```
ssh groot@stmail01
sudo -i
```

### 1.Install and configure Postfix:Stork DC mail server.

First, install the Postfix Mail Transfer Agent. After installation, append the required domain and interface configurations to main.cf so it listens on all interfaces and stores mail in the Maildir/ format.

```Bash
# Install Postfix
yum install -y postfix
```

```Bash
# Comment out the default localhost interface binding
sed -i 's/^inet_interfaces = localhost/#inet_interfaces = localhost/' /etc/postfix/main.cf

# Append the xFusionCorp domain and mailbox configurations
cat <<EOF >> /etc/postfix/main.cf
myhostname = stmail01.stratos.xfusioncorp.com
mydomain = stratos.xfusioncorp.com
myorigin = \$mydomain
inet_interfaces = all
mydestination = \$myhostname, localhost.\$mydomain, localhost, \$mydomain
home_mailbox = Maildir/
EOF

# Start and enable the service
systemctl restart postfix
systemctl enable postfix
```

### 2.Create the email account:javed@stratos.xfusioncorp.com.

Create the local Linux user account for javed. Because we already told Postfix to use the $mydomain origin in Step 1, creating a local user will automatically map to javed@stratos.xfusioncorp.com.

```Bash
# Create the user
useradd javed

# Set the requested password securely
echo "TmPcZjtRQx" | passwd --stdin javed
```

### 3.Set the mail directory:/home/javed/Maildir.

While Postfix will automatically create the Maildir/ folder the first time it delivers an email, it is best practice to explicitly construct it now with the correct ownership so Dovecot can read it.

```Bash
mkdir -p /home/javed/Maildir
chown -R javed:javed /home/javed/Maildir
chmod -R 700 /home/javed/Maildir
```

### 4.Install and configure Dovecot:IMAP/POP3 Server.

Finally, install Dovecot and configure it to read from the Maildir format we just specified.

```Bash
# Install Dovecot
yum install -y dovecot

# Specify the IMAP and POP3 protocols
sed -i 's|^#protocols = imap pop3 lmtp submission|protocols = imap pop3|' /etc/dovecot/dovecot.conf

# Point Dovecot to the Maildir location
echo "mail_location = maildir:~/Maildir" >> /etc/dovecot/conf.d/10-mail.conf

# Start and enable the service
systemctl restart dovecot
systemctl enable dovecot
```

Once complete, verify that both services are running smoothly by checking `systemctl status postfix` and `systemctl status dovecot`.  