

* [^Siedler_2023] investigates a MARL setup for a cooperative-competitive task (in this case, microplastic cleanup)
	* It makes use of a [[Graph Neural Network|GNN]]-based communication system. 
	* *Limitation*: It's very limited in scope. At best, it illustrates how MARL can be applied to a real world problem.


[^Siedler_2023]: Siedler (2023) [Learning to Communicate and Collaborate in a Competitive Multi-Agent Setup to Clean the Ocean from Macroplastics](https://arxiv.org/abs/2304.05872)



* [^Wang_2022] proposes a [[Transformer Model|Transformer]]-based multi actor-critic framework for active voltage control. It also aims to stabilize the training process of [[MARL Algorithms and Approaches|MARL algorithms]] with a transformer.
	* The network operates on a power distribution network (represented as a graph). 
	* Raw observations are projected into an embedding space. Since it operates on a graph, it makes use of the adjacency matrix as additional positional information.  This information is then fed to a transformer
	* A [[Recurrent Neural Network|GRU]] is used to project the representation to an action. 
![[TMADDPG.png]]
<figcaption> Transformer-Based MADDPG. Image taken from Wang, Zhou Li (2022) </figcaption>

[^Wang_2022]: Wang, Zhou, and Li (2022) [Stabilizing Voltage in Power Distribution Multi-Agent Reinforcement Learning with Transformer](https://arxiv.org/pdf/2206.03721)



