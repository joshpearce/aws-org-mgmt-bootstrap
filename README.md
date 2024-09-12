# Org management account bootstrap

Some instructions and scripts (probably CloudFormation) to get the AWS org management account ready for Terraform

## Description

The steps I took and code I used to set up a personal AWS Org with Google Workspace as the IdP

## Getting Started

### Dependencies

* A Google Workspace account
* AWS CLI

### Steps

1. Create a new account at https://signin.aws.amazon.com/signup?request_type=register
1. Open Identity Center and click Enable
1. Choose to also create an organization
1. Open IAM and notice the following roles are created:
    1. AWSServiceRoleForOrganizations
    1. AWSServiceRoleForSSO
    1. AWSServiceRoleForSupport
    1. AWSServiceRoleForTrustedAdvisor
1. Registered a passkey with 1P (why is this here?)
1. Enabled Service Control Policies under AWS Organizations > Policies
1. Followed instructions here to use Google Workspace as an IdP, https://docs.aws.amazon.com/singlesignon/latest/userguide/gs-gwp.html
1. Once SSO is working, log in at, https://d-9a677b9b70.awsapps.com/start, use the access keys credentials to authenticate, and create the bootstrap resources with cloudformation, `aws cloudformation create-stack --stack-name tf-state-store --template-body file://cf-template.yml --region us-east-2`




