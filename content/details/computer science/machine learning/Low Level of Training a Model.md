* If we wish to incrementally add data or remove data without calculating the inverse, we may use the [[Matrix Inversion|Woodbury formulas]] to give a rank $1$ update. For more info. see  [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy 4.3.4.2]]

* Pytorch: Models can be made to run faster and with less memory at the cost of some numerical instability by using `torch.autocast` (to make use of FP16)
	* **Gradient Accumulation** can be used as an approximation to having a higher batch size beyond the one that hardware allows for without OOM-ing.
# Links
* [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy]]