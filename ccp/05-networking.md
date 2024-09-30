# Networking
We now have a couple of things running in the cloud, but all our services might be exposed. for some services that might not make sense. This is where `VPC`s come in. Amazon `Virtual Private Cloud`, or `VPC`, lets you provision an isolated section of the AWS Cloud where you can launch resources on a virtual network. Then you can choose yourself if your resources are public or private. We will have a look at the following concepts:
- Describe the [basic concepts of networking](#basic-concept-of-networking)
- Describe the difference between public and private networking resources
- Explain a virtual private gateway using a real life scenario
- Explain a virtual private network, VPN, using a real life scenario
- Describe the benefit of AWS Direct Connect
- Describe the benefits of hybrid deployments
- Describe the layers of security used in an IT strategy
- Describe the services customers use to interact with AWS global network

## Basic concept of networking
A `VPC` allows you to define your private IP range for you AWS resources, and you place things like `EC2` instances ans `ELB`s inside of you `VPC`.
Now you don't just throw you services in there and be done. You want to create chunks of IP addresses and group your resources, these chunk are called `subnets`. Subnets, together with networking rules, control whether resources are private or public. 