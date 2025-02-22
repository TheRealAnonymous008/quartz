* [ABM never took off in economics because it was already a “model-oriented” discipline.](https://economistwritingeveryday.com/2022/03/14/why-agent-based-modeling-never-happened-in-economics/) [[Agent Based Modeling|ABM]] is inherently empirical which means that: 
	* It is hard to validate the created model; 
	* It is hard to prove that these models are indeed theoretically sound; 
	* There are a lot of bad ABM models for economics compared to good ones since it is easy to do; and 
	* [[Data Analytics]] had more ground compared to [[Agent Based Modeling]]


# ABM
* *[[Microeconomics|Microeconomics]] Models*
	* A simple model can be used to simulate [[Scarcity, Supply, and Demand|Supply and demand]] using the following assumptions:
		* Buyers with heterogeneous internal valuations will create a downward sloping demand curve.
		* Sellers with heterogeneous costs will produce an upward sloping supply curve.
		* High market efficiency arises when buyers pay less than their internal values and sellers try to cover costs.

* Simulating markets 
	* The **Albin-Foley Model** which involves distributed decentralized bilateral [[Trade|trading]] with local price formation
	* The **Sugarscape Model** which extends the Albin-Foley model to include heterogeneous agents and changing preferences. 
	* The **Wilhite Model** which adds network topologies.

* [[Auction Theory|Auctions]]

* [[Bipartite Graph|Bipartite Matching]]

* [[Game Theory]]
	* ABM has the advantage that it can include facets such as memory and network structures.  It also relaxes the assumption of rationality 
	* ABM models allow for ergodicity that is only apparent at large time scales.
	* The **El Farol Model** - an ABM model for learning inductive rather than rational behavior. Agents with heterogeneous preferences determine whether or not to attend a club -- with a club that is too full or too empty being undesirable. *Agents arrive at the Nash equilibrium without trying to compute it*.

* Simulating [[Firms, Production and Externalities|firms]],  organizational behavior, and firm operations. This also includes
	* [[Supply Chain Management|Supply Chain Management]]
	* Customer Behavior
	* Product and Information Diffusion
	* E-Commerce
	* [[Manufacturing|Manufacturing Logistics]]
	* Hierarchy Dynamics

* Studying [[Labor Market Theory|Labor Markets]]. 
* Studying the [[Financial Market|Financial Market]]
	* Stocks trading and analysis of the Stock market. 
	* The **Santa Fe Stock Market Model** - simulates investors choosing between  a stock or a bond. Agents had brains powered by machine learning. The goal was to understand the volatility of the stock market.
	* Modeling systemic risk in the financial market.
	* Diffusion
	* Policies and interventions for the financial market. 

* Studying [[Macroeconomics|Macroeconomics]]
	* It is possible to simulate macroeconomic phenomena using microeconomic dynamics.
	* Some applications:
		* Barter and Trade dynamics.
		* [[Money]] dynamics
		* [[Macroeconomic Policy|Fiscal]] policies. 
		* Taxation policies
		* Modeling Wealth inequality

* Environmental Economics -- assessing the impact of economic processes to the environment 

# Research
* [^Axtell_2022] provides a survey of the use of Agent-Based Modeling Techniques in [[Economics|Economics]] and Finance. 

[^Axtell_2022]: Axtell  and Farmer (2022) [Agent-Based Modeling in Economics and Finance](https://oms-inet.files.svdcdn.com/staging/files/JEL-v2.0.pdf)


* [^Steinbacher_2021]  gives a review on ABM with regards to modeling economic behavior 
	* In the context of computational social science, ABM can be characterized as having the following components 
		* Agents have *psychological traits* (heuristics) and socio-demographic *attributes*. These traits could be based on real world data. 
		* Agents operate on an *environment* where they interact with others. 
		* Agents operate under *rules of interactions* and decision making processes are deduced from social and psychological theories. 
		* *Macro-level structure* that [[Emergence|emergent]] as a consequence of micro-level behavior. Tuning the micro helps understand the macro. 
	* *Data driven ABMS are initialized and validated using data* from surveys, digital media, social [[Network Science|network data]], crowd sourced data, digital sensors and information networks, existing databases, census data, and urban data. 
	* *Heuristics can be used to model [[Human Biases|human behavior]]*. Agents in the system can either be "automatic" (i.e., have no cognitive function) or learn from the environment. 
		* Behavioral heuristics underutilize the possibilities offered by expectation formation theory -- that is, heuristics based on the expectation of a variable (such as price). 
		* Heuristics may provide a more accurate and robust tool for modeling action also within an uncertain environment than sophisticated techniques.
	* Besides modeling the behavior of agents we have to model *realistic networks of interactions* where these are relevant for the dynamics of the system
		* Large scale networks could be used to study cascades via **cascade models**.
		* ABM can be used to study *the extent to which network structure influences macroscopic outcomes. However, they do not answer whether the proposed structures are found in reality, how they formed, or how they might develop*
		* Modeling could be done using data or analyzing the dependencies of real world markets. 
	* *ABMs can be used to explain the stability of a financial system* 
		* Early work has focused on micro-structures such as transactions and trading 
		* They can help in identifying mechanisms that lead to instabilities, and to evaluate policies to mitigate them. 
		* They can also be used for risk analysis and to the extent that cascades in the system are affected by the network's structure. 
		* ABM could be used to test the effectiveness of micro and macroprudential policies to counteract banking crises.
		* *ABM can be used to generate a dataset to evaluate the consequences of policy*.
	* ABMs have so far mostly been used to generate insights and qualitative descriptions of scenario that may occur rather than quantitative forecasts.
	* *ABM can be extended to apply to heterogeneous agents* -- that is, agents that behave differently and not necessarily rationally .
	* *ABM can be used to explain experimental results*. 
	* *ABMs can be used to generate priors* to produce scenarios for machine learning algorithms in a semi-supervised manner to reduce errors and prevent the amplification of distortions
 
	[^Steinbacher_2021]: Steinbacher et al. (2021) [Advances in the Agent-Based Modeling of economic and social behavior](https://link.springer.com/article/10.1007/s43546-021-00103-3)

# Links 
* [[Economics]]
* [[Machine Learning]]

* [[Computational Macroeconomics]]