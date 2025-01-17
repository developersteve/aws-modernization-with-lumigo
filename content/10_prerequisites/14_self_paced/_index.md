---
title: "Part 2: On your own"
chapter: true
draft: false
weight: 120
---

### Running the workshop on your own


{{% notice warning %}}
Only complete this section if you are running the workshop on your own. If you are at an AWS hosted event (such as re:Invent, Kubecon, Immersion Day, etc), go to [Start the workshop at an AWS event](../13_aws_event.html).
{{% /notice %}}

{{% notice warning %}}
Your account must have the ability to create new IAM roles and scope other IAM permissions.
{{% /notice %}}

{{% notice warning %}}
You are responsible for the cost of the AWS services used while running this workshop in your AWS account.
{{% /notice %}}

1. If you don't already have an AWS account with Administrator access: [create
one now by clicking here](https://aws.amazon.com/getting-started/)

1. Once you have an AWS account, ensure you are following the remaining workshop steps
as an IAM user with administrator access to the AWS account:
[Create a new IAM user to use for the workshop](https://console.aws.amazon.com/iam/home?#/users$new)

1. Enter the user details:
![Sysdig Trial](/images/10_prerequisites/iam-1-create-user.png)

1. Attach the AdministratorAccess IAM Policy:
![Sysdig Trial](/images/10_prerequisites/iam-2-attach-policy.png)

1. Click to create the new user:
![Sysdig Trial](/images/10_prerequisites/iam-3-create-user.png)

1. Take note of the login URL and save:
![Sysdig Trial](/images/10_prerequisites/iam-4-save-url.png)
