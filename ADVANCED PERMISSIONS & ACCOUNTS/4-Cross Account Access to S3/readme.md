# Demo - Cross Account Access to S3
![1 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/1.png)
- In this Demo, we act as BOB identity (management account) to interact with S3 bucket within the A4L-PROD account.
- Three bucket with each interact with different way.

# Set Up The Environment
Switch role to PROD acc and deploy the bucket via CloudFormation [Click Here](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0039-aws-mixed-cross-account-s3/prod_bucketsandrole.yaml&stackName=buckets)
Download these file
- [Bucket Image](https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0039-aws-mixed-cross-account-s3/bucket_images.zip)
- [Bucket Policy](https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0039-aws-mixed-cross-account-s3/bucket_images.zip)
Note down all output created in cloud formation
![2 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/2.png)

# First Method :  Access Control List (ACL) --legacy
Copy the Account canonical user ID in the general account
![3 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/3.png)
Switch to Prod account, open bucket 1 bucket permission and add a grantee using Account canonical user ID in the general account.
![4 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/4.png)
We can now access and upload file to the bucket 
![5 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/5.png)
After upload a file in General account, switch to PROD account. We cannot access the object in PROD account. The object owner is General Account even thought the bucket owner is PROD Account
![6 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/6.png)

# Second Method :  Bucket Policy
- Go to PROD account and open the bucket permission
- Go to the Bucket policy and then edit the policy to [HERE](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/policy.json)
- Replace the arn management account id and the bucket name
- Go back to the management account and you should now have access to the object and able to upload file.
- Same as ACL, We cannot access the object in PROD account. The object owner is General Account even thought the bucket owner is PROD Account.
- However, we can set it as bucket owner preferred 
![7 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/7.png)
# Third Method: Cross-account role
- Go to prod acc and copy down the prod account id
- Go back to the management account and select switch role 
- Key in the Prod account ID and the role that set up at the cloud formation output
![8 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/8.png)
- This time it is bucket -CrossAccountS3Role
![9 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/9.png)
On the XACCDEMO, you now can upload the file in bucket 3
![10 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/4-Cross%20Account%20Access%20to%20S3/images/10.png)
- This role is own by prod acc and the prod account owns this object and also own this bucket
- Therefore, Prod account and XACCDEMO both can upload and view the object. While management account cannot.
- This is a lot tidier and lower admin overhead.

