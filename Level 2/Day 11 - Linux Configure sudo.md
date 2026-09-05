# Question

We have some users on all app servers in Stratos Datacenter. Some of them have been assigned some new roles and responsibilities, therefore their users need to be upgraded with sudo access so that they can perform admin level tasks.


a. Provide sudo access to user yousuf on all app servers.

b. Make sure you have set up password-less sudo for the user.

# Step By Step Solution(Perform on Each App Server)

### SSH into the App Server:

using your assigned user credentials (tony for stapp01, steve for stapp02, banner for stapp03):

```Bash


ssh <user>@stapp0<1|2|3>
```

### Create a Dedicated Sudoers Entry for yousuf
Add a configuration file inside /etc/sudoers.d/ using tee:

```Bash


echo "yousuf ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/yousuf

```

### Set Proper File Permissions
Ensure the newly created file has strict permissions (0440), as required by sudo:

```Bash


sudo chmod 0440 /etc/sudoers.d/yousuf
```
### Verify the Sudoers Syntax
Run visudo check to verify there are no syntax errors in the configuration files:

```Bash


sudo visudo -c
```

Expected output: /etc/sudoers.d/yousuf: parsed OK

### Test Passwordless Sudo Access

Switch to user yousuf (or execute a command as yousuf) to verify that sudo executes without prompting for a password:

```Bash


sudo sudo -u yousuf sudo -n true
```

(If no error or password prompt is returned, passwordless sudo is working as expected).

> **Note:** Repeat these steps on all three application servers (stapp01, stapp02, and stapp03). Creating dedicated files under /etc/sudoers.d/ is preferred over editing /etc/sudoers directly, as it preserves system upgrades and minimizes syntax corruption risks.

