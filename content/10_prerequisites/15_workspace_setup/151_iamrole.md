---
title: "Create an IAM role for your workspace"
chapter: false
weight: 132
---

{{% notice info %}}
Starting from here, when you see command to be entered such as below, you will enter these commands into Cloud9 IDE. You can use the **Copy to clipboard** feature (right hand upper corner) to simply copy and paste into Cloud9. In order to paste, you can use Ctrl + V for Windows or Command + V for Mac.
{{% /notice %}}

1. Follow [this deep link to create an IAM role with Administrator access.](https://console.aws.amazon.com/iam/home#/roles$new?step=review&commonUseCase=EC2%2BEC2&selectedUseCase=EC2&policies=arn:aws:iam::aws:policy%2FAdministratorAccess)
2. Confirm that **AWS service** and **EC2** are selected, then click **Next: Permissions** to view permissions.
3. Confirm that **AdministratorAccess** is checked, then click **Next: Tags**, then **Next: Review** to review.
4. Enter `Lumigo-Workshop-Admin` for the Role name, and select **Create role**

{{% notice info %}}
When you create IAM policies in your production account, follow the standard security advice of granting [least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html), or granting only the permissions required to perform a task. Determine what users (and roles) need to do and then craft policies that allow them to perform only those tasks.

{{% /notice %}}