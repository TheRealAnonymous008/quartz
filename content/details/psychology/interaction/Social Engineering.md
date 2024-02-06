* Social engineering takes the way humans are wired to make decisions and exploits the vulnerabilities in those processes. 
* The goal is to have someone make a decision without [[Thinking Fast And Slow|thinking]] and to act in a way that is not in their best interests.  
	* *Thinking is the enemy of the social engineer*. 
	* Heightened emotional reactions and intimate moments that cause the subject's brain to release dopamine and oxytocin help. 

# The SE Pyramid 
## Open Source Intelligence (OSINT)
* **OSINT** is the life blood of social engineering pertaining to *relevant information about the target*. 
* The key is to combine both nontechnical and technical OSINT to uncover information about the target. 
* *It is recommended to document findings to keep everything organized*.

* *Caveat: Remember that just because you can see "what" doesn't mean you can automatically know "why"*. The connection between the two can only be established through further observation and more information.

### Non-Technical OSINT 
* This is anything that does not involve direct interaction with a computer. This is usually where social engineering starts. 
* *The vast majority of non-technical OSINT skills constitutes **observational skills***. Observe the environment, Gather Information and use this information as the situation arises. 
* Observing allows us to both spot opportunities (vulnerabilities) in the environment, and to gather seemingly trivial information that can give us access to more secure information 
* *Be detail-oriented and observe everything*. Not only can this make for a good cover in the context of OSINT gathering, but if the target can catch onto missing or suspicious details, then your cover will be blown.  *The little details (especially that which the target can catch) matter*

* *Practice*: Remember details of the people around you. Begin with simple details and scale up in complexity to formulating a crude profile of the person(s) 

### Technical OSINT 
* Information can come from a variety of sources
	* Social media - a profile of the target can be built just from this.
		* *Caveat: Online personalities != Real personality. What is online is how a person wants to be viewed online*
	* Search engines - the Internet holds secrets for those who know how to ask
		* *Information about the target's family* is good as well. They offer good attack vectors. 
		* Especially look at indexed and cached web pages .
		* Use search operators to minimize search 
		* Look at images of the target if possible 
	* RSA Keys - we can search using the query 
	```
	BEGIN (CERTIFICATE|DSA|RSA) filetype:key
	```
	* Webcam information 
	* Misconfigured directories and robot.txt files can give additional information -- look at what files in the robot.txt are "disallowed". 
	* Metadata - both text and from EXIF data in images. 

## Pretext Development
* **Pretext Development** - develop a pretext based on OSINT. The pretext means that you *become anyone you want to be; presenting yourself as someone else to obtain information*.   
* The point is that there is no such thing as one pretext that fits all situations
* Method acting and Improv helps in this regard.

* Keep in mind the following principles
	* *Think through your goals*.. Use the results from OSINT to develop the pretext, but more importantly understand the goal that the pretext aims to achieve 

	* *Understand Reality vs Fiction*. It is easier to remember the pretext if it is based in reality and one can use their experience or knowledge . Keep the pretext realistic for the target so that they are not suspicious. *Do not pretend to have knowledge that you don't., especially when the other person has this.*

	* *Know how far to go*. You do not have to create a [[Lenses for the Experience#The Look and Feel of a World is Defined by Its Aesthetics|detailed backstory]]. People will only care about what they have to in order to complete the social contract you have created.  

	* *Avoid short term memory loss*. Use a few techniques to remember important details 
		* Have being able to write things down as part of the pretext 
		* Use business cards (after establishing rapport) 
		* Use recording devices 
		* Have a partner

	* *Get support for pretexting*. Play the part convincingly. The little details will help support the pretext.

	* *Execution of the pretext*. Be prepared to adapt on the fly. Practice. Stay Calm. Communicate with the right people at the right time. Do not use a script. 

* The pretext serves as the bridge between [[Communication#Framing|your frame]] and your target's frame. 

## Attack Plan, Attack Launch, and Reporting
* **Attack Plan** 
	* What is the plan? 
	* What is the goal? 
	* What is the best time to launch the attack? 
	* Who needs to be available at a moment's notice for support or assistance 
* **Attack Launch** - use an outline rather than a [[Narrative|script]]. 
* **Reporting** - report what went well or poorly in the attack. 

* Some attack vectors to consider
	* **Phishing** - use malicious emails that pretend to be reputable sources with the goal of 
		* Delivering malicious payloads that give remote access 
		* Gathering credentials 
		* Gathering further intel. 
	* **Educational Phishing** - use curiosity, greed, happiness or fear to get people to click. Tailor the phishing to these aspects of the client. The goal is to be geared towards informing vulnerabilities 
	* **Pentest Phishing** -  use fear, greed, surprise or sadness. The goal is not just a click but remote access
	* **Spear Phishing** - a personalized form of phishing that considers the target's personal information
	* **Vishing** - phishing over the phone. Usually used for 
		* Harvesting credentials to gain access.
		* OSINT, particularly to verify details. 
		* Full compromise. 
	* **SMiShing** - using SMS messaging, typically geared towards loading malware on the device or stealing credentials. 
		* The key is brevity. Just facts and links 
		* Leave domains that look similar to the attack. 
		* Make sure the link leads to a believable website. 
		* Make the procedure of gathering information simple -- do not make the user perform many actions. 
	* **Impersonation** - most dangerous and also riskiest.  This requires proper planning 
		* Gather information about the site and to develop a plausible pretext. 
		* Develop your pretext before you attack. 
		* Understand the goals of the attack from start to finish. 
		* Ensure all necessary equipment are on hand. 
		* Make sure to have a get out of jail free card. 

## Mitigation and Prevention Plan 
* At the end of the day, the goal of pentesting and social engineering (for good) is to develop actionable mitigation and prevention plans to improve infrastructure security. 

* *Step 1: Learn to Identify Social Engineering Attacks*. Understand what actual attacks might look like and what they can do to the institution. Social engineering helps teach both how to recognize and take a hit. 

* *Step 2: Develop Actionable and Realistic Policies*. 
	* The plan should require minimal thinking from the client. Too many policies are broad and general that they leave too much thinking to the client rather than the expert. 
	* Remove the ability for empathy bypasses. Suggest policies for employees to help others without compromising company security. 
	* Make the policy as detailed as possible. A realistic policy is one which helps the employee see the situation rom all angles. It should be unambiguous and give a clear direction on what to take. 
	* Good policies explain both what and why. 
	* Good policies train the employees to react with muscle memory. 

* *Step 3: Perform Regular Real-World Checkups*. Check how well the policy stuck by using a test. 

* *Step 4: Implement Applicable Security-Awareness Programs* By making security-awareness programs applicable to your client’s specific needs, you can help their employees learn not only what not to do, but also what they should do when and if something bad happens
# Considerations
* *Leave them better off for having met you* 
	* If things are not panning out, back off. 
	* Use pretexts that do not have long-lasting negative emotional effects on the target
* As a professional social engineer, you are influencing or manipulating the emotional content of your target
* Do not underestimate how easy people can fall for human hacking. 

* Considerations for pentesting
	* What do you record? 
	* The client should be aware of each step of the pentest. 
	* Obtain written permission. 
	* Consider the [[Data Analytics|data story]]
	* Don't share successful exploits on social media.

* *Document everything*. Even things that are not used in OSINT and even sensitive information that, while not used in the pentest, may be of interest for the client's safety
	* Be professional, the report will be read by many people. 
	* Grammar and spelling checks. 
	* Be detailed. The client will appreciate your knowledge. Give them enough details to know what to do next. 
	* Suggest ways to mitigate vulnerabilities. These suggestions should be actionable. 
* *Be judicious with Pretext* 
* The right emotional trigger at the right time to the right people leads to massive success.
# Tools 
* [pipl.com](https://pipl.com) - gives information about a person and their social media. 
* [webmii.com](https://webmii.com) - helps see online visibility.
* [whois.com](http://www.whois.net) 
* [Maltego](https://www.maltego.com) - tool for data collection and investigation
* [SET](https://trustedsec.com/resources/tools/the-social-engineer-toolkit-set) - Social Engineer's Toolkit 
* [Inteltechniques](https://inteltechniques.com/menu.html) - a collection of additional tools.

# Links 
* [[Social Engineering -- The Science of Human Hacking by Hadnagy]]
	* Ch. 9 further details techniques on Social Engineering 
* [[Persuasion]]
* [[The 48 Laws of Power]]
* [[Communication]]

