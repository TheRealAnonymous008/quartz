# ABM
* Medium and large Macroeconomic ABMs (MABMs) typically feature the following agent types: [[Consumer Behavior and Transactions|Households]] $(H)$, [[Firms, Production and Externalities|Firms]] $(F)$ and [[Financial Market|Banks]]. $(B)$
* MABMs involve five markets.
	* Consumption goods (C-goods)
	* Capital or investment goods (K-goods)
	* [[Labor Market Theory|Labor]] $(N)$
	* Credit / Liabilities$(L)$
	* Deposits / Assets $(A)$

## Households
* MABMs consist of a population of $H$ households. 
	* Households purchase $C$-goods.  
	* Generally, households do not go into debt.
	* Households can be [[Network Science|linked]] to firms  via trading relationships where they buy $C$-goods from and work for. 
	* Households may be capitalists who re-capitalize a defaulting firm to make it survive.

* Consumption is done in two stages
	* Determine the consumption expenditure $C_{ht}$
		* The budget can be specified as 
		  $$
		  C_{ht} = c_h W_{ht}^h + c_f W_{ht}^f
		  $$
		  Where $W_{ht}^f$ is the financial wealth, $W_{ht}^h$ is the human capital and $0<c_h,c_f<1$ are weights. 
		* By definition
		  $$
		  \begin{split}
		  W_{ht}^f &= \hat{R} W_{h,t-1}^f + Y_{ht} - C_{ht} \\
		  S_{ht} &= W_{ht}^f - W_{ht}^{f-1}
		  \end{split}
		  $$
		  Where
		  $R=1+r$ is the gross nominal interest rate, 
		  $Y_{ht}$ is the income of household $h$
		  $C_{ht}$ is the total consumption of household $h$
		  $S_{ht}$ is the total saving of household $h$. 
		* Savings is therefore defined as 
		  $$
		  S_{ht} = Y_{ht} + (r-c_f)W_{h,t-1}^f + c_hW_{ht}^h
		  $$
		* We can extend the above to also account for past incomes and financial wealth.
		* We can also extend them to account for expected future incomes and human wealth. 
		* $c_f$ and $c_h$ can also be functions of past income and wealth. This mimics what is observed [[Behavioral Economics|empirically]] where people reduce their spending when wealth is low.

	* Determine how to allocate $C_{ht}$ for each $C$-good. 
		* Generally *this choice is influenced by the relative prices of the goods*
		* Choosing can be done via a multinomial logit distribution or via a search.
		* Alternatively, it can incorporate network data. Households may only buy from firms they are connected to or these firms' immediate neighbors.
		* [[Information Theory|Information]] can also be incorporated in the search process.

* Active households supply labor to the [[Labor Market Theory|Labor Market]], while inactive households do not.
	* Households may have specific labor types offered and $C$-products preferred.  Typically we assume these are different and all households produce one unit of labor. 
	* Employed households earn wages. 
	* Unemployed households may earn an unemployment subsidy.
	* Households can be (temporarily or permanently) firm owners who receive dividends 
	  $$
	  \text{
	  Income = Wages + Dividends 
	  }
	  $$ 
	* Households may also look for new jobs (i.e., jobs which offer higher wages). 

* Unspent income is saved to generate financial wealth (typically only bank deposits)
	* Modeling a portfolio choice for each households' savings may be complex.

## Firms
* The MABM system consists of $F$ firm which are either $C$-firms (produces consumption goods) or $K$-firms (produces capital good)

* $C$-firms demand labor and $K$-goods to [[Firms, Production and Externalities|produce]] $C$-goods for consumption.
* Firms set the quantity and price of the goods they sell. 
	* Buyers do not have information on all prices and quantities sold by firms .
* Firms set the demand for $K$-goods and labor based on the planned scale of activity.
	* *Crucially, firms do not have perfect information on the demand for the goods they offer*.
		* Firms only observe the actual demand after they have sold their goods.
		* *Uncertainty in the market forces firms to adapt*.
	* The demand for $K$-goods by a $C$-firm is determined by production requirement (i.e., its investment) 
		* Actual future developments of the $K$-goods markets are unknown to the firms.
	* [[Material Requirements Planning|Capital in stock is used first]]. 
	* In some cases, investment is driven by long run production requirements which may not be useful for short run demand peaks.
	* Firms whose labor is insufficient to meet demand will post job openings and a wage offer. 

* More formally, firms start with an initial price and quantity $(P_{it}, Y_{it})$  defined as the status quo.
	* When all transactions are made at the end of period $t$, the actual sales is observed given by 
	  $$
	  Q_{it} = \min (Y_{it}, C_{it})
	  $$
	  Where $C_{it}$ is the quantity soled. 
		* Firms predict the expected demand. 
		* If $C_{it} < Y_{it}$ the firm holds an inventory consisting of a buffer stock of finished goods. The inventory held is 
		  $$
		  \Delta_{it} = Y_{it} - C_{it}
		  $$
		* Inventory shortages and excesses are determined either using an interval $\Delta_{it}^m,\Delta_{it}^M$ or using a single threshold $\Delta_{it}^\ast$. 
		* Positive inventory is always involuntary and corresponds to a negative prediction error.
		* Negative inventory means unsatisfied customers.
		* The target inventory is determined using a target inventory-to-sales ratio 
		  $$
		  \Delta_{it}^\ast = \delta^\ast Y_{it}
		  $$
* The firm receives two market signals.
	* An excess or shortage of inventory with respect to the target. *This signal corresponds to estimates for $Y$* 
	* The relative price (between the firm's price and the average market price).*This signal corresponds to estimates for $P$. 
	* Let $P_t$ denote the average price. The estimates are adjusted as follows (see [[Optimization Algorithms in Machine Learning|here for something similar]]). 
		* Production plans go up if there is a shortage of inventories and the current price is greater than the competitor's prices.
		* Production plans go down if there is an excess of inventories and the current price is lower than the competitor's prices.
		* Prices go up if there is a shortage of inventories and the current price is smaller than the competitor's price.
		* Prices go down if there is an excess of inventories and the current price is greater than the competitor's price

|                | $\Delta_{it} < \Delta_{it}^m$       | $\Delta_{it} > \Delta_{it}^M$       |
| -------------- | ----------------------------------- | ----------------------------------- |
| $P_{it} < P_t$ | $P_{i,t+1}^\ast = P_{it}(1+\eta^p)$ | $Y_{i,t+1}^\ast=Y_{it}(1-\eta^y)$   |
| $P_{it}>P_t$   | $Y_{i,t+1}^\ast=Y_{it}(1+\eta^y)$   | $P_{i,t+1}^\ast = P_{it}(1-\eta^p)$ |


* We may also consider [[Factory Dynamics|Factory Dynamics]] in particular by considering utilization *if capacity is not fully utilized, only a fraction of the capital stock is used in production*.
	* We can further divide $K$-goods (vintages) based on what they produce (i.e., certain machines can only make certain things).
	  
	  In such a case, firms choose vintages based on the ratio of expected future productivity of each vintage relative to the price of the tool of that vintage.
	* This necessitates specifying the production function.
	* *Demand for labor, capital, and credit are determined using production goals*

* In addition to deciding prices and production goals, firms may also decide on 
	* *Capacity utilization* (for short term demand fluctuations); and 
	* *Investment* (for long-term production goals)

* The demand for credit is more formally determined as follows. If $X_{ft}$ is the operating cost of the firm and $M_{f,t-1}$ is the internal funds. THen:
	* If $M_{f,t-1} > X_{ft}$, internal funds can finance the operation costs.
	* If $M_{f,t-1}<X_{ft}$, there is a **financing gap**. Banks fill this financing gap via loans. A general specification for the financing gap is
	  $$
	  F_{ft} = \max(0, w_{ft}N_{ft} +  P_{t-1}^K I_{ft} - M_{f,t-1})
	  $$
	  Where the first term corresponds to labor costs ($w_{ft}$ for wages and $N_{ft}$ number of laborers).
	  
	  The second term corresponds to capital costs. $P^K$ denotes the price index for $K$-goods and $I_{ft}$ the investment of the firm on its supplier for $K$-goods.

# Banks
* [[Financial Market|Financial factors]] influence macroeconomic performance primarily *through the assumption of financial frictions* -- that is, we assume the transmission of funds from lenders to borrowers is imperfect. This encompasses the following:
	* *Costly state verification* - Information on the return of investment becomes asymmetric after the investment has been carried out -- entrepreneurs can observe the ROI at zero cost (since they are involved in the project being invested) but banks can only ascertain the true return with a monitoring cost.  
	* *Costly enforcement* - the debt contract itself is costly to enforce. Producers in the financial market are not substitutable therefore lenders run the risk of borrowers running with the money and have to design contracts to minimize loss incurred from this.
	* *Costly bankruptcy* - the burden of bankruptcy is on the borrower since it is the borrower who incurs monetary and reputational costs on default. Thus, to the borrower, there are additional implicit costs when borrowing money. 

* The bank primarily determines the interest rates. 
* Banks accept deposits from people in its sector and extends loans to firm owners.

* Banks are subject to a prudential constraint -- banks must have net worth $E_{bt}$ at least equal to a given fraction of risky assets. $RA_{ht}$. 
  
  The constraint can be specified using the maximum leverage $\lambda_b^M$ where
  $$
  RA_\text{ht} \le \lambda_b^M E_{bt}
  $$

## Policy

* The main challenges for using MABMs for policy design are as follows:
	* Explainability -- can we explain the mechanisms driving the policy's effects using the model.
	* Calibration - MABMs require calibration based on empirical data.

[^dawid_2018] provides a survey of Macroeconomic models and also outlines some of their common features

[^Dawid_2018]:  Dawid and Gatti (2018) [Agent Based Macroeconomics](https://d-nb.info/1151638439/34)

# Links
* [[Macroeconomics]]
* [[Agent Based Modeling]]