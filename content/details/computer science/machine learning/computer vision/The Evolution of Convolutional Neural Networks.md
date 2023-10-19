# Why Convolutions? 
* *Convolutions were not chosen randomly*, the choice to use a convolution is natural considering the following reasonable constraints that we want to impose upon an image in computer vision.
	* **Equivariance** -  the "object-ness" of any particular object in the image remains the same regardless of any rotation, translation or scaling that is applied (i.e., it is invariant to certain [[Group Theory|symmetries]])
	* **Locality** - pixels that are close to each other in the image tend to be related to each other.
	* The model should gradually **capture long ranged** dependencies by expanding its receptive field the deeper we go.

# Classical Models and their Innovations
### LeNet-5
* Made for the task of classifying hand-written digits. It was *one of the earliest CNNs*
* It defined the use of convolutional layers, however it was not widely adopted due to a lack of hardware. 

### AlexNet
* An improved version of LeNet-5 that was made to run on GPUs. *Parallelization* greatly improved the performance.
* Made use of *modernized techniques* such as Image Augmentation, Dropout, and the use of ReLU instead of the sigmoid as its activation function.

### VGG Network
* Made use of *convolutional blocks* which perform a series of convolutions before any pooling is done.
* The resulting network has the same number of parameters as a dense network with a wider convolutional kernel. However, the performance is much better.
* The convolution layers were kept small to support a narrow yet deep network. 

### Network In Networks
* Aimed to address the fact that CNNs with too many parameters can slow down layers. 
* It also aimed to add more fully connected layers at the end of the network to introduce non-linearities without destroying the spatial structure of the network.
* For low resolution images, the *Global Average Pooling* operation introduced more translational invariance.
* It made use of *1x1 Convolutional layers* to minimize the number of parameters without sacrificing accuracy by convolving over the channels of the image rather than compress it.

### GoogLeNet
* Strengthens Network in Networks by allowing for *multiple granularities* of feature maps extracted. 
* It is cheaper while having more improved accuracy. 
* This is done through the use of *Inception Blocks* that have many parallel branches that all perform convolutions but with different kernel sizes to scan at varying levels of detail.

### ResNet
* Aimed to *increase expressivity* of its predecssors and allow it to precisely capture a particular class of functions through *increased complexity* 
* To that end, introduced *skip connections* or residual blocks whcih connected the current output with the output of the previous layer (before any activations). 
* By using skip connections, the model counteracts performance degradation due to the deeper architecture, as well as the vanishing and exploding gradient problems.
* *It introduces an inductive bias that the target function is close to the identity function* 

### ResNeXt
* An extension of ResNet which takes from the inception blocks.
* *It combines skip connections with multi-branched convolutional layers*. Each group in the grouped convolutional layer can share results with other layers and previous layers.
* It adds more non-linearity by increasing the number of channels at the cost of some performance.

### DenseNet
* A generalization of ResNet which has *each layer be skip connected to all previous layers*. These are called *dense connections*
* It is more expressive as it incorporates previous feature maps from earlier on in the network. 
* It is also more computationally expensive and more complicated to parallelize.
* Compared to ResNet, the model parameters are relatively smaller. It introduces a form of regularization and allows for fewer parameters overall since feature maps are not lost. 
* The network can also be much narrower since the feature maps are preserved.

### AnyNet Design Space
* A generalization of the CNN architecture based on the observation that most modern neural networks follow the same structure.
	* A *stem* performs image pre-processing techniques (i.e., using a convolutional layer with a large window size).
	* A *body* consisting of convolutional blocks carry out transformations to go from images to feature maps. It operates on the image in decreasing resolutions
	* A *head* consists of an interface that can convert the outputs of the body into the desired outputs for the task.
* It operates under the following assumptions:
	* *General Design Principles actually exist* and these principles indicate good performance.
	* *Partial Metrics are sufficient* We need not train the network to convergence to assess whether it is good. Approximations are enough.
	* *Small networks usually scale*. Results obtained at a smaller scale can generalize to larger ones. Only after we have found a good architecture do we test if it scales well.
	* *Optimization is moderately easy*. Aspects of the design can be approximately factorized such that it is possible to infer their effect on the quantity at the outcome somewhat independently.

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al Ch. 7.1]] - for a full derivation of why we use convolutions. 
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al Ch. 7.6, Ch. 8]] - for a more in depth view on all the models discussed so far. 

