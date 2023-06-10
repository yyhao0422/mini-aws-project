# Demo - Add Single Sign-on to the Animal4life ORG
Below are the architecture diagram that I will implement in this DEMO!
![1 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/1.png)
Note: AWS SSO do not associated any cost.

- Go to general account ( US-East-1)
- In SSO console, go and enable the product. (If you get an error, just retries to enable it)
- Identity source remain default as it is (AWS SSO)
- GO and customize your SSO User Portal URL
![2 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/2.png)
- Go to permissions set section and create predefined permission set. Create 4 permission sets as below. Sessions duration set to 4 hour. 
![3 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/3.png)
- Next, we gonna create user. Go to the user tab. Add user (Sally), specify the user detail. 
- Create a group called biling and add Sally into the group which in my demo is biling group.
- Copy the credential of Sally.
- Go to the AWS account tab in SSO console, click all the account within the organization and click on assign user and group. 
![4 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/4.png)
- Specify the group that you want to give SSO access to, in this case, billing group. 
![5 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/5.png)
- Assign permissions set to the account. Then submit it. 
![6 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/6.png)
- Open incognito window, go the the SSO User Portal URL. Key in all the credential
- Go to the management console and check wheather the permissions assign is working or not
![7 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/7.png)

- Billing section can be access and ec2 section cannot be accessed. It worked as it is. 
![8 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/8.png)
![9 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/9.png)
- Go back to SSO console, create new group (Power User) and add user.
- Go to AWS account in the sso console and then select all account within the organization
- Select the power user permission set and submit
- Go back to Sally SSO user portal and refresh it.
- You now have access to the Power User permissions. (EC2)
![10 - PNG](https://github.com/yyhao0422/aws-project/blob/master/ADVANCED%20IDENTITIES%20%26%20FEDERATION/1-%20Adding%20Single%20Sign-on%20to%20the%20Animals4life%20ORG/images/10.png)
- You can also go to application tab for external applications but now we not gonna configure this .
- Now, we delete all the configuration we done so far. Delete user, delete group.
- Create new user and group that have iamadmin user permission.
- Go to aws account, select all account and give the administrator access permission set and then submit it.
- Go to the SSO User Portal, sign in with the iamadmin account created.
- As it is a administrative access , it will be incur a risk on it. 
- To avoid that, we can go to SSO User Portal and then go to setting tab.
- Enable MFA setting and then go to the SSO User Portal to set up MFA device.
- That’s all for this demo. Thanks.

