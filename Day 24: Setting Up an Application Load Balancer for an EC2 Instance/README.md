###Step 1: Create the security group for ALB
- We create the xfusion-sg security group in the default VPC
- Inbound rule: HTTP port 80 from anywhere IPV4
<img width="1088" height="506" alt="image" src="https://github.com/user-attachments/assets/68861128-dddd-4d3b-aef1-2850362fe792" />

###Step 2: Create the target group for the ALB
- We create the xfusion-tg target group for instances
- We register our EC2 instance to the target group (to add more instances later or add an autoscaling group)
- Our target group is now ready to be attached to an ALB
<img width="1076" height="456" alt="image" src="https://github.com/user-attachments/assets/bda2cf85-bcb0-41ed-8adf-971c4ba0705c" />

###Step 3: Create the ALB
- We create the xfusion-alb ALB
- Attach the security group and target group created previously
- Ensure the availability zones match the one the EC2 is in (this case us-east-1d should be selected)
<img width="1080" height="312" alt="image" src="https://github.com/user-attachments/assets/b154cf98-5ea7-4431-a463-c645074e88d0" />

###Step 4: Check EC2 security group allows inbound traffic from ALB
- We review our EC2 security group. On inspection it shows that it allows all inbound traffic on all ports.
<img width="1073" height="179" alt="image" src="https://github.com/user-attachments/assets/b10ba2fb-7080-45c5-a5f9-a87114c9f6c5" />

- We edit this to allow inbound traffic from ALB on port 80 (This is a security measure for our EC2)
- Our EC2 security group now allows HTTP traffic on port 80 from ALB security group
<img width="1052" height="190" alt="image" src="https://github.com/user-attachments/assets/78c19529-5f74-4174-ac38-7ce6e7fbcd5c" />

###Step 5: Test our web page
- We copy the DNS name of ALB and paste it on a new browser tab
<img width="855" height="291" alt="image" src="https://github.com/user-attachments/assets/1469fa8e-ade0-4cb6-b335-2a9a78cfe796" />






