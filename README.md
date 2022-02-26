# nextcloud-1-terraform

# Prerequisites

## Ensure AWS Creds Exist

```bash
#Ensure AWS creds exist in `~/.aws/credentials`
$ cat ~/.aws/credentials
[default]
aws_access_key_id=djjgoijd
aws_secret_access_key=8dh3hgf8hfoih
```

### Generate Permission (.pem) File

1.  Log into AWS console
2.  Navigate to the EC2 service
3.  Left panel -> Under 'Nextwork & Security' -> Select 'Key Pairs'
4.  Select the orange 'Create key pair' button in the middle panel
5.  Enter 'nextcloud-1' for the name
6.  Select 'Create key pair'
7.  Download the pem file and copy to this directory
    - `$ cp ~/Downloads/nextcloud-1.pem .` might work in the terminal

# Install Terraform (Locally)
Guide - https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/aws-get-started

```bash
# Install required packages
$ sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl

# Add the HashiCorp GPG key
$ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -

# Add the hashiCorp Linux repo
$ sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

# Update repo
$ sudo apt-get update

# Install Terraform CLI
$ sudo apt-get install terraform

# Confirm Install
$ terraform -h

# These are not required but nice to have

# Ensure this file exists
$ touch ~/.bashrc

# Install the auto-complete package
$ terraform -install-autocomplete
```

# Execute Terraform 

```bash
# Initalize - downloads and installs the providers defined in the configuration
$ terraform init

# Format - automatically updates configurations in the current directory for readability and consistency
$ terraform fmt

# Validate - ensure configuration is syntactically valid and internally consistent
$ terraform validate

# Apply - apply the configuration
$ terraform apply
# enter 'yes' when prompted
```

Everything should be up and running.  Log into the AWS console and see if the EC2 instance is in the 'Running' state.