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
* Proper input validation. Accept known good.
* The application should only be allowed to use certain commands.
* Assign permissions that prevent the user from accessing privileged files.

# Cross Site Request Forgery
* A **Cross Site Request Forgery (CSRF)** is an attack which forces an end user to execute unwanted actions on a web application in which they're currently authenticated. Essentially, the authenticated user is tricked by the hacker into performing a malicious action.
* CSRFs target functionality that causes a state change to the server. 

* A variant of this is **Login CSRF** wherein the hacker forces the non-authenticated user to log in to an account they control. Because of this, the hacker can access user data. 

# File Upload Exploits
* An attack can be done using **Polyglot Files**. These files are valid forms of multiple different file types (i.e., JPEG and PHP). These can be used to bypass any checks of files and inject a malicious payload on the server. 

# Links
* [DVWA Ultimate Guide - First Steps and Walkthrough](https://bughacking.com/dvwa-ultimate-guide-first-steps-and-walkthrough/#Insecure_CAPTCHA)
* [Fortinet](https://www.fortinet.com/resources/cyberglossary/types-of-cyber-attacks)
* [The Hacker Recipes](https://www.thehacker.recipes)
* [OWASP](https://owasp.org)
