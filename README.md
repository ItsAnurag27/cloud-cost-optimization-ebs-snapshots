# AWS Lambda Snapshot Cleanup Automation

This project automates the deletion of unused or old EC2 EBS snapshots using AWS Lambda and CloudWatch Events.  
It helps in **cost optimization** by cleaning up unnecessary resources.

---

## AWS Cloud Cost Optimization - Identifying Stale Resources

**Identifying Stale EBS Snapshots:**  
In this example, we create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

**Description:**  
- The Lambda function fetches all EBS snapshots owned by the same account (`self`).
- It also retrieves a list of active EC2 instances (both **running** and **stopped** states).
- For each snapshot, it checks if the associated volume (if it exists) is not attached to any active instance.
- If it finds a **stale snapshot**, it automatically deletes it.
  
This helps in **optimizing storage costs** and keeps the cloud environment clean and efficient.

---

## How It Works
- **CloudWatch** triggers the Lambda function based on a schedule.
- **Lambda** checks for snapshots based on conditions:
  - Snapshots older than a specified number of days
  - Snapshots missing specific tags
  - Snapshots not attached to any active instance
- Eligible snapshots are deleted automatically.

---

## Prerequisites
- AWS account
- IAM Role for Lambda with necessary permissions
- Lambda function deployed
- CloudWatch scheduled rule

---

## Files
- `lambda_function.py`: Main Lambda function code.
- `cloudwatch_event.json`: Sample event structure to test locally.
- `iam_policy.json`: IAM permissions required for the Lambda execution.
- `architecture.png`: Diagram showing architecture flow.

---

## Deployment
1. Create an IAM role with the permissions defined in `iam_policy.json`.
2. Create a Lambda function and upload the `lambda_function.py` file.
3. Set up a CloudWatch Event rule to trigger the Lambda function at a scheduled interval.

---

## Architecture
![Architecture Diagram](architecture.png)

---

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*Contributions are welcome! Feel free to open issues or submit PRs.*

