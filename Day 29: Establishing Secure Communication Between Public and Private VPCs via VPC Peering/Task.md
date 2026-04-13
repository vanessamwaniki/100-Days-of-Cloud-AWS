1) There is already an existing EC2 instance in the public vpc/subnet:

Name: xfusion-public-ec2

2) There is already an existing Private VPC:

Name: xfusion-private-vpc
CIDR: 10.1.0.0/16

3) There is already an existing Subnet in xfusion-private-vpc:

Name: xfusion-private-subnet
CIDR: 10.1.1.0/24

4) There is already an existing EC2 instance in the private subnet:

Name: xfusion-private-ec2

5) Create a Peering Connection between the Default VPC and the Private VPC:

VPC Peering Connection Name: xfusion-vpc-peering

6) Configure Route Tables to enable communication between the two VPCs.

Ensure the private EC2 instance is accessible from the public EC2 instance.

7) Test the Connection:

Add /root/.ssh/id_rsa.pub public key to the public EC2 instance's ec2-user's authorized_keys 
to make sure we are able to ssh into this instance from AWS client host. You may also need to update 
the security group of the private EC2 instance to allow ICMP traffic from the public/default VPC CIDR. 
This will enable you to ping the private instance from the public instance.
SSH into the public EC2 instance and ensure that you can ping the private EC2 instance.
