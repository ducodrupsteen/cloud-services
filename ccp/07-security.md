# Security
We're going to look into what security measures there are. What can we do our self and what measures does AWS have. We'll look into the following:
- AWS [Shared Responsibility Model](#shared-responsibility-model)
- [User Permission and Access](#user-permission-and-access)
- [AWS Organizations](#aws-organizations)
- Compliance
- Denial-of-Service Attacks
- Additional Security Services

## Shared Responsibility Model
We've seen a lot of services come by, the big question is "Who is responsible for securing it?". Well, both AWS and customers are responsible for keeping things secure. AWS is not a single component, rather it is a collection of components within a big environment. Bot us (the customer) and AWS are responsible for keeping parts of these components secure. This concept is called a `Shared Responsibility model`. We'll look at what parts there are and who is responsible for keeping that part secure.

### Physical
If we look at where the cloud lives then we can see that it lives in a physical data center, a building. These data centers are secured by AWS.

### Infrastructure & Hypervisors
If we look at the hardware the AWS Cloud runs on, it uses hypervisors to make it possible to virtualize machines for customers to use, next to that it is all connected to. This is also secured by AWS.

Everything above that layer is for us, the customer. Unless it is a managed service of course.

### Operating system
If you take `EC2` for an example. You have a operating system running, you have to keep that secure. This is also because AWS does not have access to this layer, you're the only one with access. 

### Application
On top of that `OS` you have an application running, this is obviously also your responsibility.

### Data
And as last, your application uses data, this is also for you to secure it.

So you can basically slim it down to, whatever we (the customer) puts in the AWS Cloud, we need to secure. And AWS is responsible for securing the AWS Cloud.

## User Permission and Access
When you first create a AWS account, you'll create something called an AWS Root Account. This account has the right to do anything they want inside your AWS environment, so to make this account more secure it is recommended to enable Multi Factor Authentication, `MFA`. And even with `MFA` it is recommended to not use the Root Account, you basically want to create an account that can control other account, to do this you van use the service AWS Identity and Access Management.

### IAM
With `IAM`, you can create `IAM` users. By default an `IAM` user you create has no permission to do anything. You have to give the user permission to do anything, even logging in.
The way you do this is by associating so called `IAM Policies`. These policies are JSON documents that describe what API calls a user can or can't make.

```
{
  "Version": "2012-10-17",
  "Statement": {
	  "Effect": "Allow",
	  "Action": "s3:ListObject",
	  "Resource": "arn:aws:s3:::AWSDOC-EXAMPLE-BUCKET"
  }
}
```
*This is an exmple IAM Policy to allow a user to access object in the S3 bucket with ID `AWSDOC-EXAMPLE-BUCKET`*. 

But making many account and granting permission through countless of policies can be a bit overwhelming. So to make it more convenient we can place users in certain `IAM Groups`.
Instead of assigning a policy to a single or multiple user(s) we simply create a group with a policy and add users who need access to the service to that group.

There is also something called `IAM Roles`, this is generally used to grant temporary permission. To switch to a role a user needs permission to do so, and once they have switched they will lose all permission they previously had.

## AWS Organizations
With `AWS Organizations` you can control permissions for accounts within an organization by using [service control policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html). These policies allow you to place restrictions on AWS services, resources and API actions that users and roles in each account can access.

### Organizational units
In Organizations, you can group accounts into organizational units, `OU`'s to make managing those accounts easier. You can apply policies to those `OU` which allows you to group accounts with similar business or security requirements.

So for example, you can create Organizations for finance, IT, HR and legal. HR and legal might have similar requirements, so it makes sense to place those two in an `OU`.

## Compliance
Depending on the industry or region you operate in you might need to uphold specific standards. An audit or inspection will ensure that you meet those standards.

### AWS Artifact
`AWS Artifact` is a service that gives you access to security and compliance reports, and allows you to select online agreements. It consists of two parts, Agreements and Reports.

#### Agreements
`Artifact Agreements` let's you review and accept certain agreements based on the regulations that apply to the customer. You accept these agreements for either an individual account or your whole organization.

#### Reports
`Artifact Reports` provides compliance reports from third party auditors. These auditors have tested and verified AWS is compliant with all sorts of standards and regulations.

### Customer compliance center
At the customer compliance center you can read various stories to discover how others have solved various compliance, governance and audit challanges.

Next to that you can read various white papers on;
- AWS awnsers to key compliance questions
- An overview of AWS risk and compliance
- An auditing security checklist

Besides that it also includes a learning path to auditing, for anyone that is interested in compliance, auditing and any other legal matters.