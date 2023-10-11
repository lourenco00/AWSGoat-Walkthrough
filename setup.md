# Installation

### Pre requisites
Install Terraform  
Create AWS Account  
On AWS Account, create a user by doing the following:  
  - Search "IAM" on the search bar
  - Create User button
  - Name it
  - attach policy "AdministratorAccess"
  - Create User
  - Add access key (Keep in mind you will only be able to see the secreet access key once)

## Main Setup
Fork the repo https://github.com/ine-labs/AWSGoat  
Go to Settings > Actions > Create Repository Secret and add there the 2 Variables: AWS_ACCESS_KEY AWS_SECRET_ACCESS_KEY  
Actions > Terraform Apply > (once it finished running) click on Application URL
