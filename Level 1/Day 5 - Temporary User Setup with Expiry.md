# Question

As part of the temporary assignment to the Nautilus project, a developer named mariyam requires access for a limited duration. To ensure smooth access management, a temporary user account with an expiry date is needed. Here's what you need to do:


Create a user named mariyam on App Server 3 in Stratos Datacenter. Set the expiry date to 2027-02-17, ensuring the user is created in lowercase as per standard protocol.
Note: You can find the infrastructure details by clicking on the Details of all Users and Servers button on the top-right section of the page.

# Step-by-step solution

1. **SSH into required App Server** using the credentials from the Details of all Users and Servers section.

2. **Create the User with an Expiry Date**
Use useradd with the -e flag (format YYYY-MM-DD):

```Bash


sudo useradd -e 2027-02-17 mariyam
```
>**Note:** If the user mariyam already exists from a previous task, modify the existing account expiry date instead using `sudo chage -E 2027-02-17 mariyam` or `sudo usermod -e 2027-02-17 mariyam`

3. **Verify the Account Expiry Date**
Check the account aging information using chage:

```Bash


sudo chage -l mariyam
```
Expected output snippet:

```Plaintext


Account expires : Feb 17, 2027
```
>***Note:*** The system will automatically lock access for mariyam on February 17, 2027, preventing any further logins while preserving the account configuration.