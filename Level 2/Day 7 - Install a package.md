# Question

As per new application requirements shared by the Nautilus project development team, serveral new packages need to be installed on all app servers in Stratos Datacenter. Most of them are completed except for strace.


Therefore, install the `strace` package on all `app-servers`.

# Step-by-Step Solution ( Perform in each app server)

### SSH into the App Server using your assigned user credentials (tony@stapp01, steve@stapp02, banner@stapp03).

### Install the strace Package

```bash

sudo yum install -y strace
```

(Or `sudo apt-get update && sudo apt-get install -y strace` if running an Ubuntu/Debian environment).

### Verify the Installation
Confirm that strace is installed and available in your system path:

```bash


strace -V
```

> Note: Be sure to repeat this installation process on all three servers: stapp01, stapp02, and stapp03.