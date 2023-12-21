* The principles outlined [[System Opportunities|here]] are helpful for balancing games since [[Games as Rules#Emergent Systems|games are systems]]. 
	* Use slow and durable negative feedback loops to balance positive feedback. 
* Generally we can either [[Lenses for the Process|Playtest]] the game or simulate the game to gather data. Analytical tools such as [[Internal Economy Design Patterns|design patterns]] also help in analysis. 

* It is often easier to perform the game balancing if the randomness mechanisms are removed. This helps detect [[Game Theory - Strategy|dominant strategies]].
* Testing for specific strategies and player roles is a good way to understand the viability of these strategies during play . 
* If you have to spend a lot of time trying to make artificial players that successfully control your economy, that’s usually an indication that your economy has a problem
* Run experiments that aim to answer specific balancing questions.

# Balancing Principles 
* According to [[The Art of Game Design -- A Book of Lenses by Schell|Schell]]

## Fairness 
* Players want to feel that the forces working against them do not have an advantage that will make them impossible to defeat 
* **Symmetric Games** - players have equal powers and resources. Suitable for Competitive games.  
	* Balancing necessitates considering first-move advantage (either random or least skilled first)
* **Asymmetrical Games** - players have different resources and abilities. We may want this for a variety of reasons 
	* To simulate a real world experience 
	* To allow for exploration 
	* To allow personalization by giving players resources that match their skills.
	* To level the playing field. 
	* To create interesting situations
* One way to balance an Asymmetrical game is to give players the same total "sum value" of resources, with each resources having the same values.
* Another way is *circular balance* where there is a rock-paper-scissors dynamic. Something exists as a counter to something else.
* Relevant Lenses: [[Lenses for Game Design - Lenses#37. Fairness|Fairness]],

## Challenge vs Success
* The appropriate level of challenge keeps the [[Lenses for the Player#The Experience is in the Player's Mind|player]] in [[Flow State Model|flow]]. 
* Some common techniques for balancing:
	* Increase difficulty with each success. However, consider the tense and release pattern
	* Let players get through easy parts fast. 
	* Create layers of challenge (for example via a scoring system)
	* Let players choose the difficulty level (this comes at the cost of balancing more versions of the game)
	* Playtesting with a variety of players. 
	* Give the losers a break 
* It may make sense to consider what percentage of players do you want to complete the game. 
* *Remember*: Just learning the game is already a challenge
* Relevant Lenses:  [[Lenses for Game Design - Lenses#38. Challenge|Challenge]],

## Meaningful Choice
* Games should have [[The Fundamentals of Game Design#Player Choice|meaningful]] choices. 
* [[Games as Rules#Game Theory Systems|Dominant strategies]] ruin game balance and make the game less fun. Balancing should get rid of dominant strategies
* The number of choices provided to the player should equal the number of things the player wants to do -- too much and its overwhelming, too little and the player is frustrated.
* Consider **triangularity** - the classic trade-off of low risk low reward and high risk high reward.
* Relevant Lenses  [[Lenses for Game Design - Lenses#39. Meaningful Choices|Meaningful Choices]], [[Lenses for Game Design - Lenses#40. Triangularity|Triangularity]]

## Skill vs Chance
* Chance and Player skill negate each other. 
* One common way to balance these is to alternate the use of chance and skill in the moment to moment gameplay. 
* According to David Perry, the key to addictive games is designing the game such that players are doing three things
	* Exercising a skill 
	* Taking a risk 
	* Working a strategy 
* Relevant Lenses: [[Lenses for Game Design - Lenses#41. Skill vs Chance|Skill vs Chance]]

## Heads vs Hands
* Consider how much of the game should involve doing a challenging physical activity vs how much it should involve thinking, again taking into account the preferences of the target demographic. 
* Relevant Lenses: [[Lenses for Game Design - Lenses#42. Heads and Hands|Heads and Hands]]

## Competition vs Cooperation
* Games provide avenues for both [[Games as Rules#Systems of Conflict|competition and cooperation]]. These can be combined and used in different ways. 
* Relevant Lenses: [[Lenses for Game Design - Lenses#43. Competition|Competition]], [[Lenses for Game Design - Lenses#44. Cooperation|Cooperation]], [[Lenses for Game Design - Lenses#45. Competition vs Cooperation|Competition vs Cooperation]] 

## Short vs Long 
* Balance should take into account the length of the gameplay
* Too short and choices will not be meaningful enough. 
* Too long and the game may feel like too much of a time commitment. 
* *The main factors that affect the duration of the game are the win conditions*. 

## Rewards
* Players are motivated by a certain desire that can be fulfilled by the game. 
* *Games judge players, but they should judge them fairly*. 
* The [[Players and Why We Play Games#Rewards|following]] are some examples of rewards: *We balance the rewards by controlling which are given out and when*. 
	* Rule of thumb: More rewards = better 
	* Rewards have diminishing returns. People have a tendency to get acclimated to rewards the more they receive them. 
	* Favor variable rewards over fixed rewards. 
	* *Rewards are generally a better tool for reinforcement than punishment*. If you need to encourage something, use a reward. 
* Relevant Lenses: [[Lenses for Game Design - Lenses#46. Reward|Reward]]

## Punishment 
* The [[Players and Why We Play Games#Rewards and Punishments|following]] show examples of punishments. 
* Be careful with setting punishments in game. Balance them by *making them reasonable.*
	* *Punish the player for things that they are able to understand and prevent* Otherwise, the player will feel like they are not in control.
	* Punishments that are unfair have their place for players who are motivated by challenges. However, even these players must be able to see how they can prevent the punishment. 
* A combination of light punishments is enough to encourage certain behaviors. 

* Relevant Lenses: [[Lenses for Game Design - Lenses#47. Punishment|Punishment]]

## Freedom vs Controlled Experience 
* There is a [[Trade Offs#Freedom of Choice Trade-Off|trade off]]  in giving the player freedom of choice. Not only that, but it is extra work for the designers in giving the player more options.
* Consider *where to give the player freedom and how much freedom to give*. 

## Simple vs Complex 
* There are two kinds of complexity in a game: 
	* **Innate Complexity** - when the very rules of the game are complex. *Generally bad because it makes the rules convoluted*. 
		* If there are a lot of exceptions to the rule, then there is innate complexity. 
	* **Emergent Complexity** - when simple rules give rise to complex phenomena. *[[Games as Rules#Emergent Systems|Emergence]] is good*. 

* There are two kinds of balancing
	* **Artificial Balancing** - adding more rules and more innate complexity to balance the game. 
	* **Natural Balancing** - the desired effects emerge naturally from the game. 

* ***Elegance** arises from simple systems that perform robustly in complex situations. Elegant game elements are those that serve many purposes*.  
	* Whenever possible, favor removing something or using something that already exists than adding something new. 
* *Elegance is balanced with character*. Too much elegance makes the game too simple. *Adding character entails adding lovable, quirky elements that make the game unique*.
	* Elegance is simplicity. Character is complexity. Both are needed.

* Relevant Lenses:  [[Lenses for Game Design - Lenses#48. Simplicity / Complexity|Simplicity and Complexity]], [[Lenses for Game Design - Lenses#49. Elegance|Elegance]], [[Lenses for Game Design - Lenses#50. Character|Character]]

## Detail vs Imagination 
* Decide exactly what details should be provided, and which should be provided to the player's imagination
* Some tips or how to do it well:
	* *Only detail what you can do well.* When you cannot detail it in high fidelity, use the player's imagination to do the detailing for you. 
	* *Give details the imagination can use* - Give details that the player can easily understand. This serves to introduce [[Knowledge in the Head and In the World|knowledge]] that is easily parsed.
	* *Familiar things do not need much detail*. The imagination cannot help when the player is not familiar with the setting. 
	* *The binocular effect*. Use a little detail to get a lot of imagination. Briefly show a detailed view then zoom out and let the imagination take care of the rest. 
	* *Give details that inspire imagination*. Appeal to the player's fantasy. 

* Relevant Lenses:  [[Lenses for Game Design - Lenses#51. Imagination|Imagination]]

## How to Balance a Game 
* Use the [[Lenses for Game Design - Lenses#8 . Problem Solving|lens of the problem statement]]. Balancing is a [[Design|design issue]]. 
* *Double and halve*. That is, narrow down the parameters of the game by doing a binary search. Push the values farther than what intuition tells us.
	* *Change something so that you can feel the difference right away*. 
* *Train your intuition by guessing exactly*. 
* *Document the model* Write down what you think the relationships are between the things being balanced. This helps clarify things and gives a framework to record results of balancing. 
* *Tune the model as you tune the game*. Essentially, follow [[Science|the scientific method]].
* *Plan to balance*. Put systems that make it easy to change the values you expect to balance. A variation of [[Lenses for the Process#The Game Improves through Iteration|iteration]].
* *Most of the time, the players shouldn't balance the game*.  The players are biased-- they want to win and poor balance may help with that. 
	* However, take into account player feedback. 
* *Beware the pitfalls of dynamic game balancing* -- that is, difficulty that adjusts to the players. This is not to say it is unviable, but that it comes with its own challenges. 
	* *It spoils the reality of the world.* If the abilities of their opponents are relative to the player, then the illusion that they are fixed challenges to be mastered disappears .
	* *It is exploitable*. If the game gets easier when they play badly, they may just play badly to make the game easy. 
	* *Players improve with practice*.

* Relevant Lenses: , [[Lenses for Game Design - Lenses#52. Economy|Economy]] [[Lenses for Game Design - Lenses#53. Balance|Balance]]

# Links 
* [[Game Mechanics -- Advanced Game Design by Adams and Dormans|Adams and Dormans]] - Ch. 8 - Ch. 12