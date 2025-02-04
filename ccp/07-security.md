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
At the customer compliance center you can read various stories to discover how others have solved various compliance, governance and audit challenges.

Next to that you can read various white papers on;
- AWS awnsers to key compliance questions
- An overview of AWS risk and compliance
- An auditing security checklist

Besides that it also includes a learning path to auditing, for anyone that is interested in compliance, auditing and any other legal matters.

## Denial of service attacks
A denial-of-service, `DoS`, attack is a deliberate attempt to make a website or application unavailable to users. Someone might overflow your application with requests, which slows everything down and prevents actual user from making any requests.

These request also might come from multiple sources, which would make it a Distributed denial of service `DDoS` attack. This could either be a group of people, or a single attacker making use of bots.

### AWS Shield
`AWS Shield` can help you minimize the effect a `DoS` or `DDoS` attack has on your application.
You can use this services in two ways:

#### AWS Shield Standard
`AWS Shield Standard` automatically protects all AWS customers at no cost. It protect AWS resources from the most common and frequently occurring types of `DDoS` attacks. As traffic comes in, it analysis the traffic and it is able to detect malicious traffic.

#### AWS Shield Advanced
`AWS Shield Advanced` is a paid service, it provides detailed attack diagnostics and the ability to detect and migrate sophisticated `DDoS` attacks.
It also integrates with other services such as `CloudFront`, `Route 53`, `ELB` and additionally you can integrate `Shield` with `AWS WAF` by writing custom rules to migrate complex `DDoS` attacks.

## Additional Security Services

### AWS Key Management Service `AWS KMS`
This service enables you to perform encryption operations through the use of cryptographic keys. You can use `AWS KMS` to create, manage and use cryptographic keys to encrypt and decrypt data. You can also control the use of keys across a wide range of services. For example, you can specify which IAM users and roles are able to manage keys.

### AWS WAF
`AWS WAF` is a web application firewall that lets you monitor network requests that come into your web application. `WAF` works together with `CloudFront` and an `ALB`. `WAF` works by using a web access control list, `ACL`, to protect your AWS resources. For example, you have been receiving malicious requests from several IP addresses. You can configure your `web acl` to allow requests from everywhere except those IP addresses.

### Amazon Inspector
Amazon inspector helps to improve the security and compliance of applications by running automated security assessments. It performs security checks for vulnerabilities and deviations from security best practices.

### Amazon GuardDuty
Amazon GuardDuty is a service that identifies threats by continuously monitoring the network activities and account behavior within your AWS environment.