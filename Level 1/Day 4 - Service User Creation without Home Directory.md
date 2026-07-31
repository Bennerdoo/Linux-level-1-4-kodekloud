# Question

In response to the latest tool implementation at xFusionCorp Industries, the system admins require the creation of a service user account. Here are the specifics:


- Create a user named john in App Server 3 without a home directory.
Note: You can find the infrastructure details by clicking on the Details of all Users and Servers button on the top-right section of the page.

# Step-by-step solution

### Step 1

**SSH into your recommended app server** using the credentials provided in the Details of all Users and Servers section.

### Step 2

**Create User Without a Home Directory**
Use the useradd command with the -M (or --no-create-home) flag:

```Bash


sudo useradd -M john
```

### Step 3

**Verify the Configuration**
Check /etc/passwd and /home to confirm the account setup:

```Bash


grep john /etc/passwd
```

**Expected output:** 
```Bash
john:x:1002:1002::/home/john:/bin/bash (Note: the line may list a default home path string, but no physical directory is created).
```

### Step 4

**Verify no home directory was created on disk:**

```Bash


ls -d /home/john
```
**Expected output:** 
```Bash
ls: cannot access '/home/john': No such file or directory
```

**Note:** The -M flag ensures the user entry is added to system databases for service ownership without wasting disk space or lea