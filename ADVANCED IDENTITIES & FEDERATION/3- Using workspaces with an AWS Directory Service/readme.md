# Demo - Using Workspaces with AWS Directory Service

This is the architecture that I am going to implement:
![1 -PNG]()

What we will do is:

- Start with Animal4Life VPC configuration
- Complete NAT gateways to provide internet connectivity
- Add a directory service for user management in workspace
- Deploy and integrate an Amazon workspace

# Step 1 : Configure VPC

Make sure my account is in IAM admin in management account 
[CLICK HERE](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0029-aws-mixed-workspaces-simple-demo/vpc_with_natgw.yaml&stackName=A4LVPC) to go in the cloud formation stack and create it.
- Wait the stack in complete status, then we will proceed. 
![2 -PNG]()

# Step 2 : Create a simple AD

- Go to workspace tab, and click get started.
- Choose Advanced setup
- You will need to select directory type.
- In this demo, I will select `simple AD` . It is a Linux-Samba Active Directory-compatible server. If you want a native Microsoft Active Direcotry then you might want to choose AD connector or AWS Managed Microsoft AD.
- Click on next to proceed
![3 -PNG]()

- At the VPC section, make sure to pick `a4l-vpc`.
- In the subnet section, pick `appaA` and `appB`
![4 -PNG]()

- Configure all the setting and create the simple AD.

# Configure and implement workspace with simple AD

- After complete, go to create workspace.
- Register the directory created just now. Register the directory able you to specific which subnet you want to put ENI in it.
- Choose the `appA` `appB``appC` that we specific just now and proceed it.
- Create User and identify user.
- Select window 10 free tier eligible bundle
- In the running mode, we can specify autostop and number of hours
- Leave root and user volumn size as default
- Create workspace.

# Go in to workspace console
- After the creation complete, you will get an URL attach in an email.
- Open it and fill all the credential.
- Follow the instruction and download Amazon workspace client
- Sign in the username and password .
![5 -PNG]()
- It might take a little bit longer when you first sign in the workspace
![6- PNG]()
- Congrat we have made our own workspace successfully and it also have connectivity without setting up any infrastruture.
![7- PNG]()
- Note that We can also use in different OS device or even in web-based client.

# DONE!!
Clear up the resource and then we are done!.
