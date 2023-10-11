# APIGateway

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
