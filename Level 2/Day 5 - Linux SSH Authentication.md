# Question

The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure the thor user on jump host has password-less SSH access to all app servers through their respective sudo users (i.e tony for app server 1). Based on the requirements, perform the following:


Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.

# Step-by-Step Solution (Perform in each app server)

### Step 1: Generate an SSH Key Pair (if one does not already exist)

Press Enter to accept the default file location `~/.ssh/id_rsa` and leave the passphrase empty when prompted:

Bash

```Bash
ssh-keygen -t rsa -N "" -f ~/.ssh/id_rsa
```

### Step 2: Copy the Public Key to Each App Server

Use `ssh-copy-id` to transfer thor's public key to the respective user accounts on each application server. Enter the password for each user when prompted:

**App Server 1 (stapp01 / User: tony)**

Bash

```Bash
ssh-copy-id tony@stapp01
```

**App Server 2 (stapp02 / User: steve)**

Bash

```Bash
ssh-copy-id steve@stapp02
```

**App Server 3 (stapp03 / User: banner)**

Bash

```Bash
ssh-copy-id banner@stapp03
```

### Step 3: Verify Passwordless Connection

Test connecting to each server to verify that SSH logs in without asking for a password:

Bash

```Bash


ssh tony@stapp01 "hostname"
ssh steve@stapp02 "hostname"
ssh banner@stapp03 "hostname"
```

> Note: If server hostnames do not resolve via SSH directly, replace stapp01, stapp02, and stapp03 with their respective internal IP addresses provided in your environment details panel.