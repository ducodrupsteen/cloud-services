# AWS Cloud practitioner essentials
Here we will seek an overall understanding of AWS Cloud. We will look into AWS Cloud concepts, AWS services, security architecture, pricing and support. This resource will help with preparation for the `ccp` exam.

## Course outline
This resource will look into the following 11 modules and the assessment related to those modules:
1. [Intro to AWS and Cloud computing](#Intro%20to%20AWS%20and%20cloud%20computing)
2. Compute in the cloud
3. Global infrastructure and reliability
4. Networking
5. Storage and Databases
6. Security
7. Monitoring and Analytics
8. Pricing and Support
9. Migration and Innovation
10. The cloud Journey
11. AWS Certified cloud practitioner basics
12. Course final assessment

The first 10 modules will help us build knowledge by learning about AWS Cloud concepts, AWS services, security architecture, pricing and support. Module 11 will be preparation for the exam and the final assessment will conclude with a 30 question exam to test your knowledge.
## Intro to AWS and Cloud computing

### Intro to AWS
AWS offers a wide range of services for every kind of business. Basic services like compute, storage and network security tools to complex services like blockchain, ML, AI robotics and specialized tools for video production management and orbital satellites you can rent by the minute. 

There is to much to cover in one course, so we are going to focus on the fundamental cloud compute model.

Almost all modern computing is based around a basic `client-server model`.

If we take a simple coffee shop for example;
At some coffee shop, there is a barista, in this example they represent a server. And we have a customer, which represents a client. All the customer wants is a cup of coffee so the customer asks the barista for a coffee. Or we could say the client `requests` something from the server. This `request` could be anything, cat video's, weather data analysis of an x-ray of your knee, but in this case it is just a coffee.

The barista, which is a server, would be called an Amazon Elastic Compute Cloud, or `Amazon EC2` instance for short, in AWS, it is a virtual server.

In the real world this could become more complex then this example, now we have just one single server and client. But to prevent over complication right away we will build up this example.

One of the key concepts of AWS is; `You pay for what you use`.
This principle also makes sense in the coffee shop setting, employees are only payed when they are working. The store owner decides who and when the employees are working. Let's say you will be releasing a new drink, you can schedule all your workers in the case your shop runs full with customers, but for most of the day it won't be that busy so that is not justified.

At AWS you can simply toggle on and off instances for when the demand is either high or low. And you will only be billed for what you have used.

### Cloud computing
What is cloud computing? It is on-demand delivery of IT resources over the internet with pay-as-you-go pricing. We can break it down to:
- `On-demand delivery`; Get the resources you need, when you need them. It requires no deals beforehand on that you going to need them.
- `IT resources`; This is a big part of AWS philosophy, why does AWS have so many resources? Because businesses need them. The resources don't differentiate you from your competition, but how you use them does.
- `Over the internet`; Speaks for itself, you have a internet portal where you can orchestrate it all.
- `Pay-as-you-go pricing`; Pay for what you use, also kinda speaks for itself. Otherwise re-read the [intro](#Intro%20to%20AWS)

#### Deployment models for cloud computing
When it comes to selecting a cloud strategy, one must consider factors such as required cloud application components, preferred resource management tools and any legacy IT infrastructure requirements.

There are three deployment models:
- `Cloud-based deployment`
	- Run all parts of the application in the cloud.
	- Migrate existing applications to the cloud
	- Design and build new application to the cloud
- `On-premises deployment`
	- Deploy resources by using virtualization and resource management tools.
	- Increase resource utilization by using application managment and virtualization technologies
- `Hybrid deployment`
	- Connect cloud based resources to on-premise infrastructure
	- Integrate cloud-based resources with legacy IT applications

#### Benefits of cloud computing
Why would a company choose for a particular cloud computing approach? Here are some of the benefits:
- Trade upfront expense for variable expense
	- Instead of renting physical servers and other resources you switch to paying for computing resources you use
- Stop spending money to run and maintain data centers
	- You don't have to spend time and money managing data centers and infrastructure, with cloud computing you can focus on applications and customers
- Stop guessing capacity
	- With cloud computing, you don't have to predict how much infrastructure you will need before deploying an application.
- Benefit from massive economies of scale
	- By using cloud computing you can achieve a lower variable then you can get on your own
- Increase speed an agility
	- The flexibility of cloud computing makes it easier for you to develop and deploy applications
- Go global in minutes
	- The global footprint of AWS allows you to quickly deploy applications to any part of the world so your customers can use your software with low latency
