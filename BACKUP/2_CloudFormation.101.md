# [CloudFormation 101](https://github.com/jacquiwuc/jacquiwu-blog/issues/2)

What is CloudFormation?

![image](https://user-images.githubusercontent.com/44564577/132982432-227d8261-0aca-4262-8192-eb245d1f7e24.png)


CloudFormation is a tool which can spin up resources on AWS. If someone wants to be an AWS expert, CloudFormation is an essential service to master.

Before we jump into writing a CloudFormation template, let’s have a brief history about how to manage AWS infrastructure before CloudFormation.

Without CloudFormation, automating a process is time-consuming because of building tools to assist with automation, e.g., log in AWS console and manually provision servers.


Maybe it is a fast way to write some scripts to get job done and it will generally work fine at a small scale, however if we need to manage more systems in more environments, it will become tedious.

So that is why configuration management tools exist.

There are some popular tools like Chef, Puppet, Salt etc. They can be used to maintain consistency and track changes. However, their disadvantages are it is not necessatily needed for containerized application deployments.

So there is another way: Infrastructure as Code

Infrastructure as Code is all about having a single souce of truth that serves as a blueprint for what we want the infrastructure look like.

Templates are written using a DSL that describes resources and relationships, e.g., CloudFormation and Terraform.

Their pros:

* Consistency
* Auditing
* Complicance
* Rollbacks

What languages CloudFormation supports?
The answer is JSON /YAML

Let’s take a look at a JSON template (a template respresents a stack, the components with the stack are known as resources):

```
{
  "AWSTemplateFormatVersion":"2010-09-09",
  "Description":"Create a S3 bucket",
  "Resources":{
  "datalake":{
    "Type":"AWS::S3::Bucket"
             }
}
}
```
Inside Resources, uniquely named keys are mapped to specific AWS resources. In our example, this CloudFormation template is used to create a S3 bucket in AWS.

Functions:
CloudFormation also supports some functions, and the most useful is Ref, it is used to pass value.

Next blog we will continue our journey with AWS.

If you are interested in or have any problems with CloudFormation, feel free to contact me .

Or you can connect with me through my LinkedIn.