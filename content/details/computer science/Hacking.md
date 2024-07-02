# Brute Force Attack
* A **Brute Force Attack** involves using trial and error to crack a password. Here, the hacker *tries multiple combinations until they find the correct one*

* **Simple brute force attacks** may be done manually without any software. Typically it helps if the hacker manages to do [[Social Engineering]] and assess their target first.
* A **dictionary attack** involves testing possible passwords by using a predefined dictionary of commonly used words, phrases and number  combinations 
* A **hybrid brute force attack** combines a simple brute force with a dictionary attack.  The attacker starts with a list of potential words and then experiments with character combinations to find the correct passwords.
* A **reverse brute force attack** is where the hacker begins with a password (either known or guessed) and then tries it with every possible combination of users. 
* **Credential Stuffing** involves collecting username and password combinations which are then tested on other sites. This relies on users using the same password across multiple sites.

## Countermeasures
* Lock accounts after a certain number of login attempts.
	* Note that this can backfire and cause a DOS instead if the user exists.
	* If the user doesn't exist, the fact that a response is sent means there is a user and the hacker knows that
	* It does not prevent hackers from bypassing this (longer fuzzing intervals or getting lucky)
* Block IPs
	* This may lead to blocking out a large group of users.
	* It can be circumvented with proxy IPs. 
* Block devices.
* Enforce secure passwords. This does not prevent a brute force attack but it does mean the hacker takes longer. 
* CAPTCHA
* Fool automated tools by making use of inconsistent response codes or variable login delay.

# Command Injection
* A **command injection** is an attack that aims to execute arbitrary commands on the host [[Operating System]] via a vulnerable application. Typically, the payload is executed with the privileges of the vulnerable application. 
* It occurs when 
	* Data enters the application from an untrusted source.
	* The data is part of a string that is executed as a command by the application.
	* By executing the command, the application gives an attacker a privilege or capability that the attacker would not otherwise have.

## Countermeasures
* If possible, use library calls rather than external processes to recreate the desired functionality.
* If possible, ensure that all external commands called from the program are statically created.
* Prefer passing arguments to the program rather than using standard input CLI. Prefer parameterizing and separating data from code.
* Proper input validation. Accept known good.
* The application should only be allowed to use certain commands.
* Assign permissions that prevent the user from accessing privileged files.
* Run code in a sandbox environment to restrict which files the process can discover. 
* For any data that will be used to generate a command to be executed, keep as much of that data out of external control as possible.

# Cross Site Request Forgery
* A **Cross Site Request Forgery (CSRF)**  (aka session riding) is an attack which forces an end user to execute unwanted actions on a web application in which they're currently authenticated. Essentially, the authenticated user is tricked by the hacker into performing a malicious action.
* CSRFs target functionality that causes a state change to the server. 

* A variant of this is **Login CSRF** wherein the hacker forces the non-authenticated user to log in to an account they control. Because of this, the hacker can access user data. 
* CSRF can be **stored** in the website (i.e., using an images or iframes for fields that accept [[HTML]])
## False Countermeasures
* *Using secret cookies*. Cookies are always submitted on request (whether the victim intended it or not) The session identifier does not verify that the end-user intended to submit the request.
* *Using only POST requests*. An attacker can still intercept POST requests and forge them.
* *Multistep Transactions*. An attacker only needs to know the whole process.
* *URL Rewriting*. Exposing the session ID is a security flaw.
* *HTTPS*. HTTPS does not defend against CSRF.
* *Using a referrer header*. The referrer header can be spoofed or affected by browser settings.
## Countermeasures
* Prevent any form of [[#Cross-Site Scripting]].
* Add **CSRF tokens** to all state changing requests. The CSRF tokens are to be validated on the backend.
	* CSRF tokens are generated server side per session or per request.
	* Per request CSRF tokens are more secure but less user friendly .
	* A request is only accepted if the client has the correct token. 
	* The token only lasts at most until the session expires. 
	* The token is unique per user session.
	* The token is secret and generated securely .
	* The CSRF token must  not be transmitted in a cookie.
* Use the **double cookie submit pattern**
	* Ensure that there is a session dependent value that changes with each login session.
	* The value is transmitted via a signed cookie.

# File Upload Exploits
* An attack can be done using **Polyglot Files**. These files are valid forms of multiple different file types (i.e., JPEG and PHP). These can be used to bypass any checks of files and inject a malicious payload on the server. 
* **File Bombing** can be done by uploading large files to fill up server storage and reduce availability.
* Files can become vectors for XSS or CSRF attacks.
* Executable **reverse shells** can also be uploaded as a backdoor to access the server. 
* A DoS can be done by requesting many files. This can be done with a few requests.
* The server might be used to upload illegal files.
* Information disclosure through error messages. This can be done via:
	* Uploading a file with a long name
	* Uploading a file multiple times at the same time.
	* Uploading a file with reserved or forbidden names
	* Uploading a file with illegal characters 
## Countermeasures
* Only allow safe and critical extensions
	* Checking file extensions is not enough because we can bypass these by renaming the file extensions
* Validate the file type. Do not rely on content-type headers which can be spoofed.
	* Images can be subject to image rewriting techniques. 
	* Documents can be used using Apache POI
	* Zip files are not recommended because of Zip bombing. 
* Validate the file signature as a first step. However, do not rely on this as this can also be bypassed.
* Change the filename to something generated by the application. Filenames might be special or restricted filenames or use illegal characters.
* Set a filename length limit.
* Set a file size limit
* Only authorized users can upload files.
* Store files in a secure area.
	* Store files in a different host.
	* Store files where only admin access is allowed. 
	* Store files inside the webroot and set them in write permission only. 
* Run files through an antivirus or sandbox to validate that the file does not contain malicious data 


# File Inclusion
* A  **file inclusion** vulnerability allows an attacker to include a file which will allow for access of the contents of the file. This can lead to
	* Denial of Service
	* [[#Cross-Site Scripting]]
	* Sensitive Information Disclosure
	* [[#Command Injection]]
* File Inclusion happens when filenames are accepted as parameters and these are not properly sanitized.
* **Null Byte Injection** involves using a null byte which will ignore any characters after the null byte. 
## Countermeasures
* Input Validation. Sanitization
* Avoid passing user submitted input to any filesystem. 
* Maintain an allow list of files so that we can reject invalid files.

# Insecure CAPTCHA
* This exploit involves bypassing CAPTCHA to allow for automated attacks.
* This is due to bad design or implementation of the CAPTCHA mechanism.
## Countermeasures 
* Ensure that CAPTCHA responses are at the server level rather than at the client level.
* CAPTCHAs must not be readable by an OCR.

# SQL Injection
* An **SQL Injection** involves the injection of an [[Database|SQL Query]] via input data from the client side. 
* When successful, it allows
	* Modifying or tampering with data within the database
	* Repudiation (i.e., voiding transactions)
	* Data Unavailability
	* Information Disclosure
	* Authorization bypass (attackers make themselves admins)
	* Authentication bypass

* A **Blind SQL Injection** is a variation that asks the database true or false question. This is used if generic error messages are prevented but not regular SQL injections.
	* Simple tests based on querying content may be used to probe for SQL injection vulnerabilities
	* We can also use timing. Here, we structure the query to pause for an amount of time, and from there we deduce the structure of the database. 
	* Other tests can be used to determine the RDBMS.
## Countermeasures
* Stop writing dynamic queries via string concatenation
	* Use prepared statements with parameterized queries. **Prepared statements** separate data from code (and are more readable).
	* Use **stored procedures** assuming the stored procedures are implemented safely -- parameters must be parameterized. However, they may be compromised if the attacker bypasses the authorization. 
	* Allow-list input validation
* Disallow SQL inputs via input validation (not recommended although input validation should always be done)
* Minimize the privileges assigned to every database account in the environment.

# Weak Session IDs
* Once an authenticated session is established, the session token is equivalent to the strongest authentication method used by the application. 
* *Disclosure of the session ID will lead to session hijacking*, where a hacker can impersonate an authenticated user.
* Weak session IDs increase the chance of disclosure or fixation.
## Countermeasures
* The name associated with the session ID should not be extremely descriptive (i.e., do not use `PHPSESSID` or `JSESSIONID`). This might reveal the framework used.
* The session ID length must be long enough to prevent a [[#Brute Force Attack]]. The session ID length must be at least 16 bytes.
* The session ID should be unpredictable enough. Use CSPRNG with at least 64 bits of [[Information Theory|entropy]]
* The session ID content must be meaningless. Do not use user information in making the session ID to prevent information disclosure
* Use cookies for session ID exchange. Couple this with encrypted HTTPS and using the `Secure`, `HttpOnly`, and `SameSite`cookie attributes.
# Cross-Site Scripting 
* A **Cross-Site Scripting (XSS)** attack is an injection where malicious scripts are injected into a trusted website and sent to an unsuspecting user. 
* A **DOM-Based XSS** involves the attack payload being executed as a result of modifying the DOM environment. The page doesn't change but the client side code contained in the page executes differently.
	* One way to do this is to modify the URL by injecting the code there (i.e., using `?` or `#`). 
* A **Reflected XSS** occurs when the injected script is reflected off the web server (i.e., via an error message). The injected code travels to the web site which reflects the attack back to the user's browser
	* It is carried out through a single request / response cycle.
* A **Stored XSS** occurs when the user input is stored in the target server and then the victim retrieves the data. The data is not safe to render in the browser. 

* XSS can be used for content spoofing or for other vulnerabilities (i.e., [[#Cross Site Request Forgery]]). 

## False Countermeasures
* Relying on CSP headers. These can be [[#CSP Bypass|bypassed]]. 
* Using interceptors naively.
	* Improper encoding that can still allow exploitable XSS in some URI paths of your application
	* The application can result in incorrect or double encoding
	* It does not counter DOM-based XSS
	* They are not effective when data comes from responses originates outside the application
## Countermeasures
* When using a framework, understand the extent to which it prevents XSS.
* Sanitize all input variables for XSS 
* Use **output encoding** -- variables are interpreted as text instead of code when rendering. It is not a complete solution, be aware of dangerous contexts which may have XSS issues even with output encoding.
	* Convert `&` to `&amp;`
	* Convert `<` to `&lt;` and `>` and `&gt;`
	* Convert `"` to `&quot;`
	* Convert `'` to `&#x27`
	* Use the standard percent encoding for URLs
	* For Javascript, encode all characters to `\uXXXX`
* Use **HTML sanitization** to clean the HTML. Sanitize after modifying the HTML
# CSP Bypass
* **Content Security-Policy** headers allow the browser to protect the user from dynamic calls that will load content into the page currently being visited
* CSP can be used to protect against XSS. It acts as a secondary layer of defense.
* CSP can be delivered in three ways
	* Sending a `Content-Security-Policy` HTTP response header from the server on all HTTP response
	* Use `Content-Security-Policy-Report-Only` to deliver CSP that doesn't get enforced. 
	* Use a `Content-Security-Policy` meta tag when the headers are out of one's control.
* CSP can be implemented in two ways
	* Nonce based uses one-time-use random variables for each HTTP response.
		* The nonce should be generated per response with a CSPRNG 
		* The nonce should not be generated by middleware replacing all `<script>` with `<script nonce=>`. 
	* Hash-based. This will allow only specific scripts to execute.
# Javascript-Based Attacks
* A **Javascript Injection** involves the ability to inject arbitrary JavaScript code inside the victim's browser. 
* Like with [[#Cross-Site Scripting]], it can be used for information disclosure, impersonation, or modifying page content.
# Authorization Bypass
* An **Authorization Bypass** is any place in the application that allows access for an unauthorized user.  There are two variants of this
	* **Horizontal** - accessing the data of another account at the same level of privilege
	* **Vertical** - escalating the level of privilege
* **Insecure Direct Object References** are one such vulnerability where one can easily access another account simply by modifying the identifiers used in a URL or its parameters. 
* **Force Browsing** involves forcing the browser to visit a page you do not have access to. An unsecure application would show the page and potentially its contents. 
## Countermeasures 
* Avoid exposing identifiers in URLs and POST bodies if possible. Always determine the authenticated user from session information.
* Use random identifiers for your database tables.
* Always verify user permission for any request made. 
# Open HTTP redirect
* **HTTP redirects** involve the web application accepting untrusted input that could cause the web application to redirect to a URL contained within the untrusted input. 
* This attack is used to launch other attacks (i.e., phishing or identity theft). 

## Countermeasures
* Avoid using redirects and forwards if possible.
* If used, do not allow the URL as user input for the destination.
* When possible, have the user provide a short name that is mapped to the server-side to the full target URL. 
	* This prevents tampering with the URL.
	* But it may also be bypassed by the user cycling through IDs.
* Ensure the supplied value is valid, appropriate for the application and authorized for the users.
* Sanitize inputs for URLs based on an allow-list approach.
* Force all redirects to first go through a page notifying users that they are going off of your site, with the destination clearly displayed, and have them click a link to confirm.
# Links
* [DVWA Ultimate Guide - First Steps and Walkthrough](https://bughacking.com/dvwa-ultimate-guide-first-steps-and-walkthrough/#Insecure_CAPTCHA)
* [Fortinet](https://www.fortinet.com/resources/cyberglossary/types-of-cyber-attacks)
* [The Hacker Recipes](https://www.thehacker.recipes)
* [OWASP](https://owasp.org)
