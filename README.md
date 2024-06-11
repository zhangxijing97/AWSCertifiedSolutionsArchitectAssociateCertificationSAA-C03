# AWSCertifiedSolutionsArchitectAssociateCertificationSAA-C03

## Table of Contents

1. [IAM & AWS CLI](#1-IAM-and-AWS-CLI)
2. [Amazon EC2 Basics](#2-Amazon-EC2-Basics)

## 1. IAM and AWS CLI
### IAM: Users & Groups
• IAM = Identity and Access Management, Global service<br>
• Root account created by default, shouldn’t be used or shared<br>
• Users are people within your organization, and can be grouped<br>
• Groups only contain users, not other groups<br>
• Users don’t have to belong to a group, and user can belong to multiple groups<br>

### IAM Policies Structure
• Version: policy language version, always include “2012-10-17”<br>
• Id: an identifier for the policy (optional)<br>
• Statement: one or more individual statements (required)<br>

Statements consists of: <br>
• Sid: an identifier for the statement (optional)<br>
• Effect: whether the statement allows or denies access (Allow, Deny)<br>
• Principal: account/user/role to which this policy applied to<br>
• Action: list of actions this policy allows or denies<br>
• Resource: list of resources to which the actions applied to<br>
• Condition: conditions for when this policy is ineffect (optional)<br>

IAMReadOnlyAccess Example:<br>
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "iam:GenerateCredentialReport",
                "iam:GenerateServiceLastAccessedDetails",
                "iam:Get*",
                "iam:List*",
                "iam:SimulateCustomPolicy",
                "iam:SimulatePrincipalPolicy"
            ],
            "Resource": "*"
        }
    ]
}
```

### Multi Factor Authentication - MFA
MFA = password you know + security device you own<br>

Virtual MFA device<br>
• Google Authenticator<br>
• Authy<br>

Universal 2nd Factor (U2F) Security Key<br>
• YubiKey by Yubico (3rd party)<br>

### How can users access AWS?
• AWS Management Console (protected by password + MFA)<br>
• AWS Command Line Interface (CLI): protected by access keys<br>
• AWS Software Developer Kit (SDK) - for code: protected by access keys<br>

#### What’s the AWS CLI?
CLI: Command Line Interface<br>
A tool that enables you to interact with AWS services using commands in your command-line shell<br>

#### What’s the AWS SDK?
• AWS Software Development Kit (AWS SDK)<br>
• Language-specific APIs (set of libraries)<br>
• Enables you to access and manage AWS services programmatically<br>
• Embedded within your application<br>

Supports:<br>
• SDKs(JavaScript,Python,PHP,.NET,Ruby,Java,Go,Node.js, C++)<br>
• Mobile SDKs (Android, iOS, ...)<br>
• IoT Device SDKs (Embedded C, Arduino, ...)<br>
• Example: AWS CLI is built on AWS SDK for Python<br>

#### AWS CLI Hands On?
```
aws configure
AWS Access Key ID [None]: Access key
AWS Secret Access Key [None]: Secret access key
Default region name [None]: us-west-1
Default output format [None]: 
(base) zhangxijing@Xijings-MacBook-Air ~ % aws iam list-users
{
    "Users": [
        {
            "Path": "/",
            "UserName": "xijing",
            "UserId": "AIDA4MTWNLEX7DI3CBOVM",
            "Arn": "arn:aws:iam::851725605167:user/xijing",
            "CreateDate": "2024-06-08T23:31:02+00:00",
            "PasswordLastUsed": "2024-06-08T23:53:09+00:00"
        }
    ]
}
```

List IAM Users
```
aws iam list-users
```

Create a New IAM User
```
aws iam create-user --user-name newusername
```

Attach a Policy to an IAM User
```
aws iam attach-user-policy --user-name newusername --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

List IAM Policies
```
aws iam list-policies
```

### IAM Roles for Services
• Some AWS service will need to perform actions on your behalf<br>
• To do so, we will assign permissions to AWS services with IAM Roles<br>

Common roles:<br>
• EC2 Instance Roles<br>
• Lambda Function Roles<br>
• Roles for CloudFormation<br>

### IAM Security Tools
IAM Credentials Report (account-level)<br>
• a report that lists all your account's users and the status of their various
credentials<br>

IAM Access Advisor (user-level)<br>
• Access advisor shows the service permissions granted to a user and when those
services were last accessed.<br>
• You can use this information to revise your policies.<br>

### IAM Section – Summary
• Users: mapped to a physical user, has a password for AWS Console<br>
• Groups: contains users only<br>
• Policies: JSON document that outlines permissions for users or groups<br>
• Roles: for EC2 instances or AWS services<br>
• Security: MFA + Password Policy<br>
• AWS CLI: manage your AWS services using the command-line<br>
• AWS SDK: manage your AWS services using a programming language<br>
• Access Keys: access AWS using the CLI or SDK<br>
• Audit: IAM Credential Reports & IAM Access Advisor<br>

## 2. Amazon EC2 Basics
EC2 = Elastic Compute Cloud = Infrastructure as a Service<br>

### EC2 sizing & configuration options
• Operating System (OS): Linux, Windows or Mac OS<br>
• How much compute power & cores (CPU)<br>
• How much random-access memory (RAM)<br>
• How much storage space: Network-attached (EBS & EFS), hardware (EC2 Instance Store)<br>
• Network card: speed of the card, Public IP address<br>
• Firewall rules: security group<br>
• Bootstrap script (configure at first launch): EC2 User Data<br>

#### Amazon EBS (Elastic Block Store)
• Persistent storage that retains data after instance termination<br>
• High performance for both throughput and IOPS (input/output operations per second)<br>
• Snapshots for backup and restore operations<br>
• Ability to resize volumes on the fly without downtime<br>

#### Amazon EFS (Elastic File System)
• Shared file storage with automatic scaling<br>
• High availability and durability<br>
• Integration with other AWS services<br>
• Support for multiple AZs (Availability Zones), providing high availability<br>

#### Hardware Storage
• High I/O performance since the storage is directly attached to the instance<br>
• Temporary storage that is deleted when the instance is stopped, terminated, or rebooted<br>
• No additional cost since it is included with the instance<br>