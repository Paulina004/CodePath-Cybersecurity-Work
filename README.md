# Pen Testing Live Targets

Time spent: **8** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each color is vulnerable to only 2 of the 6 possible exploits. First discover which color has the specific vulnerability, then write a short description of how to exploit it, and finally demonstrate it using screenshots compiled into a GIF.

## Blue

### Vulnerability #1
Session Hijacking/Fixation

### Description
The blue site has a vulnerability that can be targeted by session hijacking or session fixation. Here, session hijacking is displayed. First, log in to the staff account (this is done using the username “pperson” and its associated password) on one browser, which in this case was Firefox. On the Firefox browser with the blue site open, change the session ID by using this attachment to the end of the URL: "public/hacktools/change_session_id.php". On a different browser (in this case, Chrome), navigate to the blue site and change its session ID in the same way. Change the session ID to the same session ID of the logged in staff account from the Firefox browser. If you then attempt to log in on Chrome, you will be able to access the staff account. This is a very bad vulnerability to have for a system because an attacker can see anything in the staff area of the blue site. 

<img src="blue-vuln1.gif">



## Green

### Vulnerability #1

Username Enumeration

### Description
The green site has a username enumeration vulnerability. If you navigate to the “Login” tab and put a username that does not exist (along with a password), you will see that the login error message will be labeled under the class “failed”. However, if you put a username that does exist (“pperson” or “jmonroe99”, in our case), the login error message will be labeled under the class “failure”. The process of checking these classes is displayed in the GIF demo. This is a very careless mistake on the part of the developer because a hacker can easily see which usernames exist and which do not exist when they attempt to brute-force or use another type of technique to confirm valid users in the system.

<img src="green-vuln1.gif">


### Vulnerability #2
Cross-Site Scripting (XSS)

### Description
The green site has a cross-site scripting (XSS) vulnerability. This vulnerability is found when leaving feedback on the “Contact” tab. If a user enters a random email and feedback comment and then injects JavaScript into the name section of the form, a stored XSS attack can be achieved. When an admin logs into the staff admin area to look through the feedback given by customers, they will see the alert that the injected script shown in the GIF created. As you can see in the GIF, since other students also performed the same attack, there were multiple XSS alerts to click through, but the one performed on my computer was also there amongst the crowd. 

<img src="green-vuln2.gif">



## Red

### Vulnerability #1
Insecure Direct Object Reference (IDOR) 

### Description
The red site has a vulnerability that the other two websites (the green and blue sites) do not have. If you navigate to the “Find a Salesperson” area on any of the three sites and click on a person in the list, you will notice (as shown in the GIF) that the ID of the employee is located in the URL. For the green and blue sites, if you try to change the ID to that of an employee whose information should not be accessible, the site will simply kick you back to the “Find a Salesperson” main menu. However, if you try to perform the same test on the red site, you will see some sensitive employee information that should not be made publicly available. For example, if you change the ID to 10 (as shown in the GIF), you will see an employee named Testy McTesterson whose data should not be made available until September 1st. Another example is if you change the ID to 11 (as shown in the GIF); you will see an employee named Lazy Lazyman who was fired for stealing and who should not be accessible.

<img src="red-vuln1.gif">



## Notes

Describe any challenges encountered while doing the work.
- One challenge I had was with the 
