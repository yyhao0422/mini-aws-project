# Demo - Service Control Policy (SCP)
In this simple demo, I will create `SCP` in my AWS Organization. 

# Simple Demo SCP
I have created two member account called `DEV` and `PROD` in my Organization which in `Management` Account and I have already configured switch role.
I will create SCP within this organization in my `management account`

# Create Heirarchical OU
- Create a hierarchical organization unit below the root container
- I created two OU which is `PROD` and `DEV`
![1 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/2-Create%20SCP/images/1.png)
- Move member account in to the organization unit
![2 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/2-Create%20SCP/images/2.png)
- Switch role to PROD account and successfully uploaded a cat pictures by creating new s3 bucket
![3 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/2-Create%20SCP/images/3.png)
- Now we want to show how SCP can used to control access
- Enable SCP in management account
![4 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/2-Create%20SCP/images/4.png)
- Create a deny s3 scp policy
![5 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/2-Create%20SCP/images/5.png)
- Apply to PROD Organization Unit (OU) and detach the allow all access
![6 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/2-Create%20SCP/images/6.png)
- Switch to PROD account and test it
![7 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/2-Create%20SCP/images/6.png)
- Clean up and DONE!

