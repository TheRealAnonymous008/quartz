* At their core, [[The Fundamentals of Game Design|games should be unpredictable for them to be engaging]]. This can be achieved either using randomness, using the [[Game Theory|dynamic nature of player choice]], or through complex gameplay via its mechanics.
* The **mechanics** of a game pertain not just to the formal systems underlying it, but the mechanisms by which the game operates -- in other words, the specifics of how to code it. 
	* A **core mechanic** in this context means a mechanic that underlies a vast majority of the game's systems in some way
	* *The mechanics of a game can be implemented through many different media*. Hence, if it can be done on paper, [[Lenses for the Process|do so]].
	* There are five kinds of mechanics 
		* **Physics** - the [[Physics|science]] of motion, temporality, and force in the game world. 
		* **Internal Economy** - The mechanics of [[Economics|transactions]] involving game elements (both concrete and abstract resources) that are collected, consumed, and traded.
		* **Progression Mechanisms** - the mechanisms involved in [[Level Design Principles|level design]] that indicate how a player will progress through the game 
			* *Example*: Any new movement mechanic in a metroidvania. 
		* **Tactical Maneuvering** - mechanics involving the placement of game units on a map for offensive or defensive advantages. 
		* **Social Interaction** - [[Games as Play#Social Play|the mechanisms]] that allow players to interact with one another 
			* *Example*: Giving gifts.
	* Mechanics can also be discrete or continuous. 

![[Game Mechanics.png]]
<figcaption> Game Mechanics. Image taken from Adamss and Dormans</figcaption>

* It is important to distinguish the structural differences between mechanics of progression and emergence. *Games tend to have a mix of both*. 
  
| Structure                         | Emergence              | Progression                 |
| --------------------------------- | ---------------------- | --------------------------- |
| Number of Rules                   | Low                    | High                        |
| Number of Game Elements           | High                   | Low                         |
| Interactions between Elements     | High                   | Low                         |
| Possibility Space                 | Large and Wide         | Small and Deep              |
| Replay value                      | High                   | Low                         |
| Designer control of Game sequence | Low (due to emergence) | High (due to level design ) |
| Length                            | Tends to be short      | Tends to be long            |
| Learning curve                    | Steep                  | Gentle                      |

* *Mechanics don't have to be realistic, only consistent*.  Remember, all games have some form of recognizable patterns inside them and the mechanics should be one of these patterns 
# Mechanics 
## Physics
* Mechanics based on physics require understanding the underlying game  engine's physics simulation. 
* They usually cannot be (conveniently) prototyped via a board game, especially if they operate on a continuous space.
* Once players grasp the physics of a game, they can intuitively predict movements and results, but with less certainty. *Skill and dexterity become a more important aspect of the interaction*
* However, *physics also implicitly lends itself to discrete mechanics*. In particular, by allowing the players to formulate a strategy that can be described without knowledge of the underlying physical computations.
* *It is hard to innovate with physics mechanics*. 

## [[Game Economy]]

## Mechanics of Emergence 
* [[Complex Systems|Emergence]] allows designers to create games which offers more player opportunities. 
* *These make good use of the computer's ability to do many processes*. 
* Games may have breadth (many possible choices) or depth (many possible outcomes as a result of subsequent actions).
* *Even relatively simple mechanics gives many gameplay opportunities*. The emergent properties arise from the mechanics interacting with each other. 
	* These opportunities give rise to new player strategies. 
* They have a *high replay value* because the challenges and possible actions that occur while playing are different every time
* *Emergent gameplay mechanics should be a balance between ordered (progression) mechanics and randomness*.
* The structural qualities of the game -- the presence of feedback loops, interconnected parts, and differing scales of complexity, determine emergent gameplay. 

## Progression 
* A game of progression requires a large amount of data, prepared in advance by the designer, that the player can access at arbitrary points
* They offer many predesigned challenges that the designer has ordered sequentially via level design. 
* These are suited for games that tell [[Narrative|stories]]. 
* They also allow the designers to arrange the levels in such a way a tutorial would meaningfully explain the mechanics of the game without overwhelming the player. 
* One challenge is **railroading** where a player feels like they are guided through the game instead of making their own choices. *Balancing between offering and restricting freedom is necessary*
* They typically have many rules but they do not interact with each other as much.

## Randomness 
* Randomness has an impact on the game's balance. 
* The *impact* of randomness is related to the [[Random Variables and Probability Distributions|distribution]] of random numbers created. 
* Aim for random mechanics that operate frequently but have low impact. In the long run, the odds even out. 
* Randomness can be a useful strategy 
	* It can force players to improvise (assuming the playing field remains fair). The deciding factor becomes the ability to prepare and adapt. 
	* It can counter [[Static Games of Complete Information#Strict Dominance|dominant strategies]]. 

# Meaningful Mechanics 
* Remember that [[Games as Play#Play of Meaning|games are systems of meaning]] but also that [[The Fundamentals of Game Design|games are interactive by nature]]. Ergo, *a meaningful game is driven by meaningful mechanics*
* Games can subtly deliver messages simply through their mechanics. In essence, as if telling a [[Narrative]] but through the mechanistic rules the game world operates in. 
	* But crucially, *games demand players take an active role in realizing these messages*. Games do not teach directly; they teach through consequences.
	* There is a danger of the game being simplified as an optimization problem and its underlying message lost. Consider [[Players and Why We Play Games|the demographic]] and the [[Lenses for the Experience|experience of the game as a whole]]. 
* *The mechanics affect how a game is experienced*. 
* *Design mechanics around the most important aspect -- the essential experience of the game*

* As a game designer you should always be on the lookout to create systems where the number of meaningful combinations is large and possibly endless.
# Links 
* [[Game Mechanics -- Advanced Game Design by Adams and Dormans]]
	* Ch. 5-6 covers the Machination framework in detail. 
	* Ch. 9 - covers an example of designing an internal economy.

* [The Best and Most Stealable Mechanics from Tabletop RPGs by GDC](https://www.youtube.com/watch?v=6sXdCKd0XdE)
	* Video games can take inspiration from how TTRPGS are able to integrate gameplay and story.

* [[Games as Rules]]
* [[Lenses for the Game]]
* [[Models for Game Rules]]
* [[Game Balancing]]
* [[Tabletop Mechanics]]