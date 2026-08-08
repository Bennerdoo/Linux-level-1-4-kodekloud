# Question

The jump host server hosts a directory named /data, serving as a repository for various developers non-confidential data. Developer james has requested a copy of their data stored in /data/james. The System Admin team has provided the following steps to fulfill this request:


- a. Create a compressed archive named james.tar.gz of the /data/james directory.
- b. Transfer the archive to the /home directory on the Jump Host Server.

# Step-by-Step Solution

## 1. Create the Compressed Archive and Save directly to /home
Run the tar command with gzip compression (-z) to create (-c) the archive in /home/james.tar.gz from the source path /data/james:

```Bash

sudo tar -czvf /home/james.tar.gz -C /data james
```

(Note: Using -C /data james archives the directory structure cleanly without embedding absolute root path prefixes).

## Verify Archive Creation
Confirm that the archive was created in /home and inspect its size:

```Bash


ls -lh /home/james.tar.gz
```

## 3. Verify Archive Contents
Ensure the contents inside the tarball are intact:

```Bash


tar -tzvf /home/james.tar.gz
```