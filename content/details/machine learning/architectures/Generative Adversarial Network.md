* A **Generative Adversarial Network** relies on the following principle: *a data generator is good if we cannot tell fake data from real data.*

![[GAN.png]]
<figcaption>Generative Adversarial Network pipeline.  Image Taken from Zhang </figcaption>


* The GAN architecture requires two parts
	* A **generator** $G$ that can generate synthetic data that looks like real data. It draws a latent variable $z$ from a source of randomness [^randomness] . It then applies a function to generate $x'=G(z)$
	* A **discriminator** $D$ that can distinguish real data from fake data. It is a binary classifier that can distinguish if $x$ is from real data or from the distribution.

[^randomness]: The source of randomness for the generator does not matter as long as it is random.

* In the GAN architecture, both networks are in [[Dynamic Games of Complete Information|competition]] with each other. 
	* The generator wants to fool the discriminator.
	* The discriminator wants to detect the fake data.


# Training
* Training involves alternating between training $G$ and $D$:
	* $D$ is trained for one or more epochs, keeping $G$ fixed. In this way, $D$ learns to detect the flaws of $G$.
	* $G$ is trained for one or more epochs, keeping $D$ fixed. In this way, $G$ learns to fool $D$.
	* Repeat.
* Over time, $D$'s performance gets worse because the $D$'s accuracy (assuming $G$ gets better) converges to $0.5$. This means that feedback for $G$ (which comes from $D$) gets worse over time and $G$'s performance might soon become random too. *Convergence is unstable*.

* $G$ and  $D$ are playing a minimax function with the objective function called the **minimax loss** (which derives from [[Loss Function#Cross-Entropy Loss|Cross Entropy Loss]])
  $$
  \min_D \max_G \{\mathbb{E}_{x\sim \text{Data}} \log D(x) -E_{x\sim \text{Noise}} \log (1-D(G(x)\}
  $$
  There are two issues with this:
	* Vanishing Gradients
	*  **Mode Collapse** wherein the generator does not [[Pathologies of Deep Learning#Generalization|generalize]]. Instead, it generates a limited number of outputs -- specifically the ones that seem most plausible to the discriminator. As a result, the discriminator only learns to reject those outputs.

* An alternative loss that can be used is the **Wasserstein Loss** function.
  We modify the GAN to be a **Wasserstein GAN (WGAN)** where the discriminator outputs a larger number (possibly greater than $0$) for real instances than for fake instances.
  
  We call the discriminator of WGAN a **critic**. The loss function is defined as follows
  
   $$
  \min_D \max_G \{\mathbb{E}_{x\sim \text{Data}} D(x) +E_{x\sim \text{Noise}}D(G(x)\}
  $$
  An important requirements for WGAN is that *weights need to remain within a constrained range*;


# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang]]
* [Google Developers Course on GAN](https://developers.google.com/machine-learning/gan)