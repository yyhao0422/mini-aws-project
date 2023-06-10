# Demo - Revoking Temporary Credential
In this demo, I am going to revoking temporary credential that is assign to users using sts:Assumerole. We need to first understand why need revoking temporary credential
# Understanding The Important If Revoking Temporary Credential
Temperary credential is given to user. If the temperory credential of any user is leaked to any bad actor then bad things will happen! 
You will ask why not we just delete the role or changing the role? The answer is Yes , we can do that but it is not the best solution. 
You might affect other users that assuming the role and no doubt that it is admin overhead. To solve this problem, we can implement revoke 
temporary credential by placing a inline policy that deny all sessions older than now. The user can then assume the role again with sts:assumerole and get a new temp credential. However, the bad actor cannot access it because of the explicit deny and he also cannot assume the role because he is not in the trust policy. Below is the architecture diagram:
![architecture-diagram - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/3-Revoking%20Temporary%20Credential/images/architecture-diagram.png)

# Lets Begin!
- Create the environment using Cloud Formation. ![Click here](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0038-aws-pro-revoking-temporary-credentials/A4LHostingInc.yaml&stackName=A4L)
![1 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/3-Revoking%20Temporary%20Credential/images/1.png)
- Connect to the Instance A (Act as an invader)
![2 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/3-Revoking%20Temporary%20Credential/images/2.png)
- Get the credential from the EC2 instance
![3 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/3-Revoking%20Temporary%20Credential/images/3.png)
- Using the credential, the invader can use to connect using local machine
![4 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/3-Revoking%20Temporary%20Credential/images/4.png)
- To revoke this we need to go to the IAM role and add the revoke at the revoke sessions
![5 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/3-Revoking%20Temporary%20Credential/images/5.png)
![6 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20PERMISSIONS%20%26%20ACCOUNTS/3-Revoking%20Temporary%20Credential/images/6.png)
- At this time, all the credential before this time is deny. The invader cannot use that credential to connect. The EC2 instance also cannot be connected by us
- We need to Stop and Start back the EC2 in order to assume the role again and then get a new credential.
- By using the new credential, we can able to connect the EC2. 
- DONE!



