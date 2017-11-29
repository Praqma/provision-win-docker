# Instructions

Set your AWS keys:

      export AWS_ACCESS_KEY_ID=<<access_key>>
      export AWS_SECRET_ACCESS_KEY=<<secret_key>>

You can generate the AWS AMI and store it in your AWS account by running the following command:

> default region is eu-central-1, you can override it with -var region=<<another_region>>

      cd packer
      packer build packer-win-ami.json -var instance_type=t2.small

Now you can run terraform to provision VMs:

> default region is eu-central-1, you can override it with -var region=<<another_region>>

      cd terraform
      terraform plan -var admin_password=<<some password>> -var instance_count=<<number of VMs>>

Destroy the resources created by terraform:

      terraform destroy

> running terraform may end with an error, but usually creates the VMs.