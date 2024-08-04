* **Quality** can be broadly defined using the following product-oriented definitions
	* **Transcendent** - quality refers to an innate excellence which is not a specific attribute of either the product or the customer, but is a third entity altogether.  *I know it when I see it*
	* **Product based** - quality is a function of the attributes of the product, *More is better*. 
	* **User based** - quality is determined by how well customer preferences are satisfied. *Beauty is in the eye of the beholder*.
	* **Manufacturing-based** - quality is equated with conformance to specifications. *Do it right the first time*
	* **Value Based** - quality is jointly determined by the performance or conformance of the product and the price. *Get your money's worth*
* Another formulation of quality is as follows:
	* **Internal Quality** - the product conforms with quality specifications inside the plant. It is monitored through direct product measures.
	* **External Quality** - the product views the product as a "quality product". Quality is measured through customer satisfaction. 

* *Internal Quality is inherently tied to External Quality*. 
	* Fewer errors in the plant mean fewer defects that reach the customer. 
	* Lower inspection standards equates to more defects.
	* An organization that has [[Management|fostered]] the right attitudes and tools inside the plant is likely to be able to do the same outside the plant. 


* **Statistical Quality Control (SQC)** focuses on quality in quantitative terms (i.e., based on compliance with specifications). It focuses on manufacturing quality
* **Total Quality Management (TQM)** focuses on quality in qualitative terms. It entails looking at the customer
* *All TQM with no SQC produces talk without substance, while all SQC with no TQM produces numbers without purpose.*

* Quality may or may not be dependent to cost.
	* Cost increases with quality because more expensive QA methods are necessary. 
		* In practice, quality problems are one of the largest and most common causes of variability
		* Quality problems often end up increasing the utilization of workstations. Utilization increases non-linearly with rework rate. 
		* Variability of process time increases with rework rate. The variance of the effective process time does not always increase faster than the mean (i.e., due to the effects of variability pooling)
		* By the law of [[Factory Dynamics|lead time]], lead time increases with rework rate. 
	* Cost decreases with quality  because doing things right the first time reduces material and labor costs.
		* Quality can reduce scrap loss.
		* Quality inherently reduces WIP levels which gives the benefits of low WIP. 
* *Quality and operations can mutually support each other*

* **Law of Rework**. For a given throughput level, rework increases both the mean and standard deviation of the cycle time of a process.
	* If the rework is high enough to cause a resource to become a bottleneck (or operates on bottleneck resources), it can substantially alter the capacity of the line. *Where this is the case, a quality improvement can facilitate an increase in throughput*.
	* Rework on a nonbottlenecked resource, even one that has plenty of spare capacity, increases variability in the line, requiring higher WIP levels to attain throughput. *In this case, reductions in rework can facilitate reductions in WIP*
	* By decreasing capacity and increasing variability, *rework problems necessitate additional WIP* in the line and hence lead to longer average cycle times.
	* *The longer the rework loop, the greater the effect of rework on other metrics* [^loop] especially since rework affects more stations.
		* One approach to mitigate this without sacrificing quality is to setup rework lines. However, this can be costly and does not promote self-correcting behavior in the line. 

* In many manufacturing environments, internal quality problems lead to yield loss-rather than rework, either because the defect cannot be corrected or because it is not economical to do so. *The effects of scrapping parts are the same as reworking them. However scrap loss, especially if variable, is generally more costly and disruptive*
	* Inflating by the expected yield rate is not necessarily the best approach to address scrap because *yield loss can be variable*.
	* When too little good product finishes to fill an order, we must start additional parts and wait for them to finish before we can ship the entire amount to the customer costing goodwill and increasing WIP
	* When low yield loss results in more good product finishing than required to fill an order, the excess will go into finished goods inventory (FOI) and be used to fill future orders. The cost comes from inventory cost.
	* *In most cases, the cost of being short exceeds that of being over.*
	* *The best approach is to eliminate scrap*

[^loop]: In effect, this introduces a longer [[System Dynamics|delay]] to the feedback loop.

* *Quality is tied to the [[Supply Chain Management|supply chain]]*. When there is a significant dependency on outside sources, internal and external quality at the plant will critically depend on these inputs.
	* Good quality at the supplier level promotes good operations and quality at the plant level.
# SQC
* There are generally three classes of approaches for SQC
	* **Acceptance Sampling** - products are inspected to determine whether they conform to quality specifications.
	* **Process control** - processes are continuously monitored with respect to both mean and variability of performance to determine when special problems occur or when the process has gone out of control
	* **Experimental Design** - causes of quality problems are traced via experiments.
* Larger sources of variability that can potentially be traced to their causes are called **assignable-cause variation**. An **out of control process** is one subject to assignable cause variation. 
* Small sources of variability are called **natural variability**. A process operating stably within natural variability is **in statistical control**.


* *Just because a process is in statistical control doesn't mean it is capable*. 
	* If we define lower and upper specification levels $\text{LSL}$ and $\text{USL}$, the **process capability index** can be defined in multiple ways.
	  
	  Let $\mu$ be the estimated mean of the process and $\sigma$ the estimated variability (standard deviation)

		* *If the process mean were to be centered between the specification limits*. Assumes process output is approximately normally distributed.
		  $$
		  C_p=\frac{\text{USL} - \text{LSL}}{6\sigma}
		  $$
		* *If process mean is not necessarily centered between specification levels*
		  
		  $$
		  C_{pk} = \min\left[\frac{\text{USL}-\mu}{3\sigma}, \frac{\mu - \text{LSL}}{3\sigma}\right]
		  $$
		  The two options inside the min function are also useful estimates if only the USL or LSL are provided.
		* The **Taguchi Capability Index** estimates the process capability around a target $T$
		  
		  $$
		  C_{pm} = \frac{C_p}{\sqrt{1+\left(\frac{\mu-T}{\sigma}\right)^2}}
		  $$
		  If an off center process mean is given, we use 
		  		  $$
		  C_{pkm} = \frac{C_{pk}}{\sqrt{1+\left(\frac{\mu-T}{\sigma}\right)^2}}
		  $$

* Other statistical measures exist to bound the LCL and UCL.
	* **R Chart**: Use the range based on samples. We use the mean range $R$ and standard deviation $\sigma_R$  to give the interval 
	  $$
	  R\pm 3\sigma_R
	  $$
	  
	* **P Chart**: Track the fraction of items $p$ in periodic samples that fail to meet quality standards.  $n$ denotes the sample size.
	  
	  $$
	  p\pm 3\sqrt{\frac{p(1-p)}{n}}
	  $$
* *These methods can be generalized to any process subject to variability*

* [[Factory Variability|Variability reduction]] is frequently a vehicle for quality improvement.


# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 12