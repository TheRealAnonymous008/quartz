* Establish Strong Pillars and then drill down to find the right level of specificity. This helps establish goals 
* The building blocks of the combat system are found in what the player can do. Options create depth and complexity. [[UX Design Principles#Tesler's Law|Tesler's Law]] applies.  The amount of options and complexity should be dependent on the target skill level (more skilled = more complex).

* The key to designing the system is through layers.  [[details/creativity/design/DOET/Design Thinking|Follow an iterative approach]].
	* A layered approach keeps scope low and allows for more organic growth. 
	* Layered systems lend themselves nicely to providing deeper combat without necessitating more complex development simply through emergent interactions.
* Be mindful of camera-genre expectations. *Closer camera = Higher Fidelity. Farther Camera = More macro view*. 
	* Note that if the camera is close to the player, make sure the camera does not get in the way of combat (i.e., snapping into awkward places)
	* Closer camera = More interactivity = More scope 

* *Enemies should feel interactive*. They should acknowledge the player's actions and react accordingly. 
	* Establish a [[Finite Automata and Regular Languages|State machine]] for the enemy's state to prototype interactivity. 
	* Consider if the player can interrupt the enemy's state -- how does the enemy recover? Is stunlocking possible?  *Recovery time is driven by the speed of the combat. Faster combat = faster recovery*.
	* How does the enemy game state vary with challenge and progression

* *Make combat feel nice*
	* Consider responsiveness for more snappy combat. Note that some of these principles can be broken as long as the intent of the system is met. 
		* Input response time
		* Input latency
		* Animation blend times. They should be fast and high fidelity
		* Movement that has high acceleration feels more uncontrollable.
		* For attack interruptions, favor the player's input to make them feel more in control. 
		* Attacks should  have some translation. This makes them feel more dynamic and less static. It is also helpful for animation blending. This is a double edged sword, however, since this may not match player intention. 
		* Enemies should be telegraphed. *Telegraphing doesn't mean having a long wind up, but a readable one*. It would be unfair if the player were hit by something that they could not have read or anticipated. 
			* Use clear poses 
			* Use strong anticipation. More difficult combat can exploit this by messing with the timings of the attack. 
			* Sound cues 
			* Visual effects 
			* Proper hierarchy. Indicate which attacks are the most immediate danger for the player. 
			* Bake in the recovery time of the enemy animation to make it more intuitive.  
	* Consider the principles of [[Animation|animation]] and sound effects to enhance the feel of the combat. 
		* Anticipation and Follow through sell the weight of the attack. 
		* Having an object only "move one way" will feel stiff. Make it lively with secondary action.
		* Slow in and Slow out. 
		* Exaggerate.
		* Use strong poses, especially for fast combat.  
		* An instant reaction (at low fidelity) works better to make the combat feel weighty .
		* *Hit reactions sell strength*.
		* *Variety sells interactivity

	* Cheat for the player to easily map intention to action. 
		* Have aim assist. Helps especially if it is configurable.
		* The character should be "magnetic" when attacking. They translate towards the enemy when attacking. Do not make this too extreme, however if the combat is positioning heavy. 
		* Have generous input windows to give the player some leeway for chaining attacks. However, do not overdo this. Have measures to counter button mashing (i.e., combat without intent)
		* Have fair hitboxes. 

	* Some additive elements to elevate combat feel. Note that it is important to not overdo these as they will have the opposite effect.  Also allow for the player to personalize these 
		* Hit flash 
		* Hit reaction 
		* Visual Sound effects 
		* Hit stop or Time dilation  (action freezes for a moment when an attack hits). 
		* Damage Numbers 
		* Screen shake 
		* Procedural Enemy Shake 
# Links 
* [Dreamsccaper -- Killer Combat on an Indie Budget](https://www.youtube.com/watch?v=3Omb5exWpd4)
* [What Makes a Good Combat System](https://www.youtube.com/watch?v=8X4fx-YncqA) 
* [How Do You Improve Turn Based Combat](https://www.youtube.com/watch?v=ktogjiX3eI4) 

* [[Lenses for Game Design - Notes]]
* [[Games as Rules]] - combat systems are part of the rules. 