* **Trick Taking** - Players play cards from their hand to the table in a series of rounds or “tricks,” which are each evaluated separately to determine a winner and to apply other potential effects.
	* In some games, cards are dealt evenly. In others, player declare the number of tricks they want
	* Many games require that players “follow the lead” or “follow suit,” which means playing a card of the same suit as the lead, if possible
	* It shares many dynamics with [[Tabletop Mechanics -- Auctions|Once-Around auctions and Sealed-Bid auctions]]. A Trick-Taking game is similar to an auction in that players hold a hand of currency and bid that currency to win the trick.
	* Trick taking emphasize hand-management and planning skills rather than valuation skills.

* **Ladder Climbing** - Players play one card or a set of related cards. Subsequently, players must play cards of an equal or higher value of the same set already played. The last player to successfully play wins the right to start a new round of Climbing.
	* Shedding all your cards, also called “going out,” is generally a goal in Climbing games, and in many classic shedding games, it is the win condition.

* **Melding** - A set of cards in a specific relationship to one another that allows them to be played to a table or scored is a meld. When laying these cards down, the way the cards splay, or overlap one another, may sometimes reveal or conceal certain abilities or attributes.
	* A kind of [[Tabletop Mechanics -- Set Collection|Set Collection]] found in card games.
	* Players must assemble a meld in their hands and only then play the melds out onto the table.
	* An important design consideration for melds is that each element (card or tile) should belong to more than one possible grouping. This gives more nuanced gameplay. 

* **Card Draw, Limits, and Deck Exhaustion** - Games frequently limit the number of cards that may be held in a given container, whether that is a hand, a deck, or something else. Similarly, various game effects trigger when a deck, draw pile, or hand becomes exhausted.
	* Typically serves as a way to balance power. Cards equate to some ability to do something.
	* In many games, there is no possibility of card advantage because card plays and Card Draws are symmetrical and metered.
	* Consider adding rules relating to draws and discards to allow players to control their deck better.
	* Some games treat Card Draw as similar to any other resource
	* Some games allow players to exceed their hand size temporarily and then discard some of their cards.

* **Deck Building** - Players play cards out of individual decks, seeking to acquire new cards and to play through their decks iteratively, improving them over time through card acquisition.
	* In many deck builders, players will dispose of their whole hand of cards each turn.
	* Commonly, players have a limit on the number of cards they can play as actions
	* Some other deckbuilding mechanisms include:
		* Forced discards.
		* Cards only purchase-able with a given currency.
		* Cards that are not discarded per turn.
		* Interactions with the discard pile
		* Incentives to adding variety to the deck
		* Giving persistent resources.
	* Games can be distinguished as **drafting verbs** -- where cards represent actions, and **drafting nouns** -- where cards represent actors that can act in the game space under certain conditions.

* **Drafting** - a means of distributing cards or other game elements to players through an ordered selection process.
	* Players ask "What do I want most right now? Do I have to take it now, or will it be here for me next turn too?"
	* Related to [[Tabletop Mechanics -- Actions|Action drafting]] and [[Tabletop Mechanics -- Worker Placement|Worker placement]]
	* In a **Rochester draft** all cards are laid on the table and players each take one card on their turns. Play continues until all cards have been taken or all players pass
		* Make all options viable and available
		* Can be overwhelming but the draft gradually simplifies as play progresses.
		* Tests players' ability to recall what cards their opponents took.
	* In a **pick and pass** system, a trigger causes the active player to draw a hand of cards equal to the number of players at the table, select one to keep and pass the rest.
		* Tightly coupled with [[Tabletop Mechanics -- Game Structure|turn order]]. 
		* Imbalances due to turn order can be mitigated with a **snake draft** where the order of drafting in round $1$ is inverted in round $2$.
		* Another approach is to have parallel pick-and-pass drafts happen simultaneously. This accelerates gameplay, but players are only able to see a fraction of the cards.
	* **Wheeling** is a skill employed in these games where cards are not taken away now. They are taken later when turn order permits.
		* In many CCGs, card synergies are tightly coupled such that once you begin drafting toward some strategy or deck type, other cards drop to little or even negative value. 
		* The extremes in valuation for cards between players make wheeling much more likely to succeed, since the card that one player values the most may have little use to the other players.
		* **Hate-drafting** is a technique of taking a card to deny it from the opponent.
		* Both Wheeling and Hate-Drafting can make the game more engaging.
	* Having players play a card immediately after drafting can help keep the draft on schedule and avoids bottlenecking and confusion by forcing all players to play at roughly the same cadence

* **Deck Construction** - Prior to a multiplayer game session, players select the cards that will make up the decks they use during the multiplayer session. 
	* The game provides rules governing how decks may be constructed that typically covers the number of cards in the deck, required cards, restricted cards, and limits on copies of the same card.
	* This doesn't just apply to cards. It can apply to any game where a group is assembled.
	* Perhaps the most important rule of all in deck construction is defining the pool of cards available to players
	* In collectible games, another key limit is which cards players own and thus have access
		* Other types of limits include limiting players to selecting cards of a particular faction and to selecting cards with a total cost that falls under some budgeted amount.
		* Faction identities emerge from the abilities assigned to their cards, and players might prefer factions that support their desired play style
	* Rules about deck construction are critical to ensuring playability, balance, and limitation on exploits
		* In games where deck exhaustion is a loss condition, the maximum number of cards in the deck determines how appealing and successful a “milling” strategy, which forces opponents to discard from their decks, might be.
		* A required minimum number of cards in the deck, coupled with limits on copies of cards, sets the variability range for a deck.
	* There are accessibility issues, namely for new players who may be overwhelmed. One common approach to this is to offer starter decks or make deck construction an engaging process
	* The alternative to deck construction is drafting, where the deck has certain limitations.
	* Deck construction is part of a larger design pattern in which players choose the kinds of power-ups, abilities, and characteristics they want to play with. An important aspect of this is the degree to which the [[Games as Culture|metagame]] plays a role.

* **Multi-Use Cards** - Multiple actions are shown on a card, but only one can be used.
	* A positive feature of this mechanism is that it presents the players with clear and focused options
	* It also naturally leads to difficult decisions, particularly when only one option may be chosen the entire game
	* A key consideration for the designer is which abilities to combine on the same card. Ideally, match the power levels and make a "superior" option difficult to determine.
	* A superset of [[Tabletop Mechanics -- Actions|Action -Event]]. 
	* An alternative approach to Multi-Use cards is to allow the cards themselves to be used as physical objects, typically as a discard to play other cards.

* **Tags** - Game objects, typically cards, have icons or other identifiers that identify them as belonging to specific categories
	* Tags may trigger special effects and/or have values and meaning that can vary, even within the scope of a single play
	* Tags are additional parameters on top of the base meaning of the game element, so tags represent a means of coupling the game element with more mechanisms and systems.
	* Tags are also bookmarks that can reference a variable set of possible rules that are encoded elsewhere, so they are also a means to modularize, or uncouple, game triggers and game effects.
	* The combination of tag types, mechanisms that key off of the tags, and the effects themselves create a highly expressive system
	* Borrows heavily from the ideas in [[Object Oriented Programming]]. 
# Links
* [[Building Blocks of Tabletop Game Design - An Encyclopedia of Mechanisms by Engelstein and Shalev]] - Ch. 13