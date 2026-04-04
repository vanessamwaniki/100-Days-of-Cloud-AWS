## Create VPC
- Name 'devops-pub-vpc'
- IPv4 CIDR block: `10.0.0.0/24`
- Tenancy: `Default`
  
<img width="1018" height="152" alt="image" src="https://github.com/user-attachments/assets/45074d1d-6801-4bda-b627-ab2fbf4e4324" />

## Create Subnet
- VPC: `devops-pub-vpc`
- Subnet name: `devops-pub-subnet`
- Availability Zone: any `us-east-1a`
- IPv4 CIDR: `10.0.1.0/28`
- Enable Auto-Assign Public IP on Subnet: ensures all EC2 instances launched in this subnet get a public IP automatically.
  
<img width="1038" height="238" alt="image" src="https://github.com/user-attachments/assets/dfcad477-89c2-4efc-ae2a-be6879129502" />

## Create Internet Gateway
- Create Internet Gateway
- Name: devops-pub-igw
- Attach Internet gateway

<img width="1074" height="227" alt="image" src="https://github.com/user-attachments/assets/85d1a52c-8eb5-4940-a8fa-7f6f8a8db4e6" />

## Configure Route Table for Internet Access
- Select the route table associated with devops-pub-vpc
- Click Edit routes
- Add route:
Destination: 0.0.0.0/0
Target: Internet Gateway (devops-pub-igw)

<img width="916" height="254" alt="image" src="https://github.com/user-attachments/assets/08f0efbf-37d1-4a0f-86e0-7f6b8a2c1e69" />

- Associate Route Table with Subnet
- Go to Subnet associations
- Click Edit subnet associations
- Select devops-pub-subnet
- 
<img width="738" height="267" alt="image" src="https://github.com/user-attachments/assets/12b94470-9457-4e93-816f-e06e181f3eae" />

## Create EC2
- Name: devops-pub-ec2
- AMI: Amazon Linux or Ubuntu
- Instance type: t2.micro
- VPC: devops-pub-vpc
- Subnet: devops-pub-subnet
- Auto-assign public IP: Enabled
- Create a new security group:
- Name: ec2-sg
- Inbound rules:
Type Port Source
SSH 22 0.0.0.0/0
Outbound: Allow all

<img width="1102" height="75" alt="image" src="https://github.com/user-attachments/assets/13bb7c4c-397b-4c4c-a0da-547ca8aa3d53" />



