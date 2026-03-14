The Nautilus DevOps team needs to set up a new EC2 instance that can be accessed securely from their landing host (aws-client). 
The instance should be of type t2.micro and named devops-ec2. 
A new SSH key should be created on the aws-client host under the/root/.ssh/ folder, if it doesn't already exist. 
This key should then be added to the root user's authorised keys on the EC2 instance, allowing passwordless SSH access from the aws-client host.

## Task Analysis
###SSH key
- Required for passwordless SSH access
- To be created in AWS Client

###EC2 Instance
- Created in AWS Console
- Type t2.micro
- Security group with inbound SSH port 22
- Add the public key to EC2 root user's authorised keys

###Test
- Test passwordless login to EC2 instance from AWS Client
