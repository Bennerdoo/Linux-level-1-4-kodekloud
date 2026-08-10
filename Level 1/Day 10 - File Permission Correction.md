# Question

After conducting a security audit within the Stratos DC, the Nautilus security team discovered misconfigured permissions on critical files. To address this, corrective actions are being taken by the production support team. Specifically, the file named /etc/hosts on Nautilus App 1 server requires adjustments to its Access Control Lists (ACLs) as follows:


1. The file's user owner and group owner should be set to root.

2. Others should possess read only permissions on the file.

3. User anita must not have any permissions on the file.

4. User jerome should be granted read only permission on the file.

# Step-by-Step Solution

1. ## SSH into Nautilus App 1 server

2. ## Set the file's user and group owner to root:
```Bash
sudo chown root:root /etc/hosts
```

3. ## Set the file's permissions:
```Bash
sudo chmod 644 /etc/hosts
```

4. ## Remove all permissions for user anita:
```Bash
sudo setfacl -x u:anita /etc/hosts
```

5. ## Grant read-only permission to user jerome:
```Bash
sudo setfacl -m u:jerome:r-- /etc/hosts
```

6. ## Verify the changes:
```Bash
getfacl /etc/hosts
```