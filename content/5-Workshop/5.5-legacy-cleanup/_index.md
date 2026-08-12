---
title : "Clean up"
date : 2024-01-01
weight : 99
chapter : false
pre : " <b> 5.5. </b> "
draft : false
---

## 5.5 Clean up

When the CloudMenu system is no longer needed on AWS, the resources created during deployment should be reviewed and cleaned up to avoid unnecessary costs.

CloudMenu uses Amazon S3, Amazon CloudFront, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, and AWS IAM. Therefore, the cleanup process should be performed for each service, with careful verification before deleting any resources.

### Resources to Review

- Amazon S3: Delete frontend files and static resources that are no longer needed. If the bucket is also going to be deleted, make sure to review and remove its objects first.
- Amazon CloudFront: Disable and delete the CloudFront distribution if the system is no longer being used.
- Amazon API Gateway: Delete APIs and stages that are no longer required.
- AWS Lambda: Delete the Lambda functions used by CloudMenu when they are no longer needed.
- Amazon DynamoDB: Delete the CloudMenuOrders table if the order data is no longer required. Back up the data first if it still needs to be preserved.
- AWS IAM: Review and delete IAM Roles or Policies that were created specifically for CloudMenu and are no longer being used.

### Before Cleanup

- Verify the correct AWS Account and AWS Region to avoid accidentally deleting resources belonging to another system.
- Review the CloudMenu resources currently running in the AWS Management Console.
- Determine whether the data stored in Amazon DynamoDB needs to be retained before deleting the CloudMenuOrders table.
- Check Amazon S3 and make sure any necessary frontend files have been backed up if required.
- Review the IAM Roles/Policies to ensure they are not being used by Lambda functions or other AWS resources.

### After Cleanup

After completing the cleanup process, review the AWS Management Console again to ensure that unnecessary CloudMenu resources have been successfully removed.

In particular, verify that:

- No unused CloudFront Distributions remain.
- No unnecessary API Gateway APIs remain.
- No unused CloudMenu Lambda Functions remain.
- The CloudMenuOrders DynamoDB Table has been removed if the data is no longer required.
- No unused S3 Buckets/Objects remain.
- No unused IAM Roles/Policies created specifically for CloudMenu remain.

Note: Deleting the DynamoDB table or order data may result in permanent data loss. Make sure to confirm that the data is no longer needed and create a backup before deletion if the data must be retained.