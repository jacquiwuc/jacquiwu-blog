# [Introduction to Terraform](https://github.com/jacquiwuc/jacquiwu-blog/issues/1)

Just imagine you are a customer of a cloud provider and you want to spin up some machines, you can go into some web console, fill in some forms, click some buttons and then launch an instance. But you can also use Terraform.


Terraform allows you to do the same thing but in code, i.e., Infrastructure as Code. It is the automation of your infrastructure and keep your infrastructure in a certain state. For example, you want to spin up 5 small instances and whenever you run Terraform, it will ensure that those run on a cloud platform. When we change something manually, Terraform will try to match the code with the actual infrastructure.

It will also make your infrastructure auditable. Just look at .tf files, we can see what the infrastructure is made of. And even better, we can keep changes in Version Control System, e.g., git.

Download and Install
Terraform can be downloaded and installed in different operational systems, pls check it out on official website.

After downloading and installing Terraform, lets verify it.

Use “terraform -v” in terminal, if the result shows the version, then it can verify if terraform is installed and everything works properly. However, if the result is “Terraform is not a command” or anything like this, there is an issue happen.

The last step in setting is to use an IDE to manage, e.g., Visual Studio.

What Language Terraform supports?
Terraform language is called Hashicorp configuration language in a file that has a .tf extension, so all of our Terraform codes will be stored in a file with .tf extension.

Let’s start!
Now we can create a new project in our own IDE and name it. Then we create a file called main.tf.

At this point, what providers Terraform can support can be checked out on their website.

For example, if we click into AWS Provider, we can see there is an example how to configure the AWS Provider.

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 3.0"
    }
  }
}

# Configure the AWS Provider
provider "aws" {
  region = "us-east-1"
}

# Create a VPC
resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}

```We can copy and paste the part of “Configure the AWS Provider” codes in our main.tf file. And we can check what region we are in AWS and modify it.

Now we get the provider set up and if we go back to Terraform tutorial, it continues to teach us how to set things up. And the next thing to set up the Authentication.


We can take the hard-coding way to have a look: create static creditials. It is not recommended because if we publish the .tf file into Github or something else, the credentials will be stored there, which will cause a security vulnerability problem.

Now using this way just keeps things simper but later we will use a securer way.

From the tutorial, it can be seen that we need three parameter values: region, “access_key” and “secret_key”. Now we can go to AWS console and check those information in Identity and Access Management(IAM) service.

We can create an access key in IAM service. And then we click “show access key” and store those 2 values: “access_key” and “secret_key”.

Then let’s try to create and provision resources within AWS. The syntax is quite simple and same whatever you configure Azure, AWS or GCP in Terraform.

The resources syntax is shown as below:

```
resource "<provider>_<resource_type>""name"{
    config options....
    key = "value"
    key2= "another value"
}
```
So this is how to create a resources within a provider. Let us to try to create and deploy a EC2 instance in Terraform.

We need to refer back to the documentation now because we need to put value as “resource_type”:

```
resource "aws_instance" "web" {
  ami           = data.aws_ami.ubuntu.id
  instance_type = "t3.micro"

  tags = {
    Name = "HelloWorld"
  }
}
```
We can find such an example and it is barely what the minimum we need. We can copy and paste these codes in our main.tf file.

The “resource_type” in the example is “aws_instance”. We can give it a name and call it what we want to replace “web” in the example. “ami” value can be got if we launch an instance in EC2 service on AWS, then we can put the value into the example. And the “instance_type” is what we select in the AWS console as well.

As in the documentation, the “tags” is optional so we can delete it.

The next thing is go to terminal of your IDE, which is suggested because it will navigate to your project directory automatically. The first Terraform command we need to learn is “Terraform init”. This command will look at the config, which is all .tf files in our project. Because we just have one provider which is AWS, so it will download all necessary plugins to interact with AWS api.

After we run it in terminal, we can see it is initializing the backend and initializing provider plugins and so on. If we add another provider for Azure, then it will also download another plugin for Azure.

After it is successful, the second Terraform command we need to know is “Terraform plan”. Even it is completely optional, but it is a quick sanity check to make sure we won’t break anything. If we have a look at what is happening, it will color code things depending on the action.

“+” means creating a resource
“-“means deleting a resource
“~”means modifying an existing resource
The final command is “Terraform apply” and it will ask you to hit “yes” then it will create our server. Then it will show “Apply complete! Resources 1 added, 0 changed, 0 destroyed”.

Then we can verify it in our AWS console. At this point, we can see the first EC2 instance is deployed through Terraform.

There are more things we can learn in Terraform, maybe talk about it in next blog.

If you are interested in or have any problems with Terraform, feel free to contact me.

Or you can connect with me through my LinkedIn.