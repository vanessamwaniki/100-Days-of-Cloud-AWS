## Step 1: Create VPC Peering Connection
-name: `xfusion-vpc-peering`
- requester default vpc
- same region
- accepter `xfusion-private-vpc`
- create and accept
  
<img width="610" height="250" alt="image" src="https://github.com/user-attachments/assets/89162b81-d54f-4ffa-ab31-8173b72390e0" />

## Step 2: Configure Route Table
- edit route table for default vpc
- add route:
- destination: 10.1.0.0/16
- target: `xfusion-vpc-peering`
- edit route table for `xfusion-private-vpc`
- add route:
- destination: 172.31.0.0/16
- target: `xfusion-vpc-peering`

<img width="506" height="211" alt="image" src="https://github.com/user-attachments/assets/c7f4309f-5e91-413d-b0db-51505305a83d" />

## Step 3: Update Security group
- allow inbound ssh on the public EC2 group
- Add inbound rule on private ec2 security group:
ICMP – Echo Request
Source: 172.31.0.0/16 (Default VPC CIDR)

## Step 4: Add SSH key to the public EC2
- `cat /root/.ssh/id_rsa.pub`
- copy public key
- `mkdir -p ~/.ssh`
-  `vi ~/.ssh/authorized_keys`


