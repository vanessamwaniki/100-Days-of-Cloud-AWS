## Step 1: Verify Docker
- Verify Docker
```
docker --version
```

## Step 2: Create ECR Repository
```
aws ecr create-repository \
  --repository-name datacenter-ecr \
  --region us-east-1
```

<img width="677" height="337" alt="image" src="https://github.com/user-attachments/assets/492fee11-8ade-41dd-bd31-0bce10ff5f76" />

- Copy the repository URI : 557258460930.dkr.ecr.us-east-1.amazonaws.com/datacenter-ecr
  

## Step 3: Authenticate Docker to ECR and Build Docker Image

```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 557258460930.dkr.ecr.us-east-1.amazonaws.com/datacenter-ecr
```
<img width="715" height="177" alt="image" src="https://github.com/user-attachments/assets/c0303afe-a492-4b4f-ba8a-eb6aece62d25" />

- Build Docker Image
```
cd /root/pyapp
# Build the image:
docker build -t datacenter-ecr:latest .
# Verify the image exists:
docker images
```

<img width="539" height="115" alt="image" src="https://github.com/user-attachments/assets/cb26b77b-a6db-413f-b067-7fb0fec971c9" />


## Step 4: Tag the Image for ECR
```
docker tag datacenter-ecr:latest 557258460930.dkr.ecr.us-east-1.amazonaws.com/datacenter-ecr
```

## Step 5: Push the Image to ECR and Verify
```
# Push image
docker push 557258460930.dkr.ecr.us-east-1.amazonaws.com/datacenter-ecr:latest

# Verify
aws ecr list-images --repository-name datacenter-ecr --region us-east-1
```

<img width="719" height="262" alt="image" src="https://github.com/user-attachments/assets/c172f1e0-eb26-4a7d-ada3-d483b9cf5cbc" />
<img width="717" height="182" alt="image" src="https://github.com/user-attachments/assets/0e38e611-2b36-4f6c-913f-c1f4541b0e88" />












