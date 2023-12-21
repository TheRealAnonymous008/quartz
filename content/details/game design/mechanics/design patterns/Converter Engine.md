* *Intent*: Two converters are set up in a loop to create a surplus of resources that can be used elsewhere
* *Motivation* Two resources that can be converted into each other fuel a feedback loop that produces a surplus of resources. At least one of the converters must output more resources than it takes in to create the surplus. 
# Applicability
* You want to create a more complex mechanism to provide the player with more resources than a [[Static Engine]] or a [[Dynamic Engine]]. 
* It increases game difficulty since the feedback loop must be maintained. 
* You need multiple options and mechanics to tune the profile of the feedback loop that drives the engine and thereby the stream of resources that flow into the game.
# Participants 

![[Converter Engine.png|300]]
<figcaption> Converter Engine. Image taken from Adams and Dormans </figcaption>

* The converters change energy into fuel and fuel into energy. The net result is a surplus of energy 

# Considerations
* The converter engine is a more complicated mechanism than most other engines but also offers more opportunities to improve the engine. As a result, a converter engine is nearly always dynamic.
* *Introduces the possibility of deadlock* -- where both resources dry and the engine stops working. Players may also accidentally create these deadlocks. 
* The feedback loop present needs to be balanced appropriately

* Fix deadlocks by using a weak [[Static Engine]] as a constant source.
* *More steps involved in the feedback loop means more difficulty in maintaining the loop but also more opportunities for tuning the engine*.
	* If there are two few steps to begin with, just use a dynamic engine 
	* If there are too many steps, the system becomes too difficult to maintain. 
* Introduce unpredictability for more interesting scenarios but beware this increases the risk of deadlock. 
* *Put a limiter in the cycle*. This keeps the engine under control and the surplus in acceptable ranges. 