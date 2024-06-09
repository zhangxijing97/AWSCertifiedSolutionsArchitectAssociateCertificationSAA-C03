# AWSCertifiedSolutionsArchitectAssociateCertificationSAA-C03

## Table of Contents

1. [IAM & AWS CLI](#1-IAM-and-AWS-CLI)

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
• Supports<br>
    • SDKs(JavaScript,Python,PHP,.NET,Ruby,Java,Go,Node.js, C++)<br>
    • Mobile SDKs (Android, iOS, ...)<br>
    • IoT Device SDKs (Embedded C, Arduino, ...)<br>
• Example: AWS CLI is built on AWS SDK for Python<br>