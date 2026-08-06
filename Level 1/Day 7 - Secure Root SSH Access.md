# Question

Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.


Your task is to disable direct SSH root login on all app servers within the Stratos Datacenter.

# Step-by-Step Instructions (Perform on Each App Server)

1. ### SSH into the App Server using the user credentials provided in the infrastructure details panel.

2. ### Edit the OpenSSH Server Configuration
Open /etc/ssh/sshd_config with sudo:

```Bash


sudo sed -i 's/^#*PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config
```
(Or manually edit `/etc/ssh/sshd_config` using `sudo vi `/ `sudo nano` to set PermitRootLogin no.)

3. ### Validate SSH Configuration Syntax
Ensure there are no syntax errors in the configuration file:

```Bash


sudo sshd -t
```
4. ### Restart the SSH Service
Apply the changes by restarting sshd (or ssh, depending on the distribution):

```Bash


sudo systemctl restart sshd || sudo service sshd restart
```
5. ### Verify the Setting
Check that the setting is active in the running configuration:

```Bash


sudo sshd -T | grep -i permitrootlogin
```
**Expected output:** `permitrootlogin no`

**Note:** Make sure you perform these commands on all App Servers (`stapp01`, `stapp02`, `stapp03`) listed in your Stratos Datacenter lab environment to satisfy the requirement.