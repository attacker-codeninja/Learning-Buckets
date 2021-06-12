---
typora-copy-images-to: images
---

# Learning Buckets 1

---



[TOC]

---

## 1. Medium Write-ups



### 1.1 Attacking Social Logins: Pre-Authentication Account Takeover

Link => https://hbothra22.medium.com/attacking-social-logins-pre-authentication-account-takeover-790248cfdc3



* If attacker Bypass Authentication Implementation Mechanism, Then he can =>
  * perform Privileged Actions
  * enumerate sensitive information 
  * And can cause Business  Logical Problems
* Modern Browsers  allow their users to 
  * register/enrol using multiple methods such as 
    * **registration via email, registration via Social Logins and other methods**
  * Log in via **OAuth2.0** and **SAML**  based authentication considered as Secure
    * **But => If not implemented correctly** => Problem is their as Vulnerability
* What is **Pre-Authentication Account Takeover Vulnerability ?**
  * This vulnerability occur due to **lack of email verification in application** + **improper implementation of social logins**
  * **Requirements for this Attack ?**
    * **Lack of Email Verification**
      * Either application not have an email verification OR should be **bypassable**
      * Often During creating account - application often require to verify their email
      * But if there is **misconfiguration**  an attacker would register an account in the application using the victim user’s account => ** **Pre-Authentication****
    * **Social-Logins**
      * Target must support at least one Social Logins [such as Google, FB, Twitter, Linkedin , Gothub]
      * Also Victim's email must be used on those Social Media Account
    * **Victim User's Email**
      * Enumerate Emails to get User's Email
* **ATTACK Steps =>**
  * After registered to application => The Application automatically allowed to login to the application
    * So, It means => **No Email Verification**
  * Application => Supported **Social-Media Logins**
  * **Now Attacker Step starts =>**
    * Gather Victim's Email + Use that email by registering account using One of Social Media Accounts [i.e. Google] [Attacker using Gmail Account to login]
    * Application will successfully Log In  upon registration process completion, and all the features of the applications are accessible.
    * Log Out  => Now go to Application's Login Functionality
  * **Now Victim's Step** =>
    * This time, use **Google Authentication** and login to the application using the same Email address
    * Observe that the login is successful and the victim user can access the application.
    * Then, perform any changes in the application, such as profile update.
  * **Now again Attacker's Step =>**
    * Now, In a separate browser window, attempt to log in using the `Email:Password` used for registration
    * Observe that the attacker is successfully logged in to the victim user’s account and can see all the changes that the victim performed.
    * This allows an attacker to keep persistence access in the victim user’s account as long as the victim manually changes the account’s password.
* **Note:** If the victim already has an account using social login on the application, this attack will most likely not work.



> From Twitter Threads =>
>
> Assume that...
>
> company 's name is xyz  
> And victims name is : sam (he the employ of company) ... 
> Email of sam will be: sam@xyz.com ....
>
> Now the attacker will make new account using sam's email id and adding a random password.and he is logged in. Now attacker will log out.
>
> Now victim will log in using google authentication ( not the default method,that  attacker used). He will use company email in google auth verification. He will be logged in and update his profile. now attacker will login using default steps and get info of  profile of employees.



> ### **Takeaways**



- Always look for possible ways to bypass the email verification, especially when the social login options are present.
- Always attempt to chain the vulnerabilities together to increase the impact.
- Be observant and approach an application after understanding its logic.



---



### 1.2 SSRF to XSS -750$ Story

Link => https://aashishandaashish.medium.com/ssrf-to-xss-750-story-b12967286507



> ### Key Points =>

* Found a subdomain => which was Using JIRA Instance
* Checked Version =>  5.8.X [Using wappalyzer]
  * Vulnerable to SSRF
  * Good Writeup => https://infosecwriteups.com/piercing-the-veil-server-side-request-forgery-to-niprnet-access-c358fd5e249a
* Endpoint => **plugins/servlet/oauth/users/icon-uri?consumerUri=http://google.com**
* Replace **http://google.com** with **http://brutelogic.com.br/poc.svg**
  * Result => XSS



Short and Sweet

---

### 1.3 Admin Panel? Pwned!

Link : https://splint3rsec.medium.com/admin-panel-pwned-89db333f3836



> Really Very Good Writeup worth to note here 
>
> ### Key Points =>



* Did Subdomain Enumeration =>
  * **Assetfinder + subfinder → httpx with title, status code and content length**
  * Got 60 alive subdomains
  * Good Advice -> Instead of taking Screenshot => 
    * Do **the title and status code plus the content length** are more than enough
* Got **301 redirect Status** => **dashboard.subdomain.com**
* Checked and got => Admin Login Page
* Tried =>
  * Default Credentials
  * looking for hidden unsanitized parameters (XSS)
  * SQL Injection
  * None worked
* Now checked the **Source Code**
  * Found a JS File => **login.js**
  * There Mistakenly Developer put login creds 
  * That's It :smile:
* **Key Takeways =>**
  * Don’t miss reading the source code and especially javascript files, you may get credentials, API keys or even sensitive hidden endpoints… Just keep looking and open your eyes!



---



## 2. Tweety Tweets =>



### 2.1 Tweets 1

Link : https://twitter.com/adamtlangley/status/1403601806647832577



> I was today years old when I learnt you could pipe lists into ffuf instead of just specifying a file. 
>
> For example, if you wanted to test a bunch of id numbers against an endpoint ( think IDOR ) then you could do 
>
> **"seq 1 - 1000 | ffuf -w - -u [https://targetdomain.com/user/FUZZ](https://t.co/Kvjdoy9mlS?amp=1)"** 



Really Nice Trick for IDORs

---



### 2.2 Tweets 2



> Want to Learn Javascript ?
>
> Here is the Thread Link => https://twitter.com/jesss_codes/status/1402990850032820234



---

## 3. Notion Notes - My XSS Diary =>



> Link => https://www.notion.so/My-XSS-Diary-87b8f401d5514ef4812fcc41755040ea
>
>
> I am Learning XSS from brutelogic blogs and I will keep updated my Notion Notes of this.



