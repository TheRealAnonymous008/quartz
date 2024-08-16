* Physical limitations are well understood by designers; mental limitations are greatly misunderstood. We should treat all failures in the same way: *find the fundamental causes and redesign the system so that these can no longer lead to problems.*
* All humans are prone to [[Faculties of the Mind#Reasoning|error]]. *When people err, change the system so that the type of error is reduced or eliminated*.
* It is not possible to eliminate human error if it is thought of as a personal failure rather than a symptom of poor design.
	* The natural tendency to blame someone for an error is even shared by those who made the error.
	* We can't fix problems unless people admit they exist. Thus, blame is unproductive since it focuses the cause of the error on the human rather than the design.
# Errors
* **Error** is defined as any deviance from appropriate behavior

* The most common reason for errors is *in the nature of the tasks and procedures that require people to behave in unnatural ways*. 
	* Staying alert for hours at a time
	* Providing precise, accurate, control specifications
	* Being subjected to multiple interleaving actions.
	* Being interrupted, especially when design makes it hard to resume tasks after interruption.
	* The attitude of people toward errors.
	* **Time stress** - where tasks have time pressure, exacerbated by environmental factors.

* *Social pressures can also contribute to errors being made*. 
	* Never underestimate the power of social pressures on behavior, causing otherwise sensible people to do things they know are wrong and possibly dangerous.
	* *Social pressures transcend design as it requires training, cultural shifts, and appropriate policy*.
	* Adding more people to check a task makes it less likely that it will be done right
	* Social pressures also lead to people not reporting when mistakes are made.

## Taxonomy of errors
* The taxonomy can be related to [[The Psychology of Everyday Actions|the seven stages of action]].
	* Slips happen during execution
	* Mistakes happen during evaluation. and between the seven stages.
### Slips
* A **slip** occurs when a person intends to do one action and ends up doing something less.

	* **Action based slips** involve the wrong action being performed.
		* **Capture slips** are situations where instead of the desired activity, a more frequently or recently performed one is chosen (i.e., the frequent captures the infrequent). 
			* They become prevalent for experts who can do the task on autopilot.
			* *The design implication is to avoid procedures that have identical opening steps but diverge*.
		* **Description similarity slips** involve acting upon an item similar to the target because the description of the target is sufficiently vague.
			* Descriptions that usually suffice fail because they do not distinguish the desired target from alternatives.
			* *The design implication is to ensure that controls and displays for different purposes are significantly different from one another*.
		* **Mode errors** occur when a device has different states in which the same controls have different meanings (or modes). 
			* *This is almost unavoidable when we add more functions to the device*.
			* Users are not always aware of the mode that a device is in, especially when they get interrupted, distracted, or confused.
			* *The design implication is to avoid modes if possible. If not, make modes visible. Add signifiers and account for interference*. 

	* In **memory lapses**, memory fails so the intended action is not done or evaluated.
		* *The immediate cause of memory lapses is interruptions* since these overload the capacity of short term memory.
		* *The design implication is to design with memory in mind. [[Knowing What To Do -- Constraints, Discoverability and Feedback|Store knowledge in the world]]*. 
	* *Slips tend to occur more frequently to skilled people because they result from a lack of conscious attention to the task*.

### Mistakes
* A **mistake** occurs when the wrong goal is established or the working place.
	* Mistakes are the byproduct of a [[Human Biases|biased]] reconstruction from memory.
	* **Rule-based** mistakes  involve a misdiagnosis of the situation being undertaken.
		* This is due to circumstances when normal routine is no longer applicable, but the new situation is one that is known and where there is already a well-prescribed **rule** governing actions.
		* Thus, this arises from:
			* The situation being *misinterpreted*, which means the wrong rule is selected
			* The *rule is faulty* because it is formulated improperly.
			* The correct rule is invoked *but the outcome is incorrectly evaluated*.
		* *These mistakes are difficult to avoid and difficult to detect*. The problem is information overload; there is information to contradict and to support the choice of rule.
		* *The design implication is to provide as much guidance as possible to ensure that the current state of things is displayed in a coherent, easily interpreted format*
			* It is important to remember that when a mistake is made, people were probably overwhelmed with a lot of irrelevant information..

	* **Knowledge based** mistakes involve a misdiagnosis due to erroneous or incomplete knowledge.
		* This arises from *faulty conceptual models*
		* It also arises in novel situations such that no skills or rules cover them. Thus, a new procedure must be devised via [[Problem Solving]].
		* *The design implication is to introduce to correct conceptual models, and to allow knowledge to be easily searched*.

	* **Memory lapse mistakes** take place when there is forgetting at the stages of goals,  plans or evaluation.
		* This arises from interruption. The cure is the same as that for memory lapse slips.
		* *The design implication is to assume interruptions are part of the user's workfow*.

### Deliberate Violations
* Sometimes people knowingly take risks, especially when there is a high positive reward.
* Most rules are written more with a goal toward legal compliance than with an understanding of the work requirements.
	* *A major cause of violations is inappropriate rules or procedures that invite violations*.
* **Routine Violations** occur when noncompliance is so frequent that it is ignored.
* **Situational violations** occur when there are special circumstances that lead to the violation or in order to complete a job.
## Additional Remarks
* In general, it is bad design to impose a sequential structure to task execution unless the task itself requires it as there is a risk of memory lapse errors.

# Error Mitigation
* **Root cause analysis** aims to investigate the accident until the single underlying cause is found. However, this should consider two things:
	* Most accidents do not have a single cause
	* Analysis shouldn't stop as soon as human error is found.
	* **The Five Whys** - *When searching for a reason, keep asking why even after a reason has already been found*.
		* This is limited by the fact that the question of "why" can be answered in many ways.
		* It also tends to emphasize the need to find a single cause.
		* It is also prone to the tendency of stopping too soon due to reaching the limits of one's knowledge.
* **Jidoka** - automation with a human touch (from Toyota). Workers are encouraged to report errors in the assembly line and experts convene to figure out why the error occured.
* **Poka-Yoke** - add simple features to constrain  the operations so that they are correct. These features are [[Knowing What To Do -- Constraints, Discoverability and Feedback|forcing functions]].

* Action slips are relatively easy to detect because it is usually easy to notice a discrepancy between the intended act and the one that got performed.
* Memory-lapse slips are difficult to detect precisely because there is nothing to see
* Mistakes are difficult to detect because there is seldom anything that can signal an inappropriate goal. *Mistakes in general take a long time to be discovered*.
* Misdiagnoses are difficult to detect because they are supposedly based on knowledge and logic, so they seem reasonable enough. *Mistakes tend to be rationalized*.
* Memory-lapse mistakes are also hard to discover since it entails realizing something (i.e., a plan) has been forgotten.

* Once people find an explanation for an apparent anomaly, they tend to believe they can now discount it. But explanations are based on analogy with past experiences, experiences that may not apply to the current situation (see [[Egocentric Biases|Illusion of Validity]]).
* *In hindsight, events seem logical*.  During an incident, there are never clear clues.

## Designing for Error
* It is tricky to design for when things go wrong. *Machines are not intelligent*.
* *Many systems make it impossible to discover where an error is made*. These need to be done:
	* Understand the causes of error and design to minimize those causes.
	* Do sensibility checks. Does the action pass the “common sense” test?
	* Make it possible to reverse actions—to “undo” them—or make it harder to do what cannot be reversed.
	* Make it easier for people to discover the errors that do occur, and make them easier to correct.
	* Don’t treat the action as an error; rather, try to help the person complete the action properly. Think of the action as an approximation to what is desired.
* *Many systems make it difficult to resume after an interruption*.
* Doing two tasks at once takes longer than the sum of the times it would take to do each alone
* *Many systems have annoying warning signals that people remove the annoying safety features*.

* Consider the following in design
	* Prevention involves *adding constraints* to actions.
	* Include a method to *undo* previous commands whenever possible.
	* Use *confirmation and error methods*. Feature a prominent display of both the action and its implications.
		* Warning messages are surprisingly ineffective against mistakes because they can be ignored. The implications are:
			* *Make the item acted upon more prominent*.
			* Allow for *undo*.
	* Use **sensibility checks** -- machines should perform a sanity check and flag seemingly unusual actions.
	* Minimize slips by *ensuring actions and controls are as dissimilar and distinct as possible.*

* **Swiss Cheese Model** - *most errors do not lead to accidents. Accidents are caused by errors lining up*. 
	* But this is also why attempts to find the root cause of accidents are futile, because accidents are caused by many events. A simple explanation does not suffice.
	* It also has the following design implications:
		* *Add more layers of defense* to prevent accidents.
		* *Reduce* the opportunity for slips and mistakes to occur.
		* *Alert* human operators about potential accidents.
		* *Think of systems rather than sole designs*. Accidents are a system failure. Make the system more reliable, robust, and resilient.
		* *Test on the infrastructure itself*, keep in mind the complexity of systems and real world failures.

* **The Paradox Of Automation**. Automation can be beneficial to make processes more efficient, but when they fail, especially for complex tasks, they can be catastrophic as it takes time to detect errors, and by then it might be too late.
# Links
* [[Design of Everyday Things]]