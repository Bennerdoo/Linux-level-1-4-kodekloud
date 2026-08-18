# Question

In the Stratos Datacenter, our application server 1 is encountering performance degradation due to excessive processes held by the nfsuser user. To mitigate this issue, we need to enforce limitations on its maximum processes. Please set the maximum process limits as specified below:


- a. Set the soft limit to 1025
- b. Set the hard limit to 2025

# Step by Step Solution

**SSH into App Server 1 using the credentials provided in your infrastructure details panel.**

**Open /etc/security/limits.conf for Editing**

**Append the limit configurations for nfsuser to /etc/security/limits.conf:**

```Bash


sudo tee -a /etc/security/limits.conf << 'EOF'
nfsuser soft nproc 1025
nfsuser hard nproc 2025
EOF
Verify the Configuration File

**Check that the entries were added correctly at the bottom of the file:**

Bash

```Bash
tail -n 5 /etc/security/limits.conf
```

**Expected output:**

```Plaintext

nfsuser soft nproc 1025
nfsuser hard nproc 2025
```

**Verify Limits for nfsuser (Optional)**
Switch to nfsuser or execute ulimit directly as nfsuser to confirm:

```Bash
sudo su - nfsuser -c "ulimit -Sn; ulimit -Hn" # for process limit checks: ulimit -Su; ulimit -Hu
```


**Expected output:**

```Plaintext

1025
2025
```

**Note**: The `nproc` item type controls the maximum number of processes allowed for the user. Setting explicit soft (1025) and hard (2025) limits prevents resource exhaustion on the application server.