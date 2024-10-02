# Storage and databases
We're going to look to how we can expand on our highly available and secure global network. We'll see what kind of databases and storage types can help us store our data.
We'll look at:
- [Instance Stores and Amazon Elastic Block Store (Amazon EBS)](#instance-stores-and-amazon-abs)
- Amazon Simple Storage Service (Amazon S3)
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