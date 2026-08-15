# Question

With the installation of new tools on the app servers within the Stratos Datacenter, certain functionalities now necessitate graphical user interface (GUI) access.


Adjust the default runlevel on all App servers in Stratos Datacenter to enable GUI booting by default. It's imperative not to initiate a server reboot after completing this task.

# Step By Step Solution 

**Perform in App Servers 1, 2 and 3**

## 1. SSH into the App Server using the credentials provided in the infrastructure details panel.

## 2. Set the Default Systemd Target to Graphical
Change the default runlevel target to graphical.target:

```Bash
sudo systemctl set-default graphical.target
```

## 3. Verify the Default Target

Confirm that the default target has been updated correctly:

```Bash
systemctl get-default
```

Expected output: `graphical.target`

**Note:** ***Do not reboot the servers after making this change, as required by the specifications.***


