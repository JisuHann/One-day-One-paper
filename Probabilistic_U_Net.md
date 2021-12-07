# A Probabilistic U-Net for Segmentation of Ambiguous Images
- [paper](https://arxiv.org/pdf/1806.05034.pdf), NIPS 2018

# Goal & Problem
- Segmentation framework that provides multiple segmentation hypotheses for ambiguous images
- Challenges: Providing only pixel-wise proabilities ignores all co-variances between the pixel, which makes a subsequent analysis much more difficult if not impossible
- Previous baseline
  - Dropout: fulfills the work of quantifying the pixel-wise uncertainty, but it produces inconsistent outputs
  - Ensemble of (deep)models: Ensembles are not necessarily diverse and typically not able to learn the rare variants as their members are trained independently
# Idea
: Generative segmentation model based on a combination of a conditional variational autoencoder
- Combines a conditional variational auto encoder(CVAE) with a U-Net
   - A low-dimensional latent space encodes the possible segmentation variants
      - Provide consistent segmentation maps, give a joint likelihood of modes (instead of pixel-wise probabilities)
      - Model the joint probability of all pixels in the segmentation map
      - Quantify the pixel-wise uncertainty 

![image](https://vitalab.github.io/article/images/UnetVAE/sc01.png)
### 1. Sampling
: on Fig.1a
1. **Prior net(distribution) P** estimates the probability of segementation variants for a given input image
   - modeled as Gaussian with mean and variance
   - z_i: Sample to an N-channel feature map
   - f_comb: combines the information and maps it to the desired number of classes
2. Concate this feature map to the last activation map of a U-Net

### 2. Training
: on Fig. 1b, trained with the standard training procedure for conditional VAEs (minimizing the variational lower bound)
- Model the joint probability of all pixels in the segmentation map
   - Probabilistic model for structured outputs based on optimizing the dissimilarity coefficient between the ground truth and predicted distributions
- Need to find a useful embedding of the segmentation variants in the latent space
   - **Posterior net(distribution) Q** learns to recognize a segmentation vairant and to map this to a position with some uncertainty tin the latent space
1. Posterior net that learns to recognize a segmentation variant
2. Sample from this posterior net distribution
