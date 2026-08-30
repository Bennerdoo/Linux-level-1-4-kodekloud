# Question

During a routine security audit, the team identified an issue on the Nautilus App Server. Some malicious content was identified within the website code. After digging into the issue they found that there might be more infected files. Before doing a cleanup they would like to find all similar files and copy them to a safe location for further investigation. Accomplish the task as per the following requirements:

- a. On `App Server 2` at location `/var/www/html/media` find out all files (not directories) having `.js` extension.

- b. Copy all those files along with their parent directory structure to location `/media` on same server.

- c. Please make sure not to copy the entire `/var/www/html/media` directory content.

# Step-by-Step Solution

### SSH into App Server 2 using the credentials provided in your infrastructure details panel.

### Ensure the Target Directory Exists

Create the target directory `/media` if it doesn't already exist:

```Bash


sudo mkdir -p /media
```

### Locate and Copy .js Files with Parent Directory Structure
Navigate to `/var/www/html/media` and use `find` combined with `cp --parents` to search for regular files (`-type f`) with a `.js` extension and mirror their structure to `/media`:

```Bash


cd /var/www/html/media
sudo find . -type f -name "*.js" -exec cp --parents -t /media {} +
```

### (Alternative method using rsync:)

```Bash
sudo rsync -av --include='*/' --include='*.js' --exclude='*' /var/www/html/media/ /media/
```

### Verify the Relocated Files
Check that only .js files and their relative path structures were copied to /media:

```Bash


ls -laR /media
```

> **Note:** Changing into `/var/www/html/media` before executing `find . ...` ensures that relative paths are mirrored directly inside `/media` without duplicating `/var/www/html/media` into the destination path.