<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Access S3 from a VPC

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-s3)

**Author:** Ashish Kumar  
**Email:** ashishjp82@gmail.com

---

## Access S3 from a VPC

![Image](http://learn.nextwork.org/excited_amber_silly_fennel/uploads/aws-networks-s3_3e1e79a2)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a networking service in AWS that lets you create a logically isolated section of the cloud where you can launch and manage your resources securely. Itʼs like having your own private data center inside AWS, but with the flexibility and scalability of the cloud. It is useful because it gives you full control over your network environment: you can define IP address ranges, create subnets (public and private), configure route tables, attach internet gateways, and manage traffic using security groups and network ACLs. VPCs also improve security by keeping resources isolated, and allows scalability by letting you easily grow your infrastructure. Essentially, itʼs the foundation for running secure and organized workloads in AWS.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to learn how resources inside VPC like EC2 instance can connect with the AWS services outside VPC. I created S3 bucket and then connected to the EC2 instance and from the EC2 terminal, was able to list s3 buckets and objects, and also uploaded a file in the S3 bucket.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the fact that I had to separately create Access Key, so that the EC2 instance can access any other AWS service. It was a great learning for me.

### This project took me...

This project took me almost 90 minutes which included creating a VPC and public EC2 instance inside of it. Then configuring IAM Access Keys and Secrete Acces Keys, creating S3 bucket and then finally from the EC2 instance terminal accessing the S3 bucket.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will create a VPC from scratch and launch an EC2 instance inside of the VPC, because later I will demonstrate how this EC2 instance can communicate with S3 bucket outside of VPC.

### Step 2 - Connect to my EC2 instance

In this step, I will use EC2 Instance Connect because it helps get direct access to my EC2 instance. Once I get direct access to the EC2 instance, then from the instance terminal, I can do some advanced work like installing software into my instance or accessing another AWS service.

### Step 3 - Set up access keys

In this step, I will set up access keys because it will allow the EC2 instance to access the AWS environment and its services like S3 bucket.

---

## Architecture set up

I started my project by launching the VPC using just one availability zone and having one public subnet and zero private subnets. Then I launched an EC2 instance in my public subnet and enabled Auto Assign IPv4 address, with the instance's security group allowing SSH traffic.

I also set up an Amazon S3 bucket and uploaded two files in it.

![Image](http://learn.nextwork.org/excited_amber_silly_fennel/uploads/aws-networks-s3_4334d777)

---

## Running CLI commands

AWS CLI (Command Line Interface) is a software that we install and run on our computer to control AWS services directly from the command line i.e. the terminal. I have access to AWS CLI, since I can connect into my instance terminal via EC2 Instance Connect, and all EC2 instances come with pre installed AWS CLI.


The first command I ran was aws s3 ls. This command is used to list all the s3 buckets in my AWS account.

The second command I ran was "aws configure". This command is used to configure credentials, which allows us to access and manage AWS services securely. Without credentials, we won't have the permission to do things like viewing your S3 bucket list.

![Image](http://learn.nextwork.org/excited_amber_silly_fennel/uploads/aws-networks-s3_e7fa8776)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured the credentials in the EC2 terminal by running "aws configure" command. These credentials contain Access Key and Secret access key which I got when I created it in the IAM console.

Access keys are the credentials for applications and other servers to log into AWS and talk to the AWS services.

Secret access keys are like a password that pairs with the access key ID (the username). We need both to access AWS services.
Secret is a key word here, anyone who has it can access your AWS account, so we need to keep this away from anyone else.

### Best practice

Although I'm using access keys in this project, a best practice alternative is to create an IAM role with the necessary permissions and then attaching that role to my EC2 instance. 

The EC2 instance would then inherit the permissions from the role. This is a best practice as we can easily attach and detach EC2 instances from roles to give and take away their credentials.

---

## In the second part of my project...

### Step 4 - Set up an S3 bucket

In this step, I will lauch a bucket in Amazon S3 because it will help me to learn how to access S3 from our VPC, when we will connect to the S3 bucket from our EC2 instance and do things like checking what objects are in the bucket.

### Step 5 - Connecting to my S3 bucket

In this step, I will head back to my EC2 instance and get my EC2 instance to interact with the S3 bucket.

---

## Connecting to my S3 bucket

The first command I ran was aws s3 ls. This command is used to list all the s3 buckets in my AWS account.

'When I ran the command "aws s3 ls" again, the terminal responded with the list of S3 buckets in my AWS account. This indicated that the credentials have successfully been configured and EC2 instance is now able to access S3 service.

![Image](http://learn.nextwork.org/excited_amber_silly_fennel/uploads/aws-networks-s3_4334d778)

---

## Connecting to my S3 bucket

Another CLI command I ran was "aws s3 ls s3://nextwork-vpc-project-ashishkr" which returned the objects in the bucket: nextwork-vpc-project-ashishkr.

![Image](http://learn.nextwork.org/excited_amber_silly_fennel/uploads/aws-networks-s3_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command "sudo touch /tmp/test.txt/". This command creates a empty file named test.txt inside the folder tmp.

The second command I ran was "aws s3 cp /tmp/test.txt s3://nextwork-vpc-project-ashishkr". This command will copy the test.txt file inside the tmp folder to the s3 bucket :  nextwork-vpc-project-ashishkr.

The third command I ran was "aws s3 ls s3://nextwork-vpc-project-ashishkr" which validated that the test.txt file was indeed uploaded to the S3 bucket.

![Image](http://learn.nextwork.org/excited_amber_silly_fennel/uploads/aws-networks-s3_3e1e79a2)

---

---
