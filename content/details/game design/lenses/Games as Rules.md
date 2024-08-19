* **Rules** - the deep formal  structure of a game from which all real-world instances of the game's play are derived.  
* If you can't identify the core rules o a digital game, you are out of touch with your own design.
# What are Rules?
* Rules have the following general characteristics
	* Limit player action. *To play a game is to voluntarily restrict behaviors according to the rules*.
	* Explicit and unambiguous. 
	* Shared by all players.
	* Fixed. They do not change as a game is played. If they are modified, they are done so in a regulated manner determined by other fundamental rules.
	* Binding. They are meant to be followed over the course of the game.
	* Repeatable. Portable between setups of different players.
* [[Models for Game Rules#Salen and Zimmerman's Model|Salen and Zimmerman's model]] applies 
* In order to play even the simplest games, the players must know and understand the rules: 
	* The traditions associated with the game
	* How to interpret the written rules
	* The conventions of playing any game according to the culture of the participants.
	* The ability to respond to the real life context to which the game is being played.

# Games as Formal Systems
### Emergent Systems
* *[[Complex Systems|Emergence]] and Complexity  are crucial aspects of games since they are [[System Science|systems]]*. They allow the game to be more systemic and meaningful.
* Complexity can arise unexpectedly from a handful of simple elements and rules. It is systematic order that emerges from the dynamic interactions of agents within an environment.
	* We may be able to describe the rules of the game with simple statements, but *we can never determine how the game itself will play out*.
* *In parts where meaningful play exist -- some aspect of the game system will be complex* 
	* *Parts are coupled*, interrelate with one another in a recursive manner, and generate unpredictable patterns of behavior.
	* Interactions within a game are *context-dependent* meaning the changes that occur are not the same very time.
* In games, emergence arises through the interaction of the formal game system with the decisions made by the players.
	* If the game system is not complex it does not provide a large possibility space for players to inhabit and explore through meaningful play.
	* *Be specific when defining the relationships between elements in the game*.

* *Game design is about creating experiences but indirectly and only through designing the rules.*.
	* We must account for the complex interactions between game elements that lead to emergent gameplay. 
	* Emergent systems allow us to reward players for exploring new ways to play the game. 
	* Often, *rules need to be tuned to create a rich play experience*. 

### Systems of Uncertainty
* *Uncertainty about the outcome of a game is a necessary ingredient in giving a game a feeling of purpose*. Players shouldn't know how a game will play out.
* There are two levels at which uncertainty operates in a game. 
	* On the micro-level are the actual operations of chance that occur at isolated moments in the system of a game. 
	* On the macro-level are larger questions of uncertainty, which relate to the ultimate outcome of the game.
* Without uncertainty the outcome of the game is predetermined -- player choice is rendered meaningless as they do not impact the outcome of the game.
* To make games more meaningful, there is a balance between the following.
	* **Risk** - a situation where there is some uncertainty but the game's players know the nature of the uncertainty.
	* **Uncertainty** - players have no idea about the outcome of the game
* *The feeling of randomness in a game is more important than having randomness itself* -- that is, games should not have a certain outcome.
	* Less Random = more dry / more competitive.
	* More random = More chaotic and unstructured.
		* Even the simple act of choosing to play, as much as the game is random, can be meaningful if the player has [[The Fundamentals of Game Design#Player Choice|choice]]. 
		* *In games of pure chance, the player's relation to the system needs to be carefully designed*
* *When having elements with RNG, understand [[Probability Theory|probability]] and [[Statistics]] first* to pace the game in an appropriate manner.
* Beware of when Uncertainty breaks down into an non-meaningful player experience:
	* Make sure your randomization functions are actually random (i.e., follow the target distribution you are aiming for.) *Changes in the randomization can lead to unexpected errors.*
	* Make sure the procedures for determining randomness operate how you intend them to. Remember that *players may use the randomness itself strategically, in ways you do not intend.*
	* Remember that players are prone to [[Extension Neglect|fallacies about.]] [[False Priors|probability]] Thus, *understand how players misinterpret randomness*.

### [[Information Theory]] Systems
* *Games are systems wherein there is a flow of information*. In this context:
	* *Information has nothing to do with the content* or meaning of a message.
	* *Information is a measure of uncertainty* (as in the standard definition in Information Theory.), and so Information in a game correlates to meaningful action rooted in uncertainty.
* As Information Theory Systems, *games rely on signal transmission and reception*. 
* In this context, *noise in the channel is desirable* because it increases information (uncertainty). 
	* This is a consequence of the lusory attitude since in ordinary contexts, we do not want noise
* We can also consider *playing with redundancy*, for example by introducing redundant hints in a puzzle game or by introducing multiple paths the player can take.
	* *Redundancy = Flexibility*. However, do note [[Trade Offs#Freedom of Choice Trade-Off|the tradeoffs of having a flexible system]]. We want some structure otherwise play is no different than taking random actions.
* *Game design is an act of balancing noise and redundancy*.

### Systems of Information
* In this context, *games are interactive systems that put knowledge or information at play*. We manipulate the information itself -- its acquisition, transformation, concealment, and whether or not we remember it.
* **Perfect Information** exists when all players have complete knowledge about the game at all times.
	* Games of perfect information tend to be more competitive.
* **Imperfect Information** exists when some of the information may be hidden from players.
	* Games of imperfect information tend to rely on trickery, deception, and mistrust.
* We may also classify the balance of information as follows (according to Ceila Pearce)
	* Information is known to all players.
	* Information is known to only one player.
	* Information is known only to the game.
	* Information is randomly generated.
* *Information flows within the game -- from being known by none to one to all. Information is a part of an **economy of information***
	* The value of information gains meaning within the larger system of the game.
	* **Objective information** pertains to the game's information structures. 
	* **Perceived information** pertains to the player's understanding of the perceived information.
	* Interaction between objective and perceived information governs the dynamics of information.
* *Information can be concealed*. For example through complex item economies, through fog of war, hidden locations and actions, and by having the game manipulate information itself.
* *Making use of information systems within the game requires information be made meaningful through player interaction*. Information should be discernable and integrated.

### Cybernetic Systems
* *Games are dynamic systems that change over time with their formal structures allowing these changes*. 
* Games as cybernetic systems are based on the interaction of inputs and outputs with its internal mechanism.
* *Games are systems that rely on feedback mechanisms*. The design of feedback [[Game Economy|mechanisms]] shape the tendencies of the game, the game balance, and the tendencies of players during play.

* *Being composed of possibly multiple cybernetic [[System Science|systems]], games are inherently complex*. 
* In design, we should *play with the presence of negative and positive feedback loops*. 
	* Feedback systems can emerge from your game systems by accident. 
	* Feedback systems can take control away from the players.
		* Positive feedback loops are usually dampened to prevent their acceleration.
		* Negative feedback loops can lead to stale gameplay, so there is a need to break out of them on occasion. 
* **Dynamic Difficulty Adjustment** - makes use of feedback loops to adjust the difficulty of play.
	* On one hand, it can feel like the system cheating as players no longer have agency.
	* On the other hand, it can be seen as a way for all players to have an optimal experience.

### [[Game Theory]] Systems
* *Games are systems that involve rational choice that involve strategic decisions and outcomes*. 
* Game states can be mapped out using decision trees. For real world, continuous cases, or unruly cases we can deal with discrete approximations to map out relationships between game states.
* A **strategy** [^1] is a methodology for navigating the decision trees towards a desirable outcome, based on a state's **utility** (quantified preference)
* *In game design, avoid having games where one player has a dominant, optimal strategy. These lead to **exploits** and **degenerate strategies***.
	* And they are not fun because there is no longer any choice besides the optimal one.
	* Remember players will optimize the fun out of the game.
	* Degenerate strategies are a sign of weaknesses in the formal systems of the game.s

[^1]: Not unlike [[Reinforcement Learning]] policies
### Systems of Conflict
* As systems of conflict *games are a contest of powers.*.
* The conflict of a game arises as the game players struggle towards achieving a goal.
* Conflict in a game can be:
	* Single player vs single player
	* Group vs Group
	* One vs Many
	* Every player for themselves
	* Single player competing against the game system
	* Individual players competing side by side against the game.
	* A group of players cooperating against a game.
	* **Direct** - where players can interfere directly or **Indirectly** -- where players cannot directly interfere with others.
* *A game's systems dictate what kinds of conflict are available for the game. Conflict in itself can determined by the players based on the game systems*. 
* *Games are competitive* All games have goals. The competitive striving towards a goal is fundamental in giving shape to the structure of a game and the way the game creates meaning 
	* In a well designed game that supports meaningful play, the journey between start and goal should be efficient -- every element contributes to the larger experience.
	* *What constitutes success must be clearly defined*. 
* At the same time, *Games are cooperative*. To play a game is to cooperatively take on the artificial meanings of the game. This class of cooperation is called **systemic cooperation**.
* *Conflict in games should be fair*.  All players should have an equal chance of winning.
	* Remember, in practice, no game is actually fair. Nevertheless, *all players should believe the game is fair*.

### Subverting Rules
* *Breaking the rules is an intrinsic part of playing games*. Players can make and play by their own rules even within the same game structures
* *Game design is about playing with ideas -- even seemingly fundamental ideas.*
* **Player Typology**

| Type | Relationship to rules | Interest in Winning | Degree of Lusory Attitude | 
| --- | --- | --- | --- | 
| Standard Player | Attempts to follow the rules as best as possible | Normal | Present |
| Dedicated Player | Studies and masters the rules to find loopholes | Plays to master and perfect the game | Highly present since they relish the inefficiencies of the game as important challenges. | 
| Unsportsmanlike Player | Follows explicit rules. Does not follow implicit rules.| Very interested in winning. | Sometimes like the dedicated player. Sometimes like the cheat | 
| Cheat | Violates the operational rules in secret | Intense interest in winning | Pretends to possess it. In reality, does not like the challenge offered by the game |
| Spoilsport | No interest in adhering to rules | None | Does not acknowledge the lusory attitude | 
* Remember, a game is a social contract, the presence of other players is important to maintaining the authority of the magic circle. Hence, most players are standard players.
* As game designers, it is important to understand the range of player types that encounter your game, and the kinds of relationships they have to the rules, goals, and magic circle that your game delineates. *Account for the non-standard player types as well*. 
* *Whether an exploit is considered cheating depends on context, particularly on how the game experience is supposed to be*.
	* However, there is a fine line between degenerate strategies and imaginative ones.
	* *Degenerate strategies can lead to [[Creativity|iterative design]]. It is beautiful to think of a game design as a design in process, which can grow and evolve over time
* When rule-breaking becomes sanctioned, a new layer of implicit rules enters the space of play.
	* In professional sports, for example, this leads to behavior of baiting the other team to committing a rule violation.
	* However, even when sanctioning rule-breaking, *we must take care to control the kind of cheating to make sure the game still remains playable and meaningful.*
	* Even then, remember that *removing the artificial nature of the game conflict means that cheating can destroy the implicit cooperation in the magic circle, letting the conflict bleed into the real world* .
* Some examples of rule-breaking:
	* Easter eggs
	* Cheat codes (sanctioned by the game)
	* Game guides and walkthroughs.
	* Workaround and exploits.
	* Using actual cheats (i.e., smurfing)
	* Hacks (here we not only break the rules, but intervene on the code level)
	* Spoil-sport hacking (DDOSing)
* As a game design principle, we can *reward player mastery over the rules by giving them authority to modify them*--done so in an attempt to create a deeper play experience.
* *Game designers are rule-breakers*. Do not limit yourself with the restrictions outlined in the above schemas.

# Links
* [[Rules of Play -- Game Design Fundamentals by Salen and Zimmerman|Salen and Zimmerman]]