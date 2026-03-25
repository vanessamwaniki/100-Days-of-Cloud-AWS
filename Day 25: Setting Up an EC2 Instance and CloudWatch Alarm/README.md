###Step 1: Create the EC2 instance
- Ubuntu AMI
- t2.micro
<img width="1062" height="118" alt="image" src="https://github.com/user-attachments/assets/1d836142-0e73-409d-816c-81db67d53880" />

###Step 2: Create Cloud watch alarm
- Metric: CPU Utilization
- Threshold: >= 90% for 1 consecutive 5-minute period.
- Alarm Actions: Send a notification to nautilus-sns-topic
<img width="917" height="151" alt="image" src="https://github.com/user-attachments/assets/5d19c142-9e62-4522-a6bb-021f756a3f16" />
<img width="1038" height="426" alt="image" src="https://github.com/user-attachments/assets/4a5ba646-f730-456f-b4f6-960eefc40225" />


