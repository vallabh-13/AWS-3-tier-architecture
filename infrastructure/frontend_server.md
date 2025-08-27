# Follow these installation steps on the AMI EC2 instance:

## Install Nginx server and git
```
sudo dnf install nginx -y
sudo dnf install git -y
```
Replace the server block in /etc/nginx/nginx.conf with the content from the nginx_config file.

## Add the following EC2 instance userdata to the Launch Template:

```
#!/bin/bash
sed -i 's/update-me/internal-demo-backend-ALB-1662229117.us-east-2.elb.amazonaws.com/g' /etc/nginx/nginx.conf
sudo systemctl start nginx
cd /usr/share/nginx/html
sudo git clone https://github.com/vallabh-13/AWS-3-tier-architecture.git
mv /usr/share/nginx/html/AWS-3-tier-architecture/frontend/* /usr/share/nginx/html/
sudo rm -rf /usr/share/nginx/html/AWS-3-tier-architecture

```



