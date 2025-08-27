# Follow these installation steps on the AMI EC2 instance:

## Install PHP, Apache, and MySQL client:
https://docs.aws.amazon.com/linux/al2023/ug/ec2-lamp-amazon-linux-2023.html

## Install git:
```
sudo dnf install git -y
```

## Add the following EC2 instance userdata to the Launch Template:

```
sudo systemctl start httpd
cd /var/www/html
sudo git clone https://github.com/vallabh-13/AWS-3-tier-architecture.git
sudo mkdir api
sudo mv AWS-3-tier-architecture/backend/api/* api/
sudo rm -rf AWS-3-tier-architecture
sed -i 's/update-me-host/insert-your-database-host-here/g' api/db_connection.php
sed -i 's/update-me-username/insert-your-database-username-here/g' api/db_connection.php
sed -i 's/update-me-password/insert-your-database-password-here/g' api/db_connection.php

```
