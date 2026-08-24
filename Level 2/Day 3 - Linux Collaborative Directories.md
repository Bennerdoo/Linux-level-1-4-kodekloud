# Question

The Nautilus team doesn't want its data to be accessed by any of the other groups/teams due to security reasons and want their data to be strictly accessed by the `devops` group of the team.


Setup a collaborative directory `/devops/data` on `app server 2` in `Stratos Datacenter`.

The directory should be group owned by the group `devops` and the group should own the files inside the directory. The directory should be `read/write/execute` to the user and group owners, and `others` should not have any access.

# Step By Step Solution

1. SSH into the `app server 2` using the credentials provided in the Details of all Users and Servers section.

2. Create the `devops` group (if it doesn't exist already):

```Bash


sudo groupadd devops
```

3. Create the collaborative directory `/devops/data`:

```Bash


sudo mkdir -p /devops/data
```

4. **Change Group Ownership:** Set the group owner of the directory to `devops`.

```Bash


sudo chgrp devops /devops/data
```

5. **Set Permissions:** Grant `rwx` for the owner and group, and no permissions for others.

```Bash


sudo chmod 770 /devops/data
```

**Verification:**
Check the permissions to ensure they match the requirements:

```Bash


ls -ld /devops/data
```

Expected Output: `drwxrwx--- 2 root devops ... /devops/data` (or similar, with root/devops ownership and `rwx` permissions).
