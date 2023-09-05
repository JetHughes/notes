---
title: "ass01-security-audit"
aliases: 
tags: 
- assignment
- comp210
---

# Security Audit for Awesome Web Site
Jet Hughes - 9474308

## Summary of system
### Function
This system is a simple website for a store called Things & Co. It allows users to create an account, login, and view their products. There are four pages: Home, Create Account, View Catalogue, and Log In. The home page is a simple landing page with a brief description of the website and some images. The View Catalogue page shows information about the list of products the store sells. It also allows the user to search for products.

To create an account the user must provide a Username, Real name, email, address, credit card information and a password. They are then able to log in to their account using the Login page. 

### Technology
It is a Web application running on a local virtual machine using Java Servlets and JSPs in the Tomcat Web server. It also uses an H2 database for storage of user, and product data. 

## Flaws
### SQL Injection 
CWE: 89

It is possible to inject SQL into the database using the login username field, and display it in the browser as the "username" of the logged-in user.

The first thing I attempted was to log in using the username " 'or 1=1;--". This worked and I was logged in as administrator.
After that, I created an account. When I noticed that my username was displayed in the browser I attempted to extract data from the database and display is as this username. 

In the username field of the login form, I entered the string:

' union select group_concat(username||':'||password||':'||name||':'||credit_card_number||':'||credit_card_expiry||':'||credit_card_cvv) from user as name;--

' union (select TABLE_NAME, TABLE_SCHEMA, 1, 2 FROM information_schema.tables) ;--

This resulted in all the user's data, credit card information, and hashed passwords being displayed in the browser. I was then able to crack 48 of the passwords using Hashcat and the rock you word list. 

An attacker would not know the names of the fields or the tables. However, security through obscurity is not sufficient and an attacker could guess or otherwise find the information.

### Cross site scripting/JavaScript injection
CWE: 79

The product catalogue is visible to other users. This means if we were able to update the product information in the database, we could run JavaScript on the browser of other users.

Since we are able to inject SQL using the username field on the login page, we can execute an UPDATE command on the database. This is the input I used:

'; update PRODUCT set DESCRIPTION = '<script>alert("hello")</script>' where PRODUCT_ID = 67696;--

An attacker could use this to present the user with an unsafe link, or export data such as session ID's and cookie data to a remote server where they can view it.

I was also able to create an account with the username ''<script>alert("hello")</script>", however when I logged in, the alert was not shown and the username in the login page was blank. 

### Password policy
CWE: 521

This website only requires that the user's passwords have 5 character and 1 number. Upper-case letters and numbers are not required. This results in a character set size of 36, and a Shannon Entropy of 15 bits.

This does not result in a secure password, and means the passwords can be easily cracked. It is also likely that many of the passwords will be simply 5 letters, then a number. This makes it very easy to crack these passwords using a pattern technique.

### Use of a Broken or Risky Cryptographic Algorithm
CWE: 327

The website uses md5 to hash the passwords, which is not a secure hash function. Furthermore, the passwords are not salted or peppered.

I was able to crack 48 of the 100 passwords using Hashcat and the rockyou word list with the command: hashcat.exe -m 0 -a 0 pwds.txt rockyou.txt.

### Improper Restriction of Excessive Authentication Attempts
CWE: 307

The login page does not restrict the number of login attempts. This means it is possible for an attacker to attempt many passwords to gain access to an account.

### Path traversal
CWE: 22
- You can access the welcome page simply using the path /catalogue/welcome.jsp. This will load the welcome page with the username null. However, it is unclear whether this is a security issue as currently the welcome page offers no functionality. 
- I don't think there are any path traversal flaws in this website. This is because there isn't any URLs which contain queries or parameters relating to sensitive pages. 

### Cleartext Transmission of Sensitive Information
CWE: 319

When a user logs in, their username  and unhashed password are transmitted in a cleartext post request to the server. This information is susceptible to a man in the middle attack and other methods of interception.

#### Example payload:
![example payload](https://i.imgur.com/9Tn6gx1.png)

## Conclusion
This system is not secure. I was able to identify multiple vulnerabilities, and successfully carry out attacks to exploit these vulnerabilities. 

The most severe of these was a simple SQL Injection attack. I was able to extract the credit card information of all the users, and crack the passwords of nearly 50% of the accounts. This is a major security issue. 

I was also able to inject JavaScript code into the database, which would then be run on the browser of other users. 

Furthermore, the system does not have adequate password policy and allows users to choose weak passwords. It also allows excessive authentication attempts.
