# Generalization Error 
* The **generalization error** of $f$ with the loss function $L$ is denoted as 
  $$
  R[p, f] =\int_{X\times Y} {L(y, f({x})) \space  p({x}, y)\space d{x}\space dy}
  $$
  
* This serves as a metric to determine how a model performs on unseen data. A high generalization error may indicate that the model is overfitting. 
* The generalization error is typically not calculated since the probability distribution is unknown. *We, instead, choose to evaluate over a set of unseen samples in the same vein as training error but using unseen data* 
  $$
  {R_n{(X,\vec{y}, f)} =\frac{1}{n}\sum_{i=1}^n L({\vec{y}^{(i)}, f(X^{(i)}))}}
  $$
  We say that the model **generalizes** if $R_{emp}(X, \vec{y},f)$ converges.  Namely by asserting that 
  $$
  {\lim_{n\to \infty} {R(X, \vec{y}, f) - R_n(X, \vec{y}, f)} = 0}
  $$

* The **Empirical Error**, denoted $\epsilon_\mathcal{D}$ is defined as the proportion of incorrectly classified values to the size of the dataset 
  
  $$
  \epsilon_{\mathcal{D}} = \frac{1}{n} \sum_{i=1}^n [y^{(i)} \ne f(x^{(i)})]
  $$

* The **training error** of the function $f$ using the loss function $L$ is denoted as $R_{emp}(X, \vec{y}, f)$: and is defined as 
  
  $$
  {R_{emp}{(X,\vec{y}, f)} =\frac{1}{n}\sum_{i=1}^n L({\vec{y}^{(i)}, f(X^{(i)}))}}
  $$

* The  **generalization gap** is defined as the difference between the training error and the generalization error or any estimate thereof.
  
  $$
  GG=|TE-GE|
  $$
  
# Empirical Risk Minimization
* We reframe the problem as follows. 
  Let $L(y,\delta(x))$ be a loss function with $y$ being the true response, and $\delta(x)$ the prediction given the input $x$. 
  
  Thus, we are *predicting observable quantities*
* The **risk** is now defined as 
  $$
  \begin{split}R(p_\ast,\delta)&=\mathbb{E}_{(x,y)\sim p_\ast}\left[L(y,\delta(x)\right] \\ 
  &= \sum_x\sum_yL(y,\delta(x)) p_\ast(x,y)
  \end{split}
  $$
  Where $p_\ast$ represents the true distribution approximated by real data through the empirical distribution.
  
  We can define something similar by replacing the summations with integrals. 
  
  * The **Risk Identity** is defined as  (for continuous case) 
    $$
    \int\int L(f(x),y) \ p(y|x) p(x) \ dxdy = \int\int L(f(x),y) q(y|x) q(x) \frac{p(x)}{q(x)} \ dxdy
    $$
    
  
* The **empirical risk** is then defined as 
  $$
  \begin{split}R_\text{emp}(\mathcal D, \mathcal D) &=R(p_{emp}, \delta) \\ &= \frac{1}{N}\sum_{i=1}^N L(y_i,\delta(x_i))\end{split}
  $$
  That is, it is the risk when we use the empirical distribution instead of the true distribution (in other words, average loss over the dataset).
* The goal, then becomes to minimize the empirical risk.
### Regularization
* Minimizing the empirical risk will usually result in overfitting. *This is because of our assumption that the true distribution is equal to the empirical distribution* (which is not necessarily true due to sampling errors)
* Hence we **regularize** by adding a penalty $C$ weighted with $\lambda$ 
  $$
  R'(\mathcal D, \delta)= R_{\text{emp}} (\mathcal D, \delta) + \lambda C(\delta)
  $$
  
### Choosing $\lambda$
* We cannot use the training set to approximate the true risk. 
* We use the **structural risk minimization principle**. Where 
  $$
  \hat{\lambda}=\underset{\lambda}{\text{argmin}} \ \hat{R}(\hat\delta_\lambda)
  $$
  Where $\hat R(\delta)$ is an estimate of the risk.
* We model the uncertainty of our estimates via standard error. The **one-standard error rule** is a heuristic where we choose the simplest model (Occam's razor) that is no more than one standard error from the mean.
#### Cross Validation
* Let
  $N=|\mathcal D|$ be the data number of data cases.
  $\mathcal{D}_k$ be the kth data fold, and all the other data by $\mathcal{D}_{-k}$. 
  $\mathcal{F}$ be a learning algorithm which outputs a parameter vector given a dataset and some model indices (i.e., hyperparameters). 
  $$
  \hat\theta_m=\mathcal F(\mathcal D,m)
  $$
  
  $\mathcal{P}$ be a prediction function that takes an input and a parameter vector and returns a prediction  
  $$
  \hat y=\mathcal P(x,\hat\theta)
  $$
  The fit predict cycle is denoted as 
  $$
  f_m(x,\mathcal D)=\mathcal P(x,\mathcal F(\mathcal D, m)))
  $$
  
* The $K$-fold CV estimate of the risk is defined as 
  $$
  R(m,\mathcal D, K)=\frac{1}{N}\sum_{k=1}^N\sum_{i\in \mathcal D_k} L(y_i, \mathcal{P} (x_i, \mathcal F(\mathcal D_{-k}, m)))
  $$
  
* We then call the fitting algorithm once per fold. Let 
  $$
  f^k_m(x)=\mathcal P (x,\mathcal F(\mathcal D_{-k},m)))
  $$
   be the function that was trained on all data except for the test data in fold $k$. The estimate then becomes 
   $$
   R(m,\mathcal D, K)=\frac{1}{N}\sum_{i=1}^NL(y_i , f_m^{k(i)}(x_i))
   $$
   Where $k(i)$ is the fold in which $i$ is used as test data.
* In summary: divide the dataset into $K$ folds, each fold will be used as a validation set for one of $K$ models not trained on this data. 
	* The empirical risk is then the average loss across all $K$ folds.
* If $K=N$, this is **leave one out cross validation**. 

#### Theoretical Upper Bounds
* *Murphy 6.5.1* For any data distribution $p_\ast$, and any dataset $\mathcal{D}$ drawn from $p_\ast$, the probability that our estimate of the error rate will be more than $\varepsilon$ wrong in the worst case, is upper bounded as follows: 
  $$
  P\left(\max_{h\in\mathcal{H}}|R_{emp}(\mathcal{D},h)-R(p_\ast,h)|>\epsilon\right)\le2 \dim(\mathcal{H})e^{-2|\mathcal{D}|\varepsilon^2}
  $$
  
  Where $\mathcal{H}$ denotes the (finite) hypothesis space so that $\dim(\mathcal H)=|\mathcal{H}|$ 
	* Training error increases with a larger hypothesis space, and decreases with a larger dataset. *This is the key insight of statistical learning theory*. 
	* For infinite dimensional hypothesis spaces, we use the **Vapnik Chervonenkis dimension** in place of $|\mathcal{H}|$

#### Relation with Population Error 
* The **population error**, denoted $\epsilon(f)$. It is the *expected fraction of example in an underlying population* characterized by probability density $p(x,y)$ for which the model disagrees with the ground truth 
  
  $$
  \epsilon(f)=\int\int[f(x)\ne y]\ p(x, y) \ dxdy
  $$
  
* By the Central Limit Theorem, we can show that the empirical error approaches the population error at a rate of $\mathcal{O}(1/\sqrt{n})$.
  
* The asymptotic standard deviation of the estimate cannot be greater than $\sqrt{0.25/n}$ by the central limit theorem.
	* This follows by reparameterize it by the probability that it gives $1$ (i.e., $\epsilon(f)$). Thus, we get the parameterization 
	  $$
	  \epsilon(f)\left(1-\epsilon(f)\right)
	  $$
	  Which has the highest variance when $\epsilon(f)=0.5$.
# Confusion Matrices
* See [Here](https://en.wikipedia.org/wiki/Confusion_matrix) for all the entries in the confusion matrix (i.e., TPR, FPR).
* The **Receiver Operating Characteristic** curve shows the $FPR$ and $TPR$ as a function of the classification boundary $\tau$.
	* Good classification systems will hug the left axis and then the top axis.
	* The quality is quantified as **Area Under the Curve** (AUC). Higher = better. 
	* The **Equal Error Rate** is the value of $\tau$ such that $FPR=FNR$. Lower = better.

### Accuracy
* **Accuracy** measures the proportion of correct predictions over all classifications performed
  
  $$
  \text{accuracy} = \frac{\text{correct classifications}}{\text{all classifications}}
  $$

* Although accuracy can give an idea for a model's performance, *it may not necessarily reflect whether or not the model has truly learned patterns in the data*.
* It is also prone to the fact we weight each correct classification correctly, which *assumes that the population proportion for each class is roughly equal* ,which does always not hold


### Precision-Recall
* The **precision** measures what fraction of positive labels are actually positive (i.e. $\frac{TP}{TP + FP}$)
* The **recall** measures what fraction of the ground truth positive samples are detected (i.e., $\frac{TP}{TP + FN}$)
* The precision-recall curve can be plotted as a function of $\tau$. Better classifiers hug the top right.
* The **average precision at $K$** is the precision at a fixed recall level.
* The **F1 score** combines precision and recall. It is the harmonic mean of the two 
  $$
  F_1=\frac{2}{1/P+1/R}
  $$
  
	* For multi-class classification, we can generalize the $F_1$ score as a **macro-averaged** $F_1$ score defined as the average $F_1$ score where we identify a class $c$ from all other classes. That is $$\frac{1}{C}\sum_{c=1}^C F_1(c)$$
	* Alternatively, we can use a **micro-averaged** $F_1$ score where we pool all counts from each class's contingency table (that is by pooling all $TP, FP$ and $FN$ across all classes)
### Multiple Hypothesis Testing
* *Problem*: We need to classify using multiple hypotheses simultaneously.
* We can minimize the **false discovery rate** defined as 
  $$
  FDR(\tau,\mathcal{D})=FD(\tau,\mathcal{D})/N(\tau,D)
  $$
  
  Where $N(\tau,\mathcal{D})$ is the number of positively classified items and  
  $$
  FD(\tau,\mathcal{D})=\sum_{i}(1-p_i) \mathbb{I}(p_i>r)
  $$
  
  Where $p_i=P(y_i=1\mathcal{D})$ is the prior belief regarding the hypothesis. 
* The **Direct Posterior Probability approach** involves modifying the decision threshold $\tau$.

# Links 
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 5]]
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al]].