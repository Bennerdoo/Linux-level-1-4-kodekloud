# Question

The `Nautilus` system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in `Stratos DC` on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:



a. Install `cronie` package on all `Nautilus` app servers and start `crond` service.

b. Add a cron `*/5 * * * * echo hello > /tmp/cron_text` for `root` user.

# Step-by-Step Solution (Perform on Each App Server)

On each Nautilus app server, run the following as root:

### 1. Install cronie

```Bash
yum install -y cronie
```


### 2. Start and enable crond

```Bash
systemctl enable --now crond
```


### 3. Add the cron job for root

```Bash
(crontab -l 2>/dev/null; echo "*/5 * * * * echo hello > /tmp/cron_text") | crontab -
```

### 4. Verify

```Bash
systemctl status crond
crontab -l
```

You should see:

```Plaintext
*/5 * * * * echo hello > /tmp/cron_text
```

### 5. After the next 5-minute interval, verify:

```Bash
cat /tmp/cron_text
```

Expected output:

```Plaintext
hello
```
