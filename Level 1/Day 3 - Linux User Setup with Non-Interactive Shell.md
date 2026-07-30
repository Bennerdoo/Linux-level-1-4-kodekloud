# Question

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the AWS cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition.
- For this task, create one subnet named datacenter-subnet under default VPC.

# Step By Step solution

1.Navigate to the VPC Dashboard:AWS Management Console.

2. Log in to the AWS Management Console.In the top search bar, search for VPC and select it from the services list.

3. Identify Your Default VPC ID:VPC Console.

4. In the left navigation pane, click on Your VPCs.Look for the VPC marked Yes under the Default VPC column.Copy or note its VPC ID (e.g., vpc-0123456789abcdef0).

5. Open the Subnet Creation Form:Subnets Section.In the left navigation pane, click on Subnets.Click the orange Create subnet button at the top right.

6. Configure Subnet Settings:Subnet Details.Under VPC ID, select your Default VPC from the dropdown menu.In the Subnet settings section:Subnet name: 
Enter datacenter-subnet.

7. Availability Zone: 
Choose any preferred zone (e.g., us-east-1a) or leave it as No preference.

8. IPv4 CIDR block: 
Enter an unused CIDR block within your default VPC range (for example, if your default VPC is 172.31.0.0/16, you can enter 172.31.128.0/20 or any available sub-range).

9. Review and Create:
Finalize Subnet.Scroll to the bottom and click Create subnet.
Verify that datacenter-subnet now appears in your Subnets list marked as Available.VerificationOnce created, you can verify it in the console by going to VPC > Subnets and searching for datacenter-subnet. Confirm that its associated VPC ID matches your default VPC ID.
