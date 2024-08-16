* In general, data should follow **CIA**
	* **Confidentiality** - data is kept secret from those who are not authorized to view it.
	* **Integrity** - data is not modified by unauthorized people or by accident.
	* **Availability** - data is available when you need it 

* To make sure that data is CIA, we should have AAA in our application
	* **Authentication** - the user must present information about *who they are* (i.e., username and password.) This comes in three forms
		* Something you know (password, PIN)
		* Something you have (RSA tokens, Certificate keys)
		* Something you are (Biometrics)
	* **Authorization** - the user is *granted only certain privileges* to access certain areas of the system. These permissions should be stored in a database with the user's identity and are granted by a system administrator.
	* **Audit Trail** - *log user activity* while users are logged in to the system and stored in a secure location. This allows actions to be traceable.

* *There is no such thing as zero risk only acceptable levels of risk*. 
# General Principles
* Minimize attack surface area.
* *Secure defaults* - the default option is the most secure option.
* **Principle of Least Privilege** - a user or entity should only have access to specific data, resources and applications needed to complete a required task. [^1]

[^1]: Analogous to [[SOLID Design Principles|The Interface Segregation Principle]]. 

* **Principle of [[Military Strategy|defense in depth]]** - leverage multiple security measures to protect assets.

* **Fail Securely** - handle errors securely. In general, design the security mechanism so that failure  follows the same execution path as disallowing the operation.

* External systems are insecure.
* Separation of duties.
* Security through obscurity is not security
* Simplicity
* Fix issues correctly 
* An unsecure business policy gives unsecure code no matter how much one adheres to secure coding practices.

# Threat Modeling
* Manual code inspection is flexible but is time consuming to perform. It focuses on analyzing existing artifacts and allows one to inspect the vulnerabilities in code.
* Penetration testing means to test the security of an application without knowledge of its working.
* A threat model allows one to capture the security risks in an application and to make informed and rational security decisions.
	* What are the assets that may be under attack. How valuable are these for the organization
	* Who might be able to attack the application
	* What countermeasures exist.
	* What vulnerabilities exist 
	* Reduce threat by identifying new countermeasures.
	* Document threats

* *Focus on likely and high impact threats*. 
* The **DREAD** model allows for one such approach for scoring threats.
	* *Damage Potential* - how much damage will it cause
	* *Reproducibility* - how easy is it to reproduce the threat
	* *Exploitability* -  how much work is it to launch the attack
	* *Affected Users* - how many users will be affected
	* *Discoverability* - how easy will it be to discover the threat

* The **STRIDE** model allows us to determine what threats may exist in a system.
	* *Spoofing* - pretending to be something other than yourself. Violation of Authenticity
	* *Tampering* - modifying something in the system. Violation of Integrity
	* *Repudiation* - claiming you didn't do something or were not responsible for. Violation of Accounting / Audit trails
	* *Information Disclosure* - obtaining information someone is not authorized to access. Violation of Confidentiality
	* *Denial of Service* - exhausting resources needed to provide service. Violation of Availability
	* *Elevation of Privilege* - allowing someone to do something they are not authorized to do.

# Topics
* [[Hacking]]

# Links
* [[Database]]
* [[Software Engineering]] - security should be a concern in the software development lifecycle.