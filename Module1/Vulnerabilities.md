# Vulnerabilities Exploited

### Reflected XSS

On Home Page search bar type: <img src="A" onerror=alert('XSS')>  

![Screenshot_2023-10-12_10_40_55](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/60b9e024-8a18-41f2-bba5-a3a2a4ccc517)

### SQL Injection

Once you logged in go to Dashboard > Users, and type    ' or '1'='1'    
And it will retrieve all users.  

![image](https://github.com/lourenco00/AWSGoat-Walkthrough/assets/91602746/8e31bb32-6dbc-4e1b-9421-5172e3c14e26)
