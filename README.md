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
• Version: policy language version, always include “2012-10- 17”<br>
• Id: an identifier for the policy(optional)<br>
• Statement: one or more individual statements(required)<br>

Statements consists of
• Sid: an identifier for the statement(optional)<br>
• Effect: whether the statement allows or denies access (Allow, Deny)<br>
• Principal: account/user/role to which this policy applied to<br>
• Action: list of actions this policy allows or denies<br>
• Resource: list of resources to which the actions applied to<br>
• Condition: conditions for when this policy is ineffect (optional)<br>