## Step 1: Launch the EC2 Instance
We create the instance `xfusion-ec2`
- Ubuntu Server
- t3.micro

Add user data
```
#!/bin/bash
apt update -y
apt install nginx -y
systemctl enable nginx
systemctl start nginx
echo "<h1>Hello from NGINX on Ubuntu!</h1>" > /var/www/html/index.html
```
<img width="1080" height="103" alt="image" src="https://github.com/user-attachments/assets/f9c12aa1-b647-47f0-88e3-7a7534ca42c4" />

## Step 2: Check Security Group
Ensure Security group allows: 
- HTTP access on port 80
- SSH access on port 22
<img width="1069" height="209" alt="image" src="https://github.com/user-attachments/assets/cdabc189-08a3-44ee-b454-2dc767d8687b" />

## Test on a new browser
Once EC2 has passed 2/2 checks we test on a browser
<img width="636" height="182" alt="image" src="https://github.com/user-attachments/assets/b7f7f578-a47b-49ee-999a-177b018de27d" />
