# serverless_submission
Solution to Graded Assignment On Serverless Architecture

## Prerequisites
- For this assignment, I have used the following IAM rles.
  ![image](https://github.com/user-attachments/assets/05531be4-16df-4e44-872a-f75e1b96106e)
  1. **Arpit-EC2FullAccess**:
     ![image](https://github.com/user-attachments/assets/b7fc3f88-c20a-4a05-aacc-9933ed5b1a05)
  2. **Arpit-S3FullAccess**:
     ![image](https://github.com/user-attachments/assets/6c81262c-5c10-4f88-aaed-997ac445fcd6)

## Assignment 1: Automated Instance Management Using AWS Lambda and Boto3
### Solution 1:
![image](https://github.com/user-attachments/assets/912fd96e-ced3-4637-8883-fa7165c59692)
This script manages EC2 instances based on specific tags (Vish-AutoStart and Vish-AutoStop). 
It performs the following operations:
- **Vish-AutoStop**: Finds running instances with this tag and stops them.
- **Vish-AutoStart**: Finds stopped instances with this tag and starts them.
- **Instance Identification**: It identifies the instances by both their InstanceId and their Name tag (or labels them as "Unnamed Instance" if no name is present).
- **Return Data**: The script returns the InstanceId and InstanceName of all the stopped and started instances.
This is useful in environments where certain EC2 instances need to be automatically stopped or started based on pre-defined tags, such as shutting down development servers after work hours or automatically starting them at the beginning of the day.


## Assignment 2: Automated S3 Bucket Cleanup Using AWS Lambda and Boto3
### Solution 2:
![image](https://github.com/user-attachments/assets/9ff4672f-9df8-4a3f-a878-e02b5fc18f43)
This script automates the deletion of old files from a specified S3 bucket:
- **Age Check**: It deletes any files in the S3 bucket that are older than 30 days.
- **List Objects**: It lists all objects in the S3 bucket and checks their `LastModified` date.
- **File Deletion**: Files older than the specified time threshold are deleted from the bucket.
- **Logging**: The script logs which files are deleted and returns a list of the deleted files. If no old files are found, it returns a message indicating that no deletions were necessary.
This script is particularly useful for maintaining storage hygiene in S3 by removing obsolete or outdated files that no longer need to be retained, freeing up space and reducing costs.

## Assignment 9: Archive Old Files from S3 to Glacier Using AWS Lambda and Boto3
### Solution 9:
![image](https://github.com/user-attachments/assets/395aec1e-844b-4c9d-ad93-ce781eb2432c)
This script automatically archives files in an S3 bucket to Amazon Glacier, a low-cost, long-term storage solution:
- **Age Check**: It identifies files in an S3 bucket that are older than 6 months.
- **Storage Class Change**: For each file older than 6 months, the script changes its storage class to Glacier using the StorageClass attribute in the copy_object API call.
- **Archiving Logs**: The script logs which files were moved to Glacier and returns a list of the archived files. If no files are older than the threshold, it returns a message indicating that no archival was needed.
This is helpful for organizations looking to reduce storage costs by moving infrequently accessed files to Glacier for long-term retention at a lower price point.

## Assignment 15: Implement a Log Cleaner for S3
### Solution 15:
![image](https://github.com/user-attachments/assets/77876786-ae30-40a0-a281-3c177228901b)
This script automates the cleanup of log files in an S3 bucket, removing logs older than 90 days:
- **Age Check**: It lists all log files in the S3 bucket and checks their age against a 90-day threshold.
- **Log Deletion**: It deletes any logs older than 90 days from the S3 bucket.
- **Logging**: The script logs and returns a list of deleted logs, and if no logs are older than 90 days, it returns a message that no logs were deleted.
This script is ideal for maintaining a clean logging environment by automatically removing old log files, which can otherwise accumulate over time and consume significant storage, impacting both performance and costs.

## Additional Information
- Neovim Config: I use Neovim as my text editor. You can find my configuration [here](https://github.com/vishwesh5544/neovish).
- Operating System: I'm using Linux Pop!_OS for all my development work.

