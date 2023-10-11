## Lambda
#### List Lambda Functions

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
#### Found JWT Secret:

            "Environment": {
                "Variables": {
                    "JWT_SECRET": "T2BYL6#]zc>Byuzu"
                }
            },
            
#### Get Function blog-application
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
#### Get Function blog-application-data
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
