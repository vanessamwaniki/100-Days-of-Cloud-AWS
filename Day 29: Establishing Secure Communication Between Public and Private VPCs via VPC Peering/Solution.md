## Step 1: Create VPC Peering Connection
- name: `xfusion-vpc-peering`
- requester default vpc
- same region
- accepter `xfusion-private-vpc`
- create and accept
  
<img width="610" height="250" alt="image" src="https://github.com/user-attachments/assets/89162b81-d54f-4ffa-ab31-8173b72390e0" />

## Step 2: Configure Route Table
### Default VPC route table
- edit route table for default vpc
- add route:
- destination: 10.1.0.0/16 (private VPC CIDR)
- target: `xfusion-vpc-peering`

### Private VPC route table
- edit route table for `xfusion-private-vpc`
- add route:
- destination: 172.31.0.0/16 (Default VPC CIDR)
- target: `xfusion-vpc-peering`

<img width="506" height="211" alt="image" src="https://github.com/user-attachments/assets/c7f4309f-5e91-413d-b0db-51505305a83d" />

## Step 3: Update Security group
- allow inbound ssh on the public EC2 group
- Add inbound rule on private ec2 security group:
- ICMP – Echo Request
- Source: 172.31.0.0/16 (Default VPC CIDR)

## Step 4: Add SSH key to the public EC2
### In CLI
- `cat /root/.ssh/id_rsa.pub` to display and copy public key

### Connect to the public EC2 via console/EC2 Instance Connect or existing access
- `mkdir -p ~/.ssh`
-  `vi ~/.ssh/authorized_keys`
-  Paste the public key and save
-  Then fix permissions
-  `chmod 700 ~/.ssh`
-  `chmod 600 ~/.ssh/authorized_keys`

## Step 5: SSH to public ec2 in AWS CLI
- `ssh -i /root/.ssh/id_rsa ec2-user@<PUBLIC_EC2_PUBLIC_IP>`
- Login should succeed
- Ping the Private EC2
<img width="416" height="115" alt="image" src="https://github.com/user-attachments/assets/1f5ef5a1-d96b-42b1-ac2d-92156111b2c9" />



