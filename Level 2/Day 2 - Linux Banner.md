# Question

During the monthly compliance meeting, it was pointed out that several servers in the Stratos DC do not have a valid banner. The security team has provided serveral approved templates which should be applied to the servers to maintain compliance. These will be displayed to the user upon a successful login.


Update the message of the day on all application servers for Nautilus. Make use of the approved template located at `/home/thor/nautilus_banner` on the jump host.

# Step by Step Solution

### Step 1: Copy the Template from the Jump Host to All App Servers

From the Jump Host Server, transfer the /home/thor/nautilus_banner file to /tmp on App Server 1, App Server 2, and App Server 3 using scp (replace user with the corresponding server username, such as tony, steve, or banner):

```Bash

scp /home/thor/nautilus_banner user@stapp01:/tmp/nautilus_banner
scp /home/thor/nautilus_banner user@stapp02:/tmp/nautilus_banner
scp /home/thor/nautilus_banner user@stapp03:/tmp/nautilus_banner
```

### Step 2: Apply the Banner to /etc/motd on Each App Server

Log in to each application server (stapp01, stapp02, stapp03) and copy the file to /etc/motd:

SSH into the App Server:

```Bash

ssh user@stapp0<1|2|3>
```
Overwrite /etc/motd with the banner content:

```Bash

sudo cp /tmp/nautilus_banner /etc/motd
```

Verify the MOTD Content:

```Bash

cat /etc/motd
```

> The contents of `/etc/motd` are automatically displayed to users upon a successful interactive SSH login, fulfilling the security compliance requirement across all application servers.