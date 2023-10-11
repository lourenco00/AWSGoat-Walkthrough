# DynamoDB

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
