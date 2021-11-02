# A Probabilistic U-Net for Segmentation of Ambiguous Images
- [paper](https://arxiv.org/pdf/1806.05034.pdf), NIPS 2018

# Goal & Problem
- learning a distribution over (semantic) segmentations given an input
- Challenges: Providing only pixel-wise proabilities ignores all co-variances between the pixel, which makes a subsequent analysis much more difficult if not impossible
- Previous baseline
  - Dropout: fulfills the work of quantifying the pixel-wise uncertainty, but it produces inconsistent outputs
  - Ensemble of (deep)models: Ensembles are not necessarily diverse and typically not able to learn the rare variants as their members are trained independently
# Idea
: Generative segmentation model based on a combination of a conditional variational autoencoder
- Combines a conditional variational auto encoder(CVAE) with a U-Net
- the ability to model the joint probability of all pixels in the segmentation map => results multiple segmentation map
- A low-dimensional latent space encodes the possible segmentation variants

![image](https://vitalab.github.io/article/images/UnetVAE/sc01.png)
### 1. Sampling
: on Fig.1a
1. Prior net estimates the probability of segemntation variants for a given input image
2. Sample to an N-channel feature map from prior probability distribution
3. Concate this feature map to the last activation map of a U=Net

### 2. Training
: on Fig. 1b, trained with the standard training procedure for conditional VAEs by minimizing the variational lower bound
1. Posterior net that learns to recognize a segmentation variant
2. Sample from this posterior net distribution
