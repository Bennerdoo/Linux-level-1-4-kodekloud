# Question

Due to an accidental data mix-up, user data was unintentionally mingled on Nautilus App Server 2 at the /home/usersdata location by the Nautilus production support team in Stratos DC. To rectify this, specific user data needs to be filtered and relocated. Here are the details:


- Locate all files (excluding directories) owned by user kareem within the 
`/home/usersdata` directory on App Server 2. 
- Copy these files while preserving the directory structure to the /blog directory.

# Step-by-Step Solution

1. **SSH into App Server 2** using the credentials from the Details of all Users and Servers section.

2. **Ensure the Destination Directory Exists**
Create the target directory /blog if it does not already exist:

Bash

```Bash


sudo mkdir -p /blog
```

3. **Locate and Copy Files Preserving Directory Structure**
Use find with cp --parents to search /home/usersdata for regular files (-type f) owned by kareem (-user kareem) and copy them to /blog:

```Bash


cd /home/usersdata
sudo find . -type f -user kareem -exec cp --parents -t /blog {} +
```

**Alternatively, using rsync or tar:**

```Bash
sudo find /home/usersdata -type f -user kareem | sudo cpio -pdm /blog
```

4. **Verify the Relocated Files**
Check that the files were copied under /blog along with their parent paths:

```Bash


ls -laR /blog
```

**Note:** Navigating into /home/usersdata first before running find . -exec cp --parents -t /blog {} + guarantees that the relative path layout is mirrored cleanly under /blog without repeating the full /home/usersdata prefix in the destination.