# Global infrastructure
AWS has data centers all over the world. Those data centers are divided into `regions`. In this module we'll go into debt about those regions and we'll learn the following:
- Summarize the benefits of [AWS Global Infrastructure](#aws-global-infrastructure)
- Describe the basic concept of [Availability Zones](#availability-zones)
- Describe the benefits of Amazon CloudFront and edge locations
- Compare different methods for provisioning AWS services

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

