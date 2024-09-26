# Compute in the cloud
This module mostly focused on `Amazon EC2` to summarize what we will learn:
- Describe the benefits of [`EC2` at a basic level](#ec2-at-a-basic-level)
- Identify the different `EC2` instance types
- Differentiate between the various billing options for `EC2`
- Summarize the benefits of `EC2` auto scaling
- Summarize the benefits of `Elastic Load Balancing`
- Give an example of the uses for `Elastic Load Balancing`
- Summarize the differences between `Amazon Simple Notification Service (Amazon SNS)` and `Amazon Simple Queue Service (Amazon SQS)`
- Summarize additional AWS compute options

## `EC2` at a basic level
Amazon Elastic Compute Cloud, or `Amazon EC2` for short, is your service for raw compute power. If we look at the coffee shop example from [Intro to AWS](./01-intro-to-aws.md), you know you're going to need compute power to serve `client` `requests` based on the `client-server model` we described there. `EC2` can provide you with the servers for that model.

These servers are virtual, and `EC2` is the service to access that compute power. Some of the benefits of `EC2` compared to running servers on premises are: 
- Highly flexible
- Cost-effective
- Quick

When we take a deeper look, these benefits will become more clear. Let's say you're going to install servers on premises, you'll need to research what type of server you need, how many you'll need, you have to order them and ship them to a data center, then you'll need to install and secure them, to be short, it is just a lot of work and all those steps don't come for free. AWS already took care of these steps, AWS already has:
- Purchased the servers
- Data centers
- Secured the data centers
- Hooked up the servers and they are ready to use

All you have to do is request the `EC2` instances you want, and they will be booted up and ready in minutes.

`EC2` runs on physical host machines managed by AWS, using virtualization technology to create isolated virtual machines, these machines are known as `EC2` instances. Typically you share a host with multiple instances, this concept is called `multi-tanancy`. This is managed by a `hypervisor` which orchestrates the allocation of the hosts resources while ensuring instances are isolated and unaware of each other.

`EC2` gives you flexibility and control, you can deploy or kill instances whenever you want and you can also configure them to run whatever you need like:
- The OS
	- Windows
	- Linux
- Internal business apps
- Web apps
- Databases
- Third-party software

They are also resize-able vertically, your app might need more resources as it grows, so you can choose to give it more CPU or more RAM. And you can also choose to scale it down whenever you want.

