# Question

The system admins team of xFusionCorp Industries has noticed intermittent issues with DNS resolution in several apps . App Server 1 in Stratos Datacenter is having some DNS resolution issues, so we want to add some additional DNS nameservers on this server.


As a temporary fix we have decided to go with Google public DNS (ipv4). Please make appropriate changes on this server.

# Step-by-Step Solution

Step 1: SSH into the Nautilus App Server 1
Use the credentials provided in your infrastructure details panel.

Step 2: Add Google Public DNS as Nameservers
Edit the resolv.conf file to add the new DNS servers:
Bash
```bash
sudo sed -i '/^nameserver/d' /etc/resolv.conf
sudo tee -a /etc/resolv.conf << EOF
nameserver 8.8.8.8
nameserver 8.8.4.4
EOF
```

Step 3: Verify DNS Configuration
Check that the file was updated correctly:
Bash
```bash
sudo cat /etc/resolv.conf
```

Expected Output:
```Plaintext
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Step 4: Test DNS Resolution (Optional)
Verify that DNS queries are working correctly:
Bash
```bash
sudo dig google.com
```

Step 5: Verify Timezone Alignment (If needed)
Ensure your local timezone matches the server timezone:
Bash
```bash
sudo timedatectl set-timezone Indian/Reunion
sudo timedatectl
```