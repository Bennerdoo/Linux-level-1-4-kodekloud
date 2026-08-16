# Question

In the daily standup, it was noted that the timezone settings across the Nautilus Application Servers in the Stratos Datacenter are inconsistent with the local datacenter's timezone, currently set to Indian/Reunion.


Synchronize the timezone settings to match the local datacenter's timezone (Indian/Reunion).

# Step by Step Solution (Perform on Each App Server)

### 1. SSH into the App Server using the credentials provided in the infrastructure details panel.

### 2. Set the Timezone using timedatectl
Run the timedatectl command to update the system timezone:

```Bash


sudo timedatectl set-timezone Indian/Reunion
```
### 3. Verify the Timezone Setting
Check that the timezone was updated successfully:

```Bash


timedatectl
```
Expected output snippet:

```Plaintext


Time zone: Indian/Reunion (+04, +0400)
```
**Note:** ***timedatectl automatically updates the /etc/localtime symlink in place, so no service restarts or server reboots are required.***

