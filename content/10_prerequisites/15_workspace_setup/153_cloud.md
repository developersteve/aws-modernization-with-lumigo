﻿---
title: "Configure workspace for Lumigo Workshop"
chapter: false
weight: 134
---

  1. Return to your workspace and click the gear icon (in top right corner), or click to open a new tab and choose "Open Preferences"

  2. Select **AWS SETTINGS** and turn off **AWS managed temporary credentials**
     ![Cloud9 AWS Settings](/images/10_prerequisites/cloud9-aws-settings.png)

  3. Close the Preferences tab
     
  4. Copy and run (paste with **Ctrl+P**) the commands below into the terminal window. Click **Enter** to execute last command. You should see *"IAM role valid"* message if everything ran correctly.
{{% notice tip %}} 
Before running it, you can review what it does by reading through the comments. 
{{% /notice %}}
     
```sh
# Update awscli
sudo pip install --upgrade awscli && hash -r

# Install jq command-line tool for parsing JSON, and bash-completion
sudo yum -y install jq gettext bash-completion moreutils

# Install yq for yaml processing
echo 'yq() {
docker run --rm -i -v "${PWD}":/workdir mikefarah/yq yq "$@"
}' | tee -a ~/.bashrc && source ~/.bashrc

# Verify the binaries are in the path and executable
for command in jq aws
do
  which $command &>/dev/null && echo "$command in path" || echo "$command NOT FOUND"
done

# Remove existing credentials file.
rm -vf ${HOME}/.aws/credentials

# Set the ACCOUNT_ID and the region to work with our desired region
export AWS_REGION=$(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r '.region')
test -n "$AWS_REGION" && echo AWS_REGION is "$AWS_REGION" || echo AWS_REGION is not set

# Configure .bash_profile
export ACCOUNT_ID=$(aws sts get-caller-identity --output text --query Account)
echo "export ACCOUNT_ID=${ACCOUNT_ID}" | tee -a ~/.bash_profile
echo "export AWS_REGION=${AWS_REGION}" |
tee -a ~/.bash_profile
aws configure set default.region ${AWS_REGION}
aws configure get default.region

# Validate that our IAM role is valid.
aws sts get-caller-identity --query Arn | grep Lumigo-Workshop-Admin -q && echo "IAM role valid" || echo "IAM role NOT valid"
```

{{% notice warning %}}
If the IAM role is not valid, <span style="color: red;">**DO NOT PROCEED**</span>. Go back and confirm the steps on this page.
{{% /notice %}}

<!--
### Explanation of the commands:

Actions executed:

:small_blue_diamond: Install jq - jq is a command-line tool for parsing JSON

:small_blue_diamond: Ensure temporary credentials aren’t already in place.

:small_blue_diamond: Remove any existing credentials file.

:small_blue_diamond: Set the region to work with our desired region.

:small_blue_diamond: Validate that our IAM role is valid.

:small_blue_diamond: Copy two scripts into place for use later in the workshop.

-->

### Setup access to GitHub in Cloud9 environment

1. Generate SSH key pair and display the public key to be copied to GitHub. Leave the default file name by pressing enter when asked for a file to save the key, and enter the passphrase on your choice (twice to confirm). You will see the key starting from "ssh-rsa"
   ```sh
   ssh-keygen -t rsa && \
   cat /home/ec2-user/.ssh/id_rsa.pub
   ```
1. Go to your GitHub account [keys](https://github.com/settings/keys), click "New SSH key", add a title (for example `Lumigo Workshop Cloud9 Environment`), insert public key into "Key" section and click "Add SSH key"

1. Check SSH agent is running, and add private SSH key to the registry. Enter your passphrase when asked
   ```sh
   eval $(ssh-agent -s) && \
   ssh-add /home/ec2-user/.ssh/id_rsa
   ```

{{% notice tip %}}
Use command **clear** in the terminal to clean it from previous outputs.
{{% /notice %}}