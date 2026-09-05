# Question

As per details shared by the development team, the new application release has some dependencies on the back end. There are some packages/services that need to be installed on all app servers under Stratos Datacenter. As per requirements please perform the following steps:


a. Install nscd package on all the application servers.

b. Once installed, make sure it is enabled to start during boot.

# Step-by-Step Solution

### 1. Log in to App Servers

```bash
SSH into App Server 1, App Server 2, and App Server 3 using the credentials provided in your infrastructure details panel.


### 2. Install nscd Package

On each server, run:


```bash
sudo yum install nscd -y
```

### 3. Enable the nscd Service

On each server, enable the service to start at boot and start it immediately:


```bash
sudo systemctl enable nscd
sudo systemctl start nscd
```

### 4. Verify the Service Status

On each server, verify that nscd is running:


```bash
sudo systemctl is-enabled nscd
sudo systemctl status nscd
```