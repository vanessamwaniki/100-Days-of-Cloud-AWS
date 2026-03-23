### Step 1: Create a new private s3 bucket
```
aws s3 mb s3://devops-sync-30653 --region us-east-1
```

### Step 2: Copy all the data from existing bucket to new bucket
Existing: s3://devops-s3-24257    New: s3://devops-sync-30653
```
aws s3 sync s3://devops-s3-24257 s3://devops-sync-30653
```

### Step 3: Verify Data Consistency:Ensure that both buckets have the same data.

Running ls should show same files on both
```
aws s3 ls s3://devops-s3-24257
aws s3 ls devops-sync-30653
```

Running a dryrun comparison should show no differences
``` 
aws s3 sync s3://devops-s3-24257 s3://devops-sync-30653 --dryrun
```





