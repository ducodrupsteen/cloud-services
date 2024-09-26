# Compute in the cloud
This module mostly focused on `Amazon EC2` to summarize what we will learn:
- Describe the benefits of [`EC2` at a basic level](#ec2-at-a-basic-level)
- Identify the different [`EC2` instance types](#ec2-instance-types)
- Differentiate between the various [billing options for `EC2`](#ec2-pricing)
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

## `EC2` instance types
AWS provide different types of `EC2` instances to fit your needs. All these `instance types` are grouped under certain `instance families` and are optimized for certain tasks. `Instance types` offer different combinations of `cpu`, `memory`, `storage` and `networking capacities`. So you can choose a type that really fits your needs. 

The different types of families are:
- General purpose
	- Balanced resources
	- Diverse workloads
	- Web servers
	- Code repositories
- Compute optimized
	- Compute intensive tasks
	- Gaming servers
	- High performance computing (HPC)
	- Scientific modeling
- Memory optimized
	- Memory intensive tasks
	- Large datasets in memory
	- High performance databases
- Accelerated computing
	- Floating point number calculations
	- Graphics processing
	- Data pattern matching
- Storage optimized
	- High performance for local data

## `EC2` billing options
How much does it all costs? There are multiple types of billing options, depending on the instance type and operating system you choose.

### On-Demand
You only pay for the time your instance runs. This can be per hour or per second. This allows for no upfront payments or long term commitment.
This is usually where you start, so you can spin up instances and play around with it.

### Savings plan
This offers low prices on `EC2` usage in exchange for a commitment for consistent usage, this is measured per hour and can be contracted for a 1 or 3 year term. Most of the time this results in a 72% lower costs on your `EC2` billing regardless of the instance type or family, size or region. This also applies to `AWS Faregate` or `AWS Lambda` which are serverless compute services.

### Reserved instances
This is suited for predictable usage and a steady workload. You can need to specify a instance family and size, platform, tenancy and region. When using `Reserved instances`, it can result in a 75% discount in comparison to the `On-Demand` pricing plan. This discount will apply once you commit to a 1 or 3 year plan, you can choose how you want to pay for it with 3 options. `Full upfront` where you pay everything upfront, `partial upfront` where you pay just a small part or `no upfront` where you don't pay anything upfront.

### Spot instances
This is probably the cheapest and gives you up to 90% discount on the `On-Demand` pricing options. With `Spot instances` you request spare `EC2` computing power, the only catch is that Amazon can take back the instance, whenever they want, they will give you a 2 minute warning to finish up the work and save state.

### Dedicated hosts
Here you will rent a whole host. These are used to meet certain compliance requirements and you won't share the tenancy with anyone else.

