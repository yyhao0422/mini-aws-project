# Demo - Shared Services VPC
Demo to implement shared services VPC using AWS RAM
![1 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/5-Create%20Shared%20Services%20VPC/images/1.png)
- Download this user data for later [User Data](https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0040-aws-mixed-sharedORGVPC/userdata.txt)
- GO to the Management account and deploy this cloud formation [Click Here](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0040-aws-mixed-sharedORGVPC/A4LVPC.yaml&stackName=A4LVPC)
- This will create a VPC in management account and few subnets

- Go to AWS Resource Access Manager and go to the setting to check the enable sharing with organization

![2 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/5-Create%20Shared%20Services%20VPC/images/2.png)
- Create resource share in management account

- Key in the name and the subnet that need to be shared

- Specify permission and the principal to access
![3 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/5-Create%20Shared%20Services%20VPC/images/3.png)
- Go to the PROD account and launch EC2 (remember the subnet ID )
![4 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/5-Create%20Shared%20Services%20VPC/images/4.png)
- Note: AWS randomise what the available means in the infrastructure.

- Configure the EC2 Security Group HTTP set to anywhere

- Paste all the user data to the EC2 
![5 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/5-Create%20Shared%20Services%20VPC/images/5.png)
- Copy the Public address and open it in http

- You can now see the image
![6 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/5-Create%20Shared%20Services%20VPC/images/6.png)
- Note : We are not able to modify the shared resources. such as subnet route table and internet gateway.

- GO to DEV account and management account, we cannot see the resource created in the PROD account.

- Note: We only can see our own created resource