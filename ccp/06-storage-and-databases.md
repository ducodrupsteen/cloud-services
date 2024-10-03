# Storage and databases
We're going to look to how we can expand on our highly available and secure global network. We'll see what kind of databases and storage types can help us store our data.
We'll look at:
- [Instance Stores and Amazon Elastic Block Store (Amazon EBS)](#instance-stores-and-amazon-abs)
- [Amazon Simple Storage Service](#amazon-simple-storage-service) (Amazon S3)
- [Amazon Elastic File System](#amazon-elastic-file-system) (Amazon EFS)
- [Amazon Relational Database Service](#amazon-relational-database-service) (Amazon RDS)
- [Amazon DynamoDB](#amazon-dynamodb)
- [Amazon Redshift](#amazon-redshift)
- [AWS Database Migration Service](#aws-database-migration-service)
- Additional Database Services

## Instance Stores and Amazon EBS
Instance store are `Block-level storage`, this is like a physical hard drive. The kind of storage your PC uses. Instance stores provide temporary block-level storage for an `EC2` instance. It is a disk attached to the host of the `EC2` instance. When an instance is terminated, all data will be lost. So you don't want to store data that you need to persist. This is because `EC2` instances are virtual, when you stop and restart an instance, it might start on a different host then before.

To get persistent storage, you want to use Amazon Elastic Block Store or `Amazon EBS`. This provides block level storage that can be attached to an `EC2` instance. With `EBS`, you can terminate an `EC2` instance safely, the data on the attached `EBS` instance will remain. You can configure `EBS` to your liking, you can choose configurations such as volume size and type. Since you want the data on an `EBS` instance to persist it would be a smart thing to backup that data, that is why `EBS` allows you to take incremental backups called `Amazon EBS snapshots`.

`EBS snapshots` are incremental backups. This means that only the first backup is a complete backup of all the data, the ones following the first are only the blocks that have changed.

## Amazon Simple Storage Service
In `object storage` each object consist of data, metadata and a key. This data might be an image, video, text document or any other type of file. The metadata contains information about the file and the key is a unique identifier.

`Amazon S3` is a service that provides this type of object storage. It stores these objects in something called buckets. So you can see a object as a file and a bucket as a directory. You can upload any file type to a `S3` bucket like backup files,  media files, static assets or even static websites. Next to that you have full control who can access file through permissions.

## Classes
With `S3` you only pay for what you use. You can choose from different types of storage classes so you can fit it to your needs and budget. When choosing a plan, you should consider two factors:
1. How often do you plan to retrieve your data
2. How available you need your data to be

There are several types of storage classes:
- Standard
	- Designed for frequent access
	- Stores data in a minimum of 3 `AZ`s
- Standard-Infrequent Access (Standard-IA)
	- Ideal for infrequently accessed data
	- Similar to Standard but has a lower storage price and higher retrieval price
- One Zone-Infrequent Access
	- Stores data in a single `AZ`
	- Has a lower storage price than `Standard-IA`
- Intelligent-Tiering
	- Ideal for data with unknown or changing access patterns
	- Requires a small monthly monitoring and automation fee per object
- Glacier Instant Retrieval
	- Works well for archived data that requires immediate access
	- Can retrieve object within a few milliseconds
- Glacier Flexible Retrieval
	- Low-cost storage for data archiving
	- Able to retrieve object within a few minutes to hours
- Glacier Deep Archive
	- Lowest cost object storage, ideal for archiving
	- Able to retrieve objects within 12 hours
- Outpost
	- Create S3 buckets on Amazon S3 Outpost
	- Makes it easier to retrieve store and access data on AWS Outpost

## Amazon Elastic File System
In file storage, multiple clients can access data that is stored in shared folders. A storage server uses block storage with a local, Linux, file system to organize files. Clients can access the data through file paths.

Compared to block storage and object storage, file storage is ideal for handling a large number of clients.

`Amazon EFS` is an automatically scaled file system used with AWS Cloud services and on-premise resources.

### Compared to `EBS`
`EBS` volumes are stored in a **single** `AZ`. It is designed to be attached to an `EC2` instance. And both the `EC2` instance and `EBD` volume must life in the same `AZ`.

`EFS` stores data across multiple `AZ`s in a region. The duplicated storage allows for fast retrieval from any `AZ` within the region.

## Amazon Relational Database Service
`Amazon RDS` is a service to run relational databases in the AWS Cloud. `RDS` is a managed service, so you won't have to worry about provisioning hardware, setup, patching and backups. Thanks to this AWS enables you to spend less time on these administrative tasks and you can spend time on using data to innovate your applications. 
`RDS` integrates with other services, like `Lambda` to query your data from a serverless application. Next to that it offers different security options like encryption at rest or encryption in transit.

### Engines
`RDS` offers 6 different database options which optimize for memory, performance or I/O:
- Amazon Aurora
- PostgreSQL
- MySQL
- MariaDB
- Oracle Database
- Microsoft SQL Server

### Aurora
`Aurora` is an enterprise-class relational database. It's compatible with MySQL and PostgreSQL. It is up to five times faster than standard MySQL databases and up to three times faster then PostgreSQL. Aurora can help you reduce your database costs by reducing unnecessary I/O. It also copies your data six times across three different `AZ`s.

## Amazon DynamoDB
`DynamoDB` is non relational database. A non relational database does not adhere to a single structure, you could opt for a key-value pair structure. In a key-value pair structure you can add or remove attributes at any time, not every item in the table is required to have the same attributes.

`DynamoDB` is such a key-value pair database service. It delivers single digit milliseconds performance at any scale.

This is a serverless service that is fully managed, so no provisioning, patching, managing servers or installing or maintaining. It scales automatically based on the size of your database. 

## Amazon Redshift
`Redshift` is a data warehouse that you can use to analyze `big data`. Most databases tent to work great at certain capacities. The problem with historical data, that answers questions like "Show me how something improved overtime", is that the data collection never stops. The data can become overwhelming for even the beefiest relational databases. Not only volume, but the variety of data can be a problem. If you want to query projects against multiple databases, to analyze some store data for example, that sounds really nice, but it is not handled very well with traditional relational databases. This is where data warehouses come in. They are designed to query historical data like "How many orders did we get in the last hour in all of our stores".  Data warehouses are designed to handle these queries against massive datasets, or otherwise know as `big data`. `Redshift` helps you to collect data from multiple resources and understand the relationships and trends in your data.

## AWS Database Migration Service
`AWS Database Migration Service` helps you to migrate your databases and other types of data stores. You migrate from a source to a target database, and during this time, your source database will stay fully operational, and it does not matter if engines are the same.  For example, you have an on premises MySQL database and you want to migrate it to `RDS`, you could opt to use `DMS` to migrate your database to an `Aurora` database.

`DMS` also makes it easier to enable development against a production database, combine several database into one and sending ongoing data copies to targets instead of doing one-time migrations.

