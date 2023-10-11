# AWSGoat-Walkthrough
Walkthrough of AWSGoat Modules

## Module 1

The first module features a serverless blog application utilizing AWS Lambda, S3, API Gateway, and DynamoDB. It consists of various web application vulnerabilities and facilitates exploitation of misconfigured AWS resources.

Escalation Path:

![Description Module 1](https://user-images.githubusercontent.com/65826354/179526761-7f473e3d-f71c-429d-bf49-16958c5cb7a6.png)

URL: https://j4nbgp3ssj.execute-api.us-east-1.amazonaws.com/prod/react

## Move to Module 2

````
git clone https://github.com/....
cd AWSGoat/modules/module-2
terraform init
terraform apply --auto-approve
````

## Module 2

The second module features an internal HR Payroll application, utilizing the AWS ECS infrastructure. It consists of various web application vulnerabilities and facilitates exploitation of misconfigured AWS resources.

Escalation Path:

![Description Module 2](https://user-images.githubusercontent.com/65826354/194799899-2968e04a-c324-4c3a-bdf2-b33f86fc0e05.png)

URL: aws-goat-m2-alb-262475468.us-east-1.elb.amazonaws.com:80/login.php 
