# Question

Following a security audit, the xFusionCorp Industries security team has opted to enhance application and server security with SELinux. To initiate testing, the following requirements have been established for App server 2 in the Stratos Datacenter:


Install the required SELinux packages.

Permanently disable SELinux for the time being; it will be re-enabled after necessary configuration changes.

No need to reboot the server, as a scheduled maintenance reboot is already planned for tonight.

Disregard the current status of SELinux via the command line; the final status after the reboot should be disabled.

# Step by step Solution

### 1. SSH into App Server 2

Use the credentials provided in your infrastructure details panel to SSH into App Server 2.

### 2. Install the SELinux Management Packages

Install the standard SELinux utilities and policy packages:

#### Bash

```Bash


sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils libselinux-utils
```

(Or `sudo apt-get install -y selinux-policy-default policycoreutils` if using an Ubuntu/Debian environment).

### 3. Permanently Disable SELinux in Configuration

Update `/etc/selinux/config` (or `/etc/sysconfig/selinux`) so SELinux stays disabled after the scheduled reboot:

#### Bash

```Bash


sudo sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/selinux/config
```

### 4. Verify the Configuration File

Confirm that the configuration file reflects `SELINUX=disabled`:

#### Bash

```Bash


grep '^SELINUX=' /etc/selinux/config
```

**Expected output:** `SELINUX=disabled`

**Note:** Do not reboot the server or force a runtime state change using `setenforce`. The prompt specifically requires setting the configuration file so that SELinux evaluates to disabled upon the upcoming maintenance reboot.
