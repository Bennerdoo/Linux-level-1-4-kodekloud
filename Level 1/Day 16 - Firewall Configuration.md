# Question

The Nautilus system administrators team has rolled out a web UI application for their backup utility on the Nautilus application server 2 within the Stratos Datacenter. This application runs on port 3001and appropriate firewall rules must be configured to allow incoming traffic. To achieve this, firewalld needs to be installed and configured on the application server. To ensure proper functionality, the following requirements have been identified:


Install and enable the firewalld service.
Allow all incoming connections on port 3001/tcp.
Ensure the zone is set to public.

# Step-by-Step Solution

### Step 1

SSH into Nautilus App server 2.

### Step 2

**Install and enable firewalld:**

```Bash
sudo yum install firewalld -y
sudo systemctl enable --now firewalld
```

### Step 3

**Verify firewalld is running and the public zone is active:**

```Bash
sudo firewall-cmd --state
sudo firewall-cmd --get-active-zones
```

Expected output:

```Plaintext
running
public
```

### Step 4

**Allow traffic on port 3001/tcp in the public zone:**

```Bash
sudo firewall-cmd --zone=public --add-port=3001/tcp --permanent
```

### Step 5

**Reload firewall rules to apply changes:**

```Bash
sudo firewall-cmd --reload
```

### Step 6

**Verify that port 3001/tcp is allowed in the public zone:**

```Bash
sudo firewall-cmd --zone=public --list-ports
```

Expected output snippet:

```Plaintext
3001/tcp
```
