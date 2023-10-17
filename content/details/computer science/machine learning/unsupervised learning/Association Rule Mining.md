* [The goal of Rule Mining is to find interesting relations between the variables in large databases, invariant of orders](https://en.wikipedia.org/wiki/Association_rule_learning)
# Key Quantities
Let $X\implies Y$ be a rule.
* **Support** defines the evidence of *how frequent a set of items appears* in the itemset. It is the probability $P(X)$.
	* Thresholding the support lets us define which items appear frequently enough that rules about them are interesting.
	* *Support is a monotonically non-increasing value*. Intuitively, larger item sets of a specific configuration will be less likely to appear than its subsets.
* **Confidence** defines *how likely a rule is true* based on how many times it is found to be true within the item set. It is the probability $P(Y\mid X)$
	* Thresholding the confidence lets us define which rules are interesting enough because the rule holds often.
* **Lift** is used to compare the expected confidence with the actual confidence. It is defined as the quantity $$\frac{P(X,Y)}{P(X)P(Y)}$$
	* A lift $=1$ implies no rule can be drawn since $X$ and $Y$ are independent.
	* A lift $>1$ implies a *dependency* between $X$ and $Y$.
	* A lift $<1$ implies $X$ can *substitute* with $Y$ or vice versa.
* **Conviction** determines the ratio of the expected frequency that a rule makes an incorrect prediction if $X$ and $Y$ were independent, divided by the actual observed incorrect predictions. It is calculated as $$\frac{1-P(Y)}{1-P(Y\mid X)}$$
# Apriori Algorithm
* Identify frequent individual items and extend them to larger and larger item sets as long as they meet a support threshold.
* *It relies on prior knowledge of frequent itemset properties*.
# ECLAT
* **Equivalence Class Transformation**. 
* Rather than explore in a BFS manner as in the Apriori algorithm, it *explores in a DFS manner*, checking larger itemsets first and then using backtracking.
* Since the support is monotonically non-increasing, it helps save on checking the support of some subsets.
# FP-Growth
* First, it counts the support of individual items in the itemset. Items that do not meet the minimum threshold are discarded.
* Then, it *builds a trie out of incoming transactions*. Each item in the trie is sorted by descending order of frequency in the dataset. 
* Unlike, apriori, this has the advantage of *finding all frequent item sets without needing to compare to the original itemset.*. All nodes that remain on the tree are, themselves, frequent item sets.

