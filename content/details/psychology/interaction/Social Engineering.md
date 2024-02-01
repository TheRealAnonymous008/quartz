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

# Tools 
* [pipl.com](https://pipl.com) - gives information about a person and their social media. 
* [webmii.com](https://webmii.com) - helps see online visibility.
* [whois.com](http://www.whois.net) 
* [Maltego](https://www.maltego.com) - tool for data collection and investigation
* [SET](https://trustedsec.com/resources/tools/the-social-engineer-toolkit-set) - Social Engineer's Toolkit 
* [Inteltechniques](https://inteltechniques.com/menu.html) - a collection of additional tools.

# Links 
* [[Social Engineering -- The Science of Human Hacking by Hadnagy]]
* [[Persuasion]]
* [[The 48 Laws of Power]]
* [[Communication]]

