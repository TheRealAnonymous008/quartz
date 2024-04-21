 
* Levels typically allow us to feature two things: *challenge* and *game space*.  Whether to begin on either challenge or game space depends.

* **Ideate-Design-Playtest-Iterate**. Map design is an [[details/creativity/design/DOET/Design Thinking|iterative process]]. The important thing is that it is designed with players in mind.
	* Take inspiration from existing maps or from a particular experience you want to capture. Take inspiration from real world [[Architecture|spaces]]
	* Make your maps fun to play so that they are fun to design and fun to playtest. Make map elements serve a fun purpose.
	* Maps are fun to play if they afford different opportunities for play and counterplay for the players,
	* Only by trying new things can you see how bad previous designs were. 

* [Level Design is about integrating the gameplay, the presentation, the story, and the emergent relations between them](https://www.youtube.com/watch?v=NO1lvc3ikXE) 
	* Presentation and Gameplay give rise to affordances and intentionality--how does the level convey what the player can do? How does it convey information and motivation to the player for them to make informed plans and decisions.
	* Presentation and Story give rise to [[Worldbuilding]]. How does the level contribute to establishing a unique, cohesive, and meaningful world? Is the worldbuilding ubiquitous in the level? Does it define the characters of the game? 
	* Gameplay and Story give rise to Interactive Narrative. Does the level tell the narrative through the strengths of the gaming medium? Does the level allow thee players to engage with and interact with the story? 

* Levels should [[Narrative|tell a story]]. They should convey something that is [[Game Mechanics Design]] or narratively interesting about the game's world or rules. In turn, levels support all other elements of the game. 

# Mechanics 
* The nature of the mechanics of a game may determine its level's lengths 
	* Games of emergence that require skill and strategy typically have short levels so that strategies can develop through many play sessions.
	* Games of progression typically have longer levels that are broken up into smaller sub-levels. 

## Progression 
* *The notion of progress is important to define*
	* **Task completion** - here progress equals the number of tasks completed. Optional tasks may also be performed for additional reward. Here, it is important to have *task variety* to keep engagement, as well as proper *pacing and [[Lenses for the Experience|challenge]]*.  Typically the tasks are *designed with the player's skill in mind*
	* **Distance to target** - here progress is measured as how close the player is to completion without explicitly specifying how the player should continue to progress. Here the player can *experience setbacks that can undo progress*.  Here tasks are *emergent and require the player to adapt*. 
	* **Character growth** - progress is measured through the character's additional strengths and abilities.  *Tends to be open-ended and offer branching paths*
	* **Player Growth** - progress is defined as the *player's own growth in skill*. Here the game trains the player on certain skills and progress is determined by player's execution. 

* *Levels should typically focus on different sets of mechanics from each other*.
	* The mechanics involved should not be trivial or repetitive. Offer a challenge. 
		* If the challenge comes from cognitive effort, the level should be slower paced. 
		* If the game requires little cognitive effort, the level should escalate in complexity and run quickly to make it more challenging. 
	* Additional subgoals that help in achieving the goal also help. 
		* Each subgoal should emphasize and integrate different mechanics as well
		* Subgoals may also be dependent on each other (lock and key approach).  However, do not rely on this too much to the point that the level becomes unintentionally linear. 
		* [[The Fundamentals of Game Design|More choices = Good]] for as long as the player is not overwhelmed. 
	* Consider *optional tasks*. When having these tasks, make sure they are not game-breaking enough to be a requirement
	* Consider *mutually exclusive tasks*. These happen when players have to choose between two alternative paths 
	* *Remember that a level is only as good as the weakest mechanics it uses*. 
	* Backtracking can be frustrating because of its repetitive, tedious nature. Either design it to be less frustrating or avoid it entirely. 

* *Levels facilitate the creation of game spaces*  A **lock and key approach** means that certain areas are locked off until the player complete certain objectives
	* Lock and key approaches control the progress in a level. 
	* *Prefer to have the player find the lock before the key*
		* If the player tends to find keys first before locks, they will collect everything, removing meaningful choice.  
		* The player will have a more active role as they realize the purpose of the key. It is especially good when the lock and the key are not obviously locks and keys 
		* The player will feel smart and have a sense of accomplishment. They may also recognize other similar locks that the key can now unlock which incentivizes them to backtrack and try the key. 
	* One possible approach is to have bonus objectives hidden behind "tough" locks. Especially good when the player sees these locks on their way to the key.
	* The key *can be a character skill* (or a combination of skills). Be careful to not have one skill be the key to many locks which may also open up unintended shortcuts. 
		* This is *typically static* which means that to add complexity, the designer must chain them together (or less ideally, add more mechanics).
	* The key *can be a consumable item* that vanishes on use. This forces the player to plan how to use the consumable, but it may also lead to a state where the player cannot progress. 
		* This *makes the lock and key more [[Internal Economy Design Patterns|dynamic]]* as the player has control of consumption (and even production) of the key. This also gives *more room for strategy* .
		* It allows for *easy difficulty tweaks* simply by controlling the feedback loops involved in the lock and key. 
	* The key *can be progress itself*. Here, the player must sacrifice level progression for something else (typically for long term benefit)
		* *Progress can be abstract* in that the player does not directly "make" progress but through a sequence of other actions, and through the use of many resources  they indirectly make progress. 

* When it comes to emergent gameplay, *we think in terms of phases and a more high level overview of general behaviors*.  
	* In many cases, we *use scripted events* to control the flow of the game. However, *mixing scripted with non-scripted events* also works to create a more dynamic experience .
	* Also consider *phase transitions* which imply a sudden shift in the balance of the game. Design patterns can be used to control how these phase transitions lead to the next gameplay phase. 
		* Slow cycles through phases are effective but lack subtlety and drama 
		* Infrequent but high impact bursts or deficits of resources also cause dramatic shifts. 
		* Passing a complexity threshold indicates a phase transition 
		* Stopping mechanisms which dampen the effects of actions due to repeated use will cause a subtle transition.

## Other Notes 
* *Levels should teach their mechanics*. 
	* One approach considers the [[The Psychology of Everyday Actions#Seven Stages Of Action|steps involved in executing a skill]] -- the player performs a physical *Action* which is then *Simulated* by the game. *Feedback* is then given to the player, who then updates their mental *Model*. Skills can depend on other skills to form a skill tree 
		* For onboarding the player, prefer a deeper tree to not overwhelm them with mechanics.  
		* Ideally, introduce the core mechanics of the game that the other mechanics put a spin on. 
		* Games that are *"easy to learn; hard to master"* are deeper more than wider. 
	* Another approach considers building mastery through gameplay. 
		* Here, difficulty is gradually increased, culminating in a test of the player's mastery of the mechanics (as expected of a certain skill level)
		* Challenges within the level also teach the player about the intricacies of the mechanic 
		* The "test" of the player's mastery must involve the mechanic. There must be no way to bypass this. 
	* In either approach, it *helps to chart out the dependencies and the general flow of the level*. 

* *Dramatic tension and gameplay tension are not the same thing*. Dramatic tension hinges on the story and the unraveling plot, while gameplay tension hinges on good level design and the player making progress .

# Links

* [Making of de_sparity by 3kliksphilip](https://www.youtube.com/watch?v=InmG615IgaA&list=PLfwtcDG7LpxG5QsLnW8FnuQXIVcIOOG0Y) - an example series for designing a map in Counter Strike.
* [Why Speed Level Design videos are so misleading](https://www.youtube.com/watch?v=IcCFto0u_g4) - Level Design is about the layout of the level in relation to how it will be played. Level Art is about the look and feel of the level.
* [GDC Talk: Holistic Level Design in Dishonored 2 and Immersive Sims](https://www.youtube.com/watch?v=NO1lvc3ikXE) 

* [[Game Mechanics -- Advanced Game Design by Adams and Dormans|Adams and Dormans]] - Ch. 10 - 11
* [The Level Design Book](https://book.leveldesignbook.com)

