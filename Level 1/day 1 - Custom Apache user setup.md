# Question

In response to heightened security concerns, the `xFusionCorp Industries` security team has opted for custom Apache users for their web applications. Each user is tailored specifically for an application, enhancing security measures. Your task is to create a custom Apache user according to the outlined specifications:

- Create a user named `<username>` on `App server 3` within the Stratos Datacenter.
- Assign a unique UID `<lab-id>` and designate the home directory as `/var/www/`userName``.

> Note: You can find the infrastructure details by clicking on the **Details of all Users and Servers** button on the top-right section of the page.


## Solution
>username e.g jim
>lab-id stands for UID e.g 1207

### Step-by-Step Instructions

1. **SSH into App Server 3**  
   Use the hostname or IP address and credentials provided in the infrastructure details panel.

2. **Create the User with the Specified Parameters**  
   Run the following command to create the user, set the custom home directory, create the home directory if needed, and assign the required UID:

   ```bash
   sudo useradd -u 1207 -d /var/www/`username` -m `username`
   ```

3. **Verify User Details**  
   Confirm that the UID, default group, and home directory were assigned correctly:

   ```bash
   id `userName`
   ```

   Expected output:

   ```bash
   uid=1207(`userName`) gid=... groups=...
   ```

   Check the home directory ownership:

   ```bash
   ls -ld /var/www/`userName`
   ```

   Expected output: Ownership should reflect ``userName`:`userName`` (or ``userName``'s primary group) on `/var/www/`userName``.

### Key Notes

> **Permissions Check:** Ensure `/var/www/``userName` has appropriate ownership and read/execute permissions for Apache process access depending on your web app deployment configuration.
