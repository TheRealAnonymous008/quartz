* Stands for **Proportional [[Integral Calculus|Integral]] [[Differential Calculus|Derivative]]** Control.  
* We define a desired set point $\text{SP}=r(t)$ and a measured process variable $\text{PV}=y(t)$. The error is defined
   $$
   e(t) = r(t) - y(t)
   $$
* It combines three forms of control based on the error. 
  The constants $K_p, K_i, K_d$ are called **gain factors**.
	* **Proportional Control**, defined by the term 
	  $$
	  P= K_p  \ e(t)
	  $$
	* **Integral Control**, defined by the term
	  $$
	  I = K_i \int  e(\tau ) \ d\tau 
	  $$

	* **Derivative Control** defined by the term 
	  $$
	  D = K_d \frac{de(t)}{ dt}
	  $$

* The overall control function is then defined by
  $$
  \begin{split}
  u(t) &= P + I + D \\
  & = K_p e (t)  + K_i \int e(\tau) \ d\tau + K_d \frac{de(t)}{dt}
  \end{split}
  $$


* Each control accounts for the temporality of $e(t)$ [^meta]
	* Proportional control accounts for the current value of $e(t)$. 
	* Integral control accounts for past values of $e(t)$ since there could be residual error that persists over time.
	* Derivative control estimates the future value of $e(t)$ which aims to reduce the effect of $e(t)$ by damping this value.

[^meta]: Although described in the context of controllers for mechanical, this logic of controlling based on current (P), cumulative past (I) and anticipated future (D) values is applicable in a lot of other non-controller related context if we adapt a [[Cybernetics]] view and examine the controller as it acts on an entire system (i.e., a human society or an economy)

* A PID controller is tuned by modifying each of the constants $K_p, K_i, K_d$.

* PID control is not always suitable.
	* They may not scale well when multiple parameters must be considered.
	* They also do not necessarily provide optimal control. 
	* It does not, by default, incorporate any knowledge about the system. 
	* It works best when the feedback loop is linear and symmetric. 
# Links
* [[Principles of Systems Science by Mobus and Kalton]]