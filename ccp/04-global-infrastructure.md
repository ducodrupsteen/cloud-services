# Global infrastructure
AWS has data centers all over the world. Those data centers are divided into `regions`. In this module we'll go into debt about those regions and we'll learn the following:
- Summarize the benefits of [AWS Global Infrastructure](#aws-global-infrastructure)
- Describe the basic concept of [Availability Zones](#availability-zones)
- Describe the benefits of [Amazon CloudFront and edge locations](#edge-locations)
- Compare different methods for [provisioning AWS services](#provision-aws-resources)

## AWS Global Infrastructure
AWS has data centers all over the world. These data centers are divided in regions, each region has multiple data centers and these regions are picked based on where traffic is in high demand. These regions contain data centers for all sorts of services, like compute, storage and many more. All regions are connected to each other by a high speed fiber network controlled by AWS. But no data is shared between regions unless you explicitly, with the right permissions and credentials, request data to be moved.

### Compliance
You might have some compliance requirements, for example, you might have financial data that cannot leave the country you operate in. That is how AWS operates, data stored in any region won't leave that region unless you want it to. Region sovereignty is part of the critical design of AWS regions. Data is subject to local law of the country where the region is.

### Proximity
With choosing you AWS region, proximity plays a role. Of course you want to be as close as possible to your users. The delivery speed of data is what you want to take in to account. So you can definitely choose a US region if your users are located in Asia, but it does not make much sense, it adds a lot of latency to your requests.

### Feature availability
Sometimes features you might want to use are not available in the closest region. AWS innovates and releases new features constantly. But sometimes these new features might require specific hardware, this hardware is installed one region at the time, so it takes some time to have features available globally.

### Pricing
Even though the hardware might be the same when comparing one region to the other, pricing might be different. Each region has it's own price sheet. The are many factors that can affect the price, like tax for example.

**These are the four key factors when you choose your AWS region.**

### Availability zones
To be as disaster proof as possibly, you might not want to run your software in just one building. AWS has these Availability Zones, or `AZ`, with either a single data center or a group of data centers. An `AZ` has redundant power, networking and connectivity. When you launch a `EC2` instance, it is a virtual machine on physical hardware in a data center that is located in an `AZ`. This means AWS regions consists of multiple isolated an physically separate `AZ`s.

When you run one `EC2` instance, it runs in just one `AZ`. So if you want to be disaster proof it is obvious to run more instances in different `AZ`s. Even though it might be more spread out, the latency between `AZ`s is still in the single digits.

Many of the AWS services run at a region level, this means that they run synchronously across multiple `AZ`s. If you look a `ELB`, this is a regional service that runs across `AZ`s and talks to `EC2` instances in a specific `AZ`.

## Edge locations
You or your users might need to access data from all over the world but you've only hosted your data in one region. Instead of having users from everywhere connect to your single region. You can place a copy locally or cache a copy in different regions.

Caching copies of data closer to the customers all around the world uses the concept of content delivery networks, or `CDN`s. This is commonly used, and at AWS it is called `CloudFront`. Amazon `CloudFront` is a service that helps you deliver data, video, applications and APIs to your users. It uses something called `Edge Locations`.

These `Edge Locations` are separate from regions. You can push content from a region to a collection of `Edge Locations`. This helps you with faster delivery times of data. `Edge Locations` also run more then `CloudFront`. They run a Domain Name Service called `Route53`, this helps with directing users to the correct location on the web.

### AWS Outpost
It is also possible to run AWS services inside your own data center, this service is called `AWS Outpost`. With `Outpost` AWS will basically install a mini region inside your own data center, this is owned and operated by AWS and uses 100% of AWS functionality, but it is isolated in your own building.

## Provision AWS Resources
There are different ways to interact with the services that are discussed until now. But it is good to know that everything in AWS is an API call. This means that there are certain ways to interact with AWS services. You can call these APIs to setup, configure and manage your AWS resources.

### AWS Management Console
The AWS Management Console is a browser based interface. This is a great way to get started, it allows you to visually interact with AWS services. It is also great for viewing AWS bills, monitoring and working with non technical resources.

The downside here is that it is a lot of clicking, and it is easy to miss certain settings. It gets also really repetitive if you want to spin up multiple instances of a service, you will have to click through the same collection of screens multiple times.

### AWS CLI
The AWS CLI allows you to make API calls through your terminal. Writing commands using the CLI makes making API calls to AWS very repeatable. You can easily prewrite some commands, this would make it less error prone and you could even schedule these type of commands.

### AWS SDKs
AWS also provides SDKs for a wide range of programming languages. This would allow you to develop your own program to interact with AWS without the need for any low level API calls. This also prevents the need for manual resource creation like with the browser console.

Besides these DIY solutions, AWS also provides some managed tools to provision AWS resources.
### AWS Elastic Beanstalk
With AWS Beanstalk you can easily setup `EC2` based environments. Instead of clicking or writing commands, you can provide Elastic Beanstalk your application code and desired configuration and it handles the rest. It sets up you network, `EC2` instances, scaling and load balancers. You can also save environments to easily redeploy it. It provides a way were you don't have to configure it all by yourself, but you still have access to the underlying resources.

### AWS CloudFormation
`AWS CloudFormation` is an infrastructure as code tool that allows you to define a wide variety of AWS services, not just `EC2` based. You setup documents, called `CloudFormation templates`, these documents are written in a `JSON` or `Yaml` format. So you can define what you want to build, and the `CloudFormation Engine` will figure out how to build it, so you don't have to worry about the API calls. `CloudFormation` will provision you templates in parallel. The templates are repeatable in any account or region, the outcome will always be the same.

