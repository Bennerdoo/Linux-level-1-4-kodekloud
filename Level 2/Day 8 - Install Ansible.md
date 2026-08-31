# Question

During the weekly meeting, the Nautilus DevOps team discussed about the automation and configuration management solutions that they want to implement. While considering several options, the team has decided to go with Ansible for now due to its simple setup and minimal pre-requisites. The team wanted to start testing using Ansible, so they have decided to use `jump host` as an `Ansible controller` to test different kind of tasks on rest of the servers.


Install `ansible` `version 4.7.0` on `Jump host` using `pip3` only. Make sure Ansible binary is available globally on this system, i.e all users on this system are able to run Ansible commands.

# Step by Step Solution

Log in to the Jump Host as a user with sudo privileges (e.g., thor).

### Ensure pip3 is Available

Verify pip3 is installed on the system: 

```bash
pip3 --version
```

(If not installed, install it using `sudo yum install -y python3-pip` or `sudo apt install -y python3-pip` depending on the system distribution).

### Install Ansible 4.7.0 Globally via pip3

Run pip3 as root (or with sudo) so the binaries and Python modules are installed into shared system directories (e.g., `/usr/local/bin` or `/usr/bin`), making them accessible to all users:

```bash
sudo pip3 install ansible==4.7.0
```

(If using a modern OS that enforces PEP 668 managed environments, append `--break-system-packages`: `sudo pip3 install ansible==4.7.0 --break-system-packages`)

### Verify the Installation and Path

Confirm that Ansible version 4.7.0 is installed globally:

```bash
ansible --version
```

Expected output snippet: 

```Plaintext
ansible 4.7.0
```

### Ensure Binary Accessibility for All Users (Optional Check)

Check where the ansible binary was installed:

```bash
which ansible
```

If it is located in `/usr/local/bin` and that directory is not in your system-wide PATH, ensure `/usr/local/bin` is added to `/etc/profile` or `/etc/environment` so every user can execute it seamlessly.