# Question

A Nautilus developer has stored confidential data on the jump host within Stratos DC. To ensure security and compliance, this data must be transferred to one of the app servers. Given developers lack direct access to these servers, the system admin team has been enlisted for assistance.


Copy `/tmp/nautilus.txt.gpg` file from jump server to `App Server 3` placing it in the directory `/home/app`

# Step-by-step Solution

### 1. Transfer the File via SCP
Use `scp` to copy the file to App Server 3's `/home/app` directory.
- Replace `stapp03` with the target hostname and use the appropriate admin username for the required App Server (e.g., banner or as listed in your infrastructure details):

```Bash


scp /tmp/nautilus.txt.gpg banner@stapp03:/tmp/
```

### 2. Move to Target Directory on App Server 3
SSH into App Server 3 and move the file into /home/app with sudo permissions:

```Bash


ssh banner@stapp03

sudo mv /tmp/nautilus.txt.gpg /home/app/
```
(Alternatively, if direct permission allows, copy directly to /home/app using `scp /tmp/nautilus.txt.gpg banner@stapp03:/home/app/`)

### 3. Verify File Location and Ownership
On App Server 3, confirm the file exists in the destination directory:

```Bash


ls -la /home/app/nautilus.txt.gpg
```
**Note:** ***If prompted for password during scp, enter the standard user password for the App Server 3 user account provided in your environment details panel.***