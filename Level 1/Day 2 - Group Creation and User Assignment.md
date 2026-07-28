# Question

The system admin team at xFusionCorp Industries has streamlined access management by implementing group-based access control. Here's what you need to do:


a. Create a group named nautilus_admin_users across all App servers within the Stratos Datacenter.

b. Add the user jarod into the nautilus_admin_users group on all App servers. If the user doesn't exist, create it as well.
Note: You can find the infrastructure details by clicking on the Details of all Users and Servers button on the top-right section of the page.

# Step By Step Solution - Perform in app server 1, 2 and 3

1. SSH into the App Server using the credentials from the Details of all Users and Servers section.

2. Create the Group
   Create the target group nautilus_admin_users:

```Bash


sudo groupadd nautilus_admin_users
```

3. Check/Create the User jarod and Add to Group
   Check if user jarod exists:

```Bash


id jarod
```

4. If jarod DOES NOT exist: Create the user and assign them directly to nautilus_admin_users as a secondary group:

```Bash


sudo useradd -G nautilus_admin_users jarod
```
5. If jarod DOES exist: Append nautilus_admin_users to their secondary groups (using -aG so existing group memberships aren't overwritten):

```Bash


sudo usermod -aG nautilus_admin_users jarod
```

6. Verify the Setup  
   Confirm jarod belongs to the new group:

```Bash


id jarod
```

Expected output includes: `groups=...(nautilus_admin_users)`

>Tip for Speed: Repeat these steps for all App Servers in your Stratos Datacenter lab environment.

