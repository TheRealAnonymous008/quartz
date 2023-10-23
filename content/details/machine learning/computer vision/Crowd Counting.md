* Although specific to counting people in a crowd, crowd counting methods can be extended to count other objects such as vehicles and plants.
# Papers
* *Adapted Dilated Network with Self-Correction Supervision for Counting by Bai et. al (2020)* - introduces ADSCNet, a model for crowd detection that addresses the issue of inconsistency in human annotation which leads to inaccurate models, and scale variations due to perspective via self-correction and adapted dilated convolutional kernels. The model achieves more consistent and SOTA performance.

* *CNN-Based Density Estimation and Crowd Counting -- A Survey by Gao et. al (Mar 28, 2020)* - conducts a survey on existing CNN-based density estimation crowd-counting methods. It identifies a taxonomy based on network architecture, learning, and inferencing methods. It also introduces various benchmarks and compares models to the SOTA. Finally, it highlights key challenges subject for future research. 

* *To Choose or to Fuse-- Scale Selection for Crowd Counting by Song et. al (May 15, 2021)* - introduces SASNet, a multi-branch model which features adaptive scale selection and a novel Pyramid Region Awareness Loss to achieve SOTA performance in crowd detection. At its core, the model determines the best granularity to use, and recursively learns on patches of the image that overestimate the density count,

* *FusionCount--Efficient Crowd Counting Via Multiscale Feature Fusion by Ma, Sanchez and Guha (Feb 28, 2022)* - introduces FusionNet, an encoder-decoder architecture for crowd counting that fuses features to create a scale continuous receptive field. The model avoids having to extract additional features from the encoder. It achieves SOTA performance.

* *Rethinking Spatial Invariance of Convolutional Networks for Object Counting by Cheng et. al (Aug 18, 2022)* - introduces a GauNet, a new approach for object counting by loosening the constraint of pixel-level spatial invariance which leads to overfitting due to pixel-level noise within the image. The paper makes use of a CNN where the convolutional kernels are replaced with learnt Gaussian kernels. The work outperforms other SOTA methods. 

# Links
* [Awesome Crowd Counting](https://github.com/gjy3035/Awesome-Crowd-Counting) - catalogue of papers for crowd counting.
* [[Computer Vision]]
