# Demo - Create Organization
In this demo series, I will create an AWS Organizations in my general account. 
The following services that I will use is:
- AWS Organization

# Step 1 - Create an organization

- Create a `management account`(general account) in AWS Organization
- Invite an existing AWS account (Prod account) for member account
- Accept Invitation in AWS console
- ![1 - PNG]()

# Step 2 - Switch role

- On the `Prod account`, create a role for the management account to assume the role in switching the role from management account (general) to member account (prod)
- ![2 - PNG]()
- Switch role from general acc to prod acc `HERE`
- ![3-PNG]()

# Step 3 - Create new account in AWS Organization

- Create new member account in the organization with one unique email and same IAM role (OrganizationAccountAccessRole)
- A new member account (dev account)is created and aws automatic create a role to allow management account role swtiching
- ![4 - PNG]()

# Conclusion

1 management account (General Account) and 1 member account (Prod Account) from existing AWS account and created 1 new member account. (Dev Account) 

Management account can assume the role created by the member account to switch role.

