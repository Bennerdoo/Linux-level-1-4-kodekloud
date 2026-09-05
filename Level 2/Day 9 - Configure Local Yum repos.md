# Question

The Nautilus production support team and security team had a meeting last month in which they decided to use local yum repositories for maintaing packages needed for their servers. For now they have decided to configure a local yum repo on Nautilus Backup Server. This is one of the pending items from last month, so please configure a local yum repository on Nautilus Backup Server as per details given below.


a. We have some packages already present at location `/packages/downloaded_rpms/` on Nautilus Backup Server.

b. Create a yum repo named `local_yum` and make sure to set `Repository ID` to `local_yum`. Configure it to use package's location `/packages/downloaded_rpms/`.

c. Install package `samba` from this newly created repo.

# Step by Step Solution

### SSH into the Nautilus Backup Server

Use the backup server credentials provided in your infrastructure details panel.

### Create the /etc/yum.repos.d Directory

```Bash


sudo mkdir -p /etc/yum.repos.d
```

### Create the local_yum.repo File

```Bash


sudo tee /etc/yum.repos.d/local_yum.repo << 'EOF'
[local_yum]
name=local_yum
baseurl=file:///packages/downloaded_rpms/
enabled=1
gpgcheck=0
EOF
```

### Re-build Yum Cache

```Bash


sudo yum clean all
sudo yum makecache
```

### Install samba from local_yum

```Bash


sudo yum --disablerepo="*" --enablerepo="local_yum" install -y samba
```

### Verify the Installation

```Bash


rpm -qi samba
```