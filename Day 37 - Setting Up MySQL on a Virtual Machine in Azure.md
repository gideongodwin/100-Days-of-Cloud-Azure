## Day 37: Setting Up MySQL on a Virtual Machine in Azure

#### Task Details:
The Nautilus DevOps team is tasked with integrating a PHP application hosted on an Azure VM with a MySQL database hosted on another Azure VM. This will validate the application's ability to connect to the database in the cloud.

Create the MySQL VM:

Create a VM named devops-mysql-vm using the MySQL Jetware image from the Azure Marketplace.
Configure the VM in the Central US region.
Use Password as the authentication type.
Set the username as devops_admin and the password as Namin@123456.
Allow inbound traffic on port 3306 to enable MySQL access.
Setup the MySQL Database:

SSH into the devops-mysql-vm.
Use the sudo /jet/enter mysql command to access the MySQL shell.
Create a database named devops_db.
Create a MySQL user named devops_user with password password123.
Grant all privileges on the devops_db database to this user.
PHP VM Setup:

A VM named devops-php-vm already exists in the East US region.
This VM is hosting a PHP application and contains a pre-existing db_test.php file in the /var/www/html/ directory.
Database Connection Configuration:

Retrieve the public IP address of the devops-mysql-vm.
Update the database connection settings in the db_test.php file to use the MySQL credentials and public IP address of the devops-mysql-vm.
Validation:Access the db_test.php file from the devops-php-vm using its public IP address.
Ensure the file displays the message Connected successfully, confirming the connection between the PHP application and the MySQL database.

#### STEPS:
1. Sign in to the [Azure Portal](https://portal.azure.com/)
2. From the Virtual Network dashboard, click on create button

<img width="652" height="362" alt="Screenshot 2026-03-10 113634" src="https://github.com/user-attachments/assets/46509c7b-4454-49ca-a4d2-b8a7cd472316" />

3. On the Basics tab, enter the VM name and select the appropriate region.
4. Select the MySQL Jetware image from the Azure Marketplace
 <img width="627" height="506" alt="Screenshot 2026-03-10 114209" src="https://github.com/user-attachments/assets/7ed8b1dc-fd03-487c-be5b-2acdaff86e54" />
 <img width="582" height="145" alt="Screenshot 2026-03-10 134235" src="https://github.com/user-attachments/assets/90bde596-4d3e-488a-b4e5-cb7aa1abaf2d" />

5. Use Password as the authentication type.
<img width="585" height="174" alt="Screenshot 2026-03-10 144538" src="https://github.com/user-attachments/assets/3df23f09-333c-4cc9-a888-7f8bc6ba482d" />

6. Allow Inbound Traffic on Port 3306
   <img width="638" height="538" alt="Screenshot 2026-03-10 145641" src="https://github.com/user-attachments/assets/d1fb51a5-961a-4ca7-be8e-0204cfc52054" />

7.  SSH into `devops-mysql-vm` and Set Up the Database \
   `ssh devops_admin@<MYSQL_VM_PUBLIC_IP>`

8. Once inside the VM, run these commands:
```
# Access the MySQL shell via Jetware
sudo /jet/enter mysql

# Inside MySQL shell — run the following SQL commands:
CREATE DATABASE devops_db;

CREATE USER 'devops_user'@'%' IDENTIFIED BY 'password123';

GRANT ALL PRIVILEGES ON devops_db.* TO 'devops_user'@'%';

FLUSH PRIVILEGES;

exit;
```
9. SSH into the PHP VM and update the config file `db_test.php file` \
    `ssh azureuser@<PHP_VM_PUBLIC_IP>`
10.  Edit the `db_test.php` file \
    `sudo vi /var/www/html/db_test.php`
11. Replace the contents of `db_test.php` with:
```
<?php
$servername = "<MYSQL_VM_PUBLIC_IP>";   // Public IP of devops-mysql-vm
$username   = "devops_user";
$password   = "password123";
$dbname     = "devops_db";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";
?>
```

12. Save and exit
13. Validate the connection, Open a web browser and navigate to:
    `<PHP_VM_PUBLIC_IP>/db_test.php`
    



