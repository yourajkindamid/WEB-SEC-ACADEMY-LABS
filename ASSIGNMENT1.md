# PORTSWIGGER WEB SECURITY ACADEMY
# Access Control Vulnerabilities and Privilege Escalation

## Concept (LAB 1 - 2)
- The first lab regarding access control vulnerabilites is based on **Vertical Privilege Escalation**.
- Access control is defined as restrictions on who or what is allowed to access resources or functionality on a site. **Vertical Privilege Escalation** is a type of an access control vulnerability.
- In this vulnerability, a user can access functionality on a web application for which they are not granted access to by the admin.
  
### LAB 1: Unprotected Admin Functionality
### Solution:
- A link to a shopping website is provided. The goal is to access the user list through the unprotected admin panel and delete the user ```carlos```.
- To solve this lab, modify the site URL by adding ```/robots.txt```. Unprotected websites usually keep sensitive data within their servers in files named as such.

<img src = "screenshots/lab1p1.png" height = "400" width = "750">

- Within this file, we find the URL to the administrative interface ```/administrator-panel```.
- Modify the URL once again by adding the newly found URL and the administrator interface can be accessed. The user ```carlos``` can now be deleted easily.

<img src = "screenshots/lab1p2.png" height = "400" width = "750">

- The solution of this lab was based on unhindered access to both the files in the server and to the administration interface.

### LAB 2: Unprotected Admin Functionality With Unpredictable URL
### Solution:
- To solve this lab, inspect the elements on this website to find the JavaScript snippet that acts as the authenticator for the administration interface.
- Within the 'Elements' tab in 'Developer Tools' follow the following pattern when checking different elements:
  1. ```<div theme> ... </div>```
  2. ```<section class = "maincontainer"> ... </section>```
  3.  ```<div class="container is-page> ... </div>```
  4. ```<header class="navigation-header> ... </header>```
  5. ```<section class = "top-links"> ... </section>```
  6. ```<script> ... </script>```
   
  <img src="screenshots/lab2p1.png" height = "700" width = "600">

- Within the Javascript snippet, search for the attribute to be added to the URL in case of an admin signing in to their account.
  ```js 
  adminPanelTag.setAttribute('href', '/admin-4ihrin');
  ```
- Copy the attribute and add to the URL which will grant access to the administration interface.

  <img src = "screenshots/lab2p2.png" height = "400" width = "750">
