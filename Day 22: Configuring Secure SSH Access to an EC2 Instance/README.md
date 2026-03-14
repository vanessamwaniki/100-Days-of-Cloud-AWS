STEP 1: Create the SSH key in AWS Client

$ ssh-keygen -t rsa -b 2048 -f /root/.ssh/id_rsa

STEP 2: Launch the EC2 instance In AWS console
- Ensure type is t2.micro
- Ensure security group allows connection on port 22

STEP 3: Add public key to EC2 instance
- Connect to EC2 using Instance Connect
- Copy the public key created earlier

$ cat /root/.ssh/id_rsa.pub

- Add the authorised keys in the EC2 in a new line

$ sudo mkdir -p /root/.ssh
$ sudo vi /root/.ssh/authorized_keys

- Fix permissions

$ sudo chmod 700 /root/.ssh
$ sudo chmod 600 /root/.ssh/authorized_keys
$ sudo chown -R root:root /root/.ssh

STEP 4: Test passwordless SSH i AWS Client

$ ssh -i /root/.ssh/id_rsa root@ec2-18-215-173-156.compute-1.amazonaws.com

SUCCESS: Should be able to login without requiring password.


