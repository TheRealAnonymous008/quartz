# Papers

* *Spatial Transformer Networks by Jaderberg, Simonyan, Zisserman, and Kavukcuoglu (Feb 4, 2016)* - introduces the Spatial Transformer architecture, which minimizes the number of parameters and layers DCNNs need to be spatially invariant by having an attention mechanism derive parameterized transformations from feature maps, and using a sample of these on the feature map. It can be used to augment existing models to achieve SOTA performance, and generalization to other tasks.

* *You Only Look Once -- Unified, Unified, Real-Time Object Detection by Redmon, Divvala, Girshick, and Farhadi (May 9, 2016)* - introduces the YOLO model which reformulates the object detection task as a regression task where the bounding box and the probability of an object class are predicted. YOLO achieves SOTA real-time object detection and is in general faster and easier to train than previous models since it makes use of a single pipeline for bounding box and class prediction.

* *Continual Learning with Lifelong Visual Transformer by Wang et. al (2022)* - introduces the Lifelong Visual Transformer (LVT) which aims to extend continual learning from CNNs to ViTs by exploiting the transformer architecture. It balances between stability and plasticity, through a dual classifier and the use of stored exemplars for rehearsal. LVTs perform significantly better than existing models in small, possibly nonstationary datasets.

* *Intelli-Paint--Towards Developing More Human-Intelligible Painting Agents by Singh, Smith, Echevarria, and Zheng (2022)* - introduces Intelli-Paint, a system aimed towards human intelligible painting. It achieves this using a three step pipeline that mimics how humans paint and perceive paintings--first it draws the background and identifies key objects, whose features are captured and drawn in a coarse-to-fine manner. The agent is also capable of removing redundant brush strokes. Altogether, the system achieves more relatable and efficient painting. 

* *BLIP -- Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation by Li, Li, Xiong, and Hoi (Feb 15, 2022)* - introduces BLIP, a new approach for Visual-Language Pre-Training framework that achieves SOTA performance on different vision-language understanding tasks and SOTA zero-shot performance on video-language-understanding tasks. It makes use of a bootstrapped dataset derived from synthetically captioned web images that have been filtered for noise. It is trained on three tasks -- encoding images and text, matching image encoding with text encoding, and generating image-grounded responses.

* *FrePGAN -- Robust Deepfake Detection Using Frequency-Level Perturbations by Jeong, Kim, Ro and Choi (Jun 8, 2022)* - introduces FraPGAN, a GAN trained pre-processes images for deepfake detectors. The pre-processing involves applying frequency-level perturbations to remove frequency-level artifacts that are characteristic of certain deepfake GANs and objects, and which make deepfake detectors prone to overfitting.

* *Meta-attention for ViT-backed Continual Learning by Xue, Zhang, Song, and Song (Mar 22, 2022)* - introduces MEAT (Meta Attention), a continual learning mechanism tailored for ViTs that involves creating adaptive attention patterns by paying attention to the self-attention mechanism. This allows for certain patches in the image to be isolated for a specific task.

* *Deconfounded Visual Grounding by Huang et. al (Jun 8, 2022)* - introduces a deconfounder to remove the bias in visual grounding wherein bounding box predictions are influenced by the location of objects in the query in the training set.

* *Decoupled Contrastive Learning by Yeh et. al (Jul 30, 2022)* - introduces Decoupled Contrastive Learning (DCL) loss which allows self-supervised learning to be done without requiring large computational resources. It does this by identifying and removing a coupling effect between positive and negative samples which trivializes the SSL task for easy positive and easy negative samples, which reduces learning.

*  *Model Doctor -- A Simple Gradient Aggregation Strategy for Diagnosing and Treating CNN Classifiers by Feng et. al (Jun 8, 2022)* - introduces Model Doctor, an automatic model diagnosis system that aims to improve the accuracy of CNN-based classifiers based on how categories tend to be correlated to specific convolutions, and how positive samples tend to be successive in feature space. The system can be used to augment existing methods. 
# Links
* The Evolution of Convolutional Neural Networks - for an overview into the history of CNNs and how they have evolved over time
* Crowd Counting - a subdomain of Computer Vision.

