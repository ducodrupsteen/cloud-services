# Storage and databases
We're going to look to how we can expand on our highly available and secure global network. We'll see what kind of databases and storage types can help us store our data.
We'll look at:
- [Instance Stores and Amazon Elastic Block Store (Amazon EBS)](#instance-stores-and-amazon-abs)
- [Amazon Simple Storage Service](#amazon-simple-storage-service) (Amazon S3)
- Amazon Elastic File System (Amazon EFS)
- Amazon Relational Database Service (Amazon RDS)
- Amazon DynamoDB
- Amazon Redshift
- AWS Database Migration Service
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
