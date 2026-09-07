# Question

To secure our Nautilus infrastructure in Stratos Datacenter, we have decided to install and configure firewalld on one of the app servers named App Server 3. We have Apache and Nginx services running on these apps. Nginx is running as a reverse proxy server for Apache. We might have more robust firewall settings in the future, but for now we have decided to go with the given requirements listed below:


a. Allow all incoming connections on Nginx port, i.e 80.

b. Block all incoming connections on Apache port, i.e 8085.

c. All rules must be permanent.

d. Zone should be public.

e. If Apache or Nginx services aren't running already, please make sure to start them.

# Step by Step Solution

1.Update Apache Configuration to Port 8085:

- **Configuration fix.**
Modify Apache's configuration to listen on port 8085 instead of port 80:

```Bash
sudo sed -i 's/^Listen 80/Listen 8085/' /etc/httpd/conf/httpd.conf
```

- Verification: Run grep "^Listen" /etc/httpd/conf/httpd.conf to confirm it outputs Listen 8085.

2.Restart Apache and Start Nginx:

- **Service deployment.**
Restart httpd to free port 80, then start nginx:

```Bash
sudo systemctl restart httpd
sudo systemctl start nginx
```

- Verification: Check status for both services to ensure they are both active and running:

```Bash
sudo systemctl status httpd nginx
```


3.Configure and Enable Firewalld:

- **Final step.**
Once both web servers are active, configure the required firewall rules:

```Bash
# Install & enable firewalld
sudo yum install -y firewalld
sudo systemctl enable --now firewalld

# Allow port 80 in public zone
sudo firewall-cmd --zone=public --add-port=80/tcp --permanent

# Explicitly reject/block port 8085 in public zone
sudo firewall-cmd --zone=public --add-rich-rule='rule family="ipv4" port port="8085" protocol="tcp" reject' --permanent

# Apply changes
sudo firewall-cmd --reload
```

- **Verification**: Confirm the active firewall configuration using:

```Bash
sudo firewall-cmd --zone=public --list-all
```