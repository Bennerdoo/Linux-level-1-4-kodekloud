# Question

In alignment with security compliance standards, the Nautilus project team has opted to impose restrictions on crontab access. Specifically, only designated users will be permitted to create or update cron jobs.


Configure crontab access on App Server 3 as follows:
- Allow crontab access to kareem user while denying access to the rod user.

# Step-by-Step Solution

### Step 1

SSH into App Server 3 using the credentials from the Details of all Users and Servers section.

### Step 2

**Allow User kareem**

Add kareem to /etc/cron.allow. When /etc/cron.allow exists, system access is restricted only to users explicitly listed in this file:

```Bash


echo "kareem" | sudo tee -a /etc/cron.allow
```


### Step 3

**Deny User rod**

Add rod to /etc/cron.deny:

```Bash


echo "rod" | sudo tee -a /etc/cron.deny

```

### Step 4

**Verify Configurations**

Confirm that the files contain the expected usernames:

```Bash


cat /etc/cron.allow
cat /etc/cron.deny

```

### Step 5

**How Cron Permissions Work:**

If `/etc/cron.allow` exists, only users listed in it are allowed to use crontab, regardless of whether they are in `/etc/cron.deny`. Explicitly adding `kareem` to `cron.allow` and `rod` to `cron.deny` satisfies both criteria.