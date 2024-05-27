* Inventory plays a key role in the logistical behavior of virtually all manufacturing systems.
	* *There is a tradeoff between replenishment frequency and inventory.*  More frequent replacement means less cycle stock carried.
	* *There is a tradeoff between customer service and inventory*. Under conditions of random demand, higher customer service levels (i.e., fill rates) require higher levels of safety stock.
	* *There is a tradeoff between variability and inventory*. For a given replenishment frequency, if customer service remains fixed (at a sufficiently high level), then the higher the variability the more inventory we must carry.
# Notation
* $t$ - time.
* $T$ - planning horizon
* $I$ - inventory level.

* $D$ - demand 
* $A$ - setup or purchase order cost (per replenishment)
* $Q$ - quantity
* $c$ - unit production cost 
* $c_o$ - cost per unit left over after demand is realized
* $c_s$ - cost per unit of shortage
* $b$ - backorder cost (cost per backorder)
* $h$ - holding cost (cost per unit held)
* $k$ - cost per stockout
* $Y$ - cost function

* $L$ - random variable corresponding to replenishment lead time.
* $l$ - replenishment lead time 
* $D$ - expected demand per year
* $X$ - demand during replacement lead time treated as a random variable.
* $p(x)$ - probability demand, assumed to be discrete but a continuous distribution can be used as well using a density function
* $g(x)$ - probability density function of demand
* $G(x)$ - cumulative distribution of demand during replacement lead time
* $\theta$ - mean demand during replenishment lead time
* $\sigma$ - standard deviation of demand during replenishment lead time

* $r$ - reorder point
* $s=r-\theta$ - **safety stock level**. This pertains to the amount we have when the order arrives. This is the inventory that protects the system from stockouts due to demand fluctuations. 

* $F(Q,r), F(Q)$ - order frequency.
* $S(Q,r), S(Q)$ - fill rate.
* $B(Q.r), B(Q)$ - average number of outstanding backorders
* $I(Q,r), I(Q)$ - average on-hand inventory level 

# Deterministic Models
## Economic Order Quantity Model
* Interest on capital tied up in wages, material and overhead sets a maximum limit to the quantity of parts which can be profitably manufactured at one time; *"set-up" costs on the job fix the minimum.*
* A factory producing various products and switching between products entails a costly setup.
* **Setup Cost** pertains to the sum of labor and material costs to ready the shop to produce a product. 
	* Setup costs may be difficult to estimate and can depend on a lot of factors. [^eoq]
	* Large lots reduce setup costs by requiring less frequent changes. 
	* Small lots reduce inventory by bringing in product closer to the time it is used.

* The following assumptions are made
	* *Production is instantaneous*. There is no capacity constraint and the entire lot is produced simultaneously
	* *Delivery is immediate*. There is no time lag between production and availability to satisfy demand.
	* *Demand is deterministic*. There is no uncertainty about the quantity or timing of demand.
	* *Demand is constant over time*. 
	* *A production run incurs a fixed setup cost*. Regardless of the size of the lot or the status of the factory; the setup cost is the same.
	* *Products can be analyzed individually*. Either there is only a single product or there are no interactions (e.g., shared equipment) between products.

* The model makes use of the following quantities
  
  The total inventory cost is given by the following
  $$Y(Q) = \frac{hQ}{2} + \frac{AD}{Q} + cD$$
	* The first term corresponds to the average holding cost. 
	* The second term corresponds to the setup cost to hold the lots needed to satisfy demand.
	* The third term corresponds to production cost. 
	  

* The **Economic Order Quantity** is the value of $Q$ that minimizes $Y(Q)$. It is derived using [[Differential Calculus]]. It is notated $Q^\ast$.
  
  $$
  Q^\ast = \sqrt{\frac{2AD}{h}}
  $$

* We can extend this model to the **Economic Production Line** model in cases where there is a finite but constant and deterministic production rate. 

### Key Insights
* *There is a tradeoff between lot size and inventory*. There are diminishing returns to cost if we add additional inventory. 
* *Holding and setup costs are fairly insensitive to lot size.* if, for any reason, we use a lot size that is slightly different than Q*, the increase in the holding plus setup costs will not be large. The sensitivity of going from $Q_0$ to $Q_1$ is given as
  
  $$
  \frac{Y(Q_1)}{Y(Q_0)} = \frac{1}{2} \left(\frac{Q_1}{Q_0} + \frac{Q_0}{Q_1}\right)
  $$
* Because demand is deterministic, *order interval is completely determined by order quantity*. The optimal order interval $T=\frac{Q}{D}$ is given as 
  
$$
T=\sqrt\frac{2A}{hD}
$$ 
* The error in the holding plus setup cost resulting from using the optimal power-of-2 order interval instead of the optimal order interval is guaranteed to be no more than six percent. [^eoq_2]


[^eoq]: If setup cost is tied to purchasing orders, then this limitation does not hold. 
[^eoq_2]: This follows by considering $T_1=\sqrt{2} T_0$ and get the sensitivity. $\sqrt{2}$ arises due to the fact that $T$ lies in the interval $[2^m,  2^m\sqrt 2]$ or $[2^m\sqrt{2}, 2^{m=1}]$..  

## Wagner-Whitin Model
* The problem of dynamic lots arises due to fluctuations in demand which make classical approaches like EOQ suboptimal. 
* The **Wagner-Whitin Model** considers the problem of determining production lot sizes *when demand is deterministic but time-varying and all the other assumptions for the EOQ model are valid*

* Note that we perform discretization rather than deal with continuous time.
  
  $I_t$ is the inventory left over defined as follows
  
  $$
  I_t = I_0 + \sum_{j=1}^{t-1} Q_t - \sum_{j=1}^{t-1} d_j.
  $$
  We assume $I_t\ge 0$ for all $t$. 

* The **lot-for-lot rule** means we perform lot sizing based on what is required in each period.  This policy implies we will produce and pay a setup cost in every period. 
* The **first order quantity** means we produce a fixed amount each time we perform a setup. Here, we produce more than is required (and so pay more inventory cost)

* *Key insight*: If we produce items in period $t$ for use to satisfy demand in period $t+1$, then it cannot be economical to produce in period $t+1$. Either we produce all of period $t+1$'s demand in period $t$, or all of it in $t+1$. *Mixing is not optimal*. 
  
  This leads to the **Wagner-Whitin property** -- under an optimal lot-sizing policy either the inventory carried to period $t+1$ from a previous period will be zero or the production quantity in period $t+1$ will be zero. 

* The **Wagner-Whitin algorithm** iterates through time, and proceeds as follows. It is a [[Algorithms|dynamic programming algorithm]]:
  
  Let
  $$
  F(t) =
  \begin{bmatrix}
  A_t + F(t-1) \\
  \min_{1\le j <t} \left[ A_j  + \sum_{h=j}^{t-1} \sum_{k=h+1}^t h_h d_k + F(j-1) \right]
  \end{bmatrix}
  $$
  
  Which denotes the minimal cost for periods $1, \dots, t$.  
  
  We use the **Planning Horizon Theorem** which states that, if at period $t^\ast$, the minimum in $F(t)$ occurs for $j=t^{\ast\ast} \le t^\ast$, then in periods $t>t\ast$, it is sufficient to consider only $t^{\ast\ast}\le j\le t$.  [^planning_horizon]
  
  If $t'=t^{\ast\ast}$, then it is sufficient to consider all policies such that $Q_{t'}>0$. 
  
  We proceed as follows
	* Consider the policies for ordering periods $t^{\ast\ast}\in [1,\dots, t^\ast]$. Fill demands $d_t, t=t^{\ast\ast}, t^{\ast\ast} + 1, \dots, t^\ast$ by this order. 
	* Add $H(Q_{t^{\ast\ast}}) \ \ A_{t^{\ast\ast}} + h_{t^{\ast\ast}} I_{t^{\ast\ast}}$ to the costs of acting optimally for periods $1,\dots,t^{\ast\ast} - 1$ determined by the previous iteration of the algorithm
	* From these $t^\ast$  alternatives, select the minimum cost policy for periods $1$ through $t^\ast$.
	* Proceed to period $t^\ast + 1$ or stop for $t^\ast = N$. 

[^planning_horizon]: The intuition for this is as follows -- if at  the current time step we achieve the minimum cost, then we know that the previous periods do not have minimum cost, otherwise we would have labelled any one of them as the minimum first.  Hence, for subsequent periods, we do not need to consider anything but the current minimum period $t^{\ast\ast}$ and beyond.

* *The Wagner-Whitin model assumes setup costs known in advance, which may not necessarily be true.*
* It also assumes deterministic production which discounts variance and uncertainties. *The optimal results in the Wagner-Whitin algorithm need to be adjusted for real world use cases*.
* It assumes that products do not share common resources, which may be violated.
* The Wagner-Whitin property may not hold in practice due to real world constraints. 

# Statistical Models 
* We make use of [[Probability and Statistics]] to account for a stochastic demand. This problem can be broken down into two parts
	* Determining **order quantity** - the amount of inventory that will be purchased for each replenishment
	* Determining **reorder point** - the inventory level at which replenishment will be triggered. 

## Newsvendor Model
* We are only interested in a single replacement.
* *Assume*: the following
	* Products are separable -- they have no interactions or shared resources.
	* Planning is done for a single period [^newsvendor]. 
	* Demand is random, characterized only with a probability distribution.
	* Deliveries are made in advance of demand.  All stock ordered or produced is available to meet demand.
	* Costs of overage or underage are linear. The charges for having too much or too little inventory is proportional to the amount of the overage or underage

[^newsvendor]: Similar to [[Markov Processes in Machine Learning]]

* The expected cost as a function of production quantity is given as the sum of the costs for overage  (first term) and underages (second term)
  
  $$
  Y(Q) = c_o\int_0^Q (Q-x) g(x) \ dx + c_s\int_0^Q(x-Q)g(x) \ dx
  $$
  
  The goal is to find the minima of the above. [^newsvendor_2] which evaluates to $Q^\ast$ such that 
  
  $$
  G(Q^\ast ) = \frac{c_s}{c_o + c_s}
  $$
  
[^newsvendor_2]: We apply [[Differential Calculus|Leibniz's Integral Rule]] for this. 

* In an environment of uncertain demand, the appropriate production or order quantity depends on both the distribution of demand and the relative costs of overproducing versus underproducing.
* If the demand is normally distributed, then increasing variability of demand will increase the production or order quantity if $G(Q^\ast)>0.5$ and decrease it otherwise. 

## Base Stock Model
* We are interested in a situation where inventory is replenished one unit at a time as random demand occurs. The goal is then, to determine the reorder point 
* The **base stock level** pertains to the  target inventory level set for the system (i.e., how much stock must the system carry to meet demand). 

* *Assume*:
	* Products are separable -- they have no interactions or shared resources.
	* Demands occur one at a time, no batch orders.
	* Unfilled demand is backordered -- no loss in sales as a result.
	* Replenishment lead times are fixed and known -- there is no randomness in delivery lead times.
	* Replenishments are ordered one at a time. There is no setup cost or constraint on the number of orders placed (i.e., no reason to have batch replacement). 

* We use the following notation

* **On-hand** inventory represents the physical inventory in stock. **Inventory Position** represents the balance of on-hand inventory, backhand orders, and replenishment orders
  
  $$
  \text{inventory position} = \text{on-hand inventory} - \text{backorders} + \text{orders}
  $$
  
  Under a base stock policy, the inventory position is $R$. 

* The **fill rate** is the fraction of orders filled from stock. Note that the only way the order can arrive after the demand for it has occurred is if $X\ge R$. We, therefore have
  
  $$
  S(R)=G(R-1) = G(r)
  $$
* The number of orders is equal to the number of demands that have occurred during the last $l$ time units [^base_stock]. The **backorder level** is given by
  
  $$
  B(R)= \sum_{s=R}^\infty (x-R)\ o(x)=  \theta -\sum_{x=0}^R [1-G(x)]
  $$

* The **inventory level** is given, then, by 
  $$
  I(R)=R-\theta + B(R) 
  $$


[^base_stock]: This is a [[Loss Function]]. 

* The higher the mean demand during replenishment lead time, the higher the base stock level required to achieve a particular fill rate. 
* Higher $\sigma$ means a larger $r$ to achieve a given fill rate.
* Since carrying a unit of backorder is typically more costly than carrying a unit of inventory, it is generally the case that the optimal base stock level is an increasing function of demand variability.

* The end goal is to minimize cost
  
  $$
  Y(R) = \text{holding cost} + \text{backorder cost} = h(R-\theta) + (b+h) \  B(R)
  $$
  
  Which is achieved by solving for 
  $$
  S(R^\ast ) = G(R^\ast) = \frac{b}{b+h}
  $$
  *The stock level should be that where the fill rate is given by the above ratio*.

* Base stock levels in multistage production systems are very similar to kanban systems, and therefore the above insights apply to those systems as well.

## $(Q,r)$ model
* We are interested in a case where inventory is monitored continuously, and demands (possibly in batches) occur randomly. When the inventory reaches or goes below $r$, an order of size $Q$ is placed. 
  
  After a lead time of $l$ during which a stockout might occur, the order is received. 

* The *assumptions* are similar to the [[#Base Stock Model]] except we allow replenishment quantities greater than $1$. 
	* There is a fixed cost associated with replenishment order
	* There is a constraint on the number of replenishment orders per year
* $Q$ is the **replenishment quantity** which affects **cycle stock** -- inventory held to avoid excessive replenishment costs.
* $r$ is the **reorder point** which affects safety stock

* The problem is a framed with two objectives, combining [[#Economic Order Quantity Mode|EOQl]] and [[#Base Stock Model]]. 
  
  $$
  \begin{split}
  \min_{Q,r} \left(\text{fixed setup cost} + \text{backorder cost} + \text{holding cost} \right)  \\
  
  
  \min_{Q,r} \left(\text{fixed setup cost} + \text{stockout cost} + \text{holding cost} \right)  
  \end{split}
  $$
	* Backorder cost assumes a charge per unit time a customer order is unfilled.
	* Stockout cost assumes a fixed charge for each demand not filled from stock.

* We can setup the frequency of replenishment orders as 
  $$
  F(Q,r) = \frac{D}{Q}
  $$
  *The fixe setup cost then becomes $F(Q,r) \cdot A$. *

* *The stockout cost is computed by considering the long term expected number of stockouts*. Similar to the Base Stock model, since all outstanding orders will have arrived within replenishment lead time, the probability of a stockout becomes the probability that the demand exceeds the current inventory position $x$. 
  
  $$
  P(X\ge x) = 1-G(x-1)
  $$
  
  The total stockout cost then becomes [^qr_model]
  $$
  S(Q,r) = \frac{1}{Q}\sum_{x={r+1}}^{r+Q} G(x-1) = 1- \frac{1}{Q}\left[B(r)-B(r+Q)\right]
  $$
  This expression is difficult to compute, so we can approximate it. 
	* The **Base Stock / Type I service approximation** is the continuous demand base stock formula for fill rate given by 
	  
	  $$
	  S(Q,r) \approx G(r)
	  $$
	  This is an underestimation of the true fill rate since we take the smallest term in the original stockout expression

	* The **Type II Service approximation** is found by ignoring the second term of the original fill rate formula 
	  
	  $$
	  S(Q,r) \approx 1-\frac{B(r)}{Q}
	  $$

[^qr_model]: The approximation with $B(R)$ follows from using the backorder level function (see [[#Base Stock Model]]) which is expressed in terms of $G$. 


* *The backorder cost is computed using the average backorder level, computed similarly to the average fill rate* 
  
  $$
  B(Q,r) = \frac{1}{Q} \sum_{x=r+1}^{r+Q} B(x) 
  $$
  This can be approximated using 
  $$
  B(Q,r) \approx B(r) 
  $$


* *The holding cost is approximated using the average net inventory and treating demand as deterministic*. 
  
  Average inventory is given by
  $$
  I(Q,r) \approx \frac{(Q+s + (s+1))}{2} = \frac{Q+1}{2} +r-\theta 
  $$
  The inventory at any point in a replacement cycle ranges from $Q+s$ to $s+1$.
  
  The inventory cost is then
  
  $$
  I(Q,r) =\frac{Q+1}{2} + r-\theta + B(Q,r)
  $$

* *With the above formulations for cost, we can perform optimization using either analytical (difficult), heuristic, or computational methods*.   
	* For the backorder cost approach, we optimize
	  $$
	  Y(Q,r) =\frac{D}{Q}A + bB(Q,r) + hI(Q,r)
	  $$
	  Using our outlined approximations, we get 
	  
	  $$
	  \begin{split}
	  Q^\ast &\approx\sqrt{\frac{2AD}{h}} \\
	  G(r^\ast) &\approx \frac{b}{b + h}
	  \end{split}
	  $$

	* For the stockout cost approach, we optimize
	  
	  $$
	  Y(Q,r) = \frac{D}{Q}A + kD[1- S(Q,r)] + hI(Q,r)
	  $$
	  
	  This gives the approximations outlined above
	  $$
	  \begin{split}
	  Q^\ast &\approx \sqrt{\frac{2AD}{h}} \\
	  G(r^\ast) &\approx \frac{kD}{kD + hQ}
	  \end{split}
	  $$
	  
	  Note that quantity plays a role, since a larger quantity implies less frequent replenishments (hence a smaller reorder point)

* *We can model lead-time variability* to account for circumstances where replenishment time varies (which it does in practice). This variability inflates the standard deviation of demand due to being another source of variability.
  
  In this case, the variance of $X$ is modified
  
  $$
  \text{Var}[X]= l\sigma_D^2 + d^2 \sigma^2_L
  $$
  Where $\sigma_D$ and $\sigma_l$ are the standard deviations of demand and lead time respectively. 


* The key *Insighst* we observe in this model are as follows
	* Cycle stock increases as replenishment frequency decreases
	* Safety stocks provide a buffer against stockouts. 
	* If $Q$ is large, then stock level seldom reaches reorder point and has few opportunities for stockouts.
	* If $Q$ is small, then stock level frequently reaches the reorder point. 
	* Increasing the average demand $D$ tends to increase the optimal order quantity $Q$. 
	* Either high demand or long replenishment lead times will tend to require more inventory in stock
	* A highly variable demand process typically requires more safety stocks than a very stable one.
	* Increasing the holding cost (i.e., via increased pricing or interest) will decrease both optimal replenishment quantity and reorder point. The more expensive it is to hold the inventory, the less we should hold. 

# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 2

* [[Manufacturing]]
* [[Factory Dynamics]]
* [[Scarcity, Supply, and Demand]]