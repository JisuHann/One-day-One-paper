# Video Instance Segmentation Tracking with a Modified VAE Architecture
## Idea
- VAE architecture which consists of a probabilistic variable to describe an observation in latent space
   - capture spatial and motion information shared by all instances
   - generate attentive cues to reduce false negative mask predictions
- Gaussian Process model to enhance the statistical representation of VAE
   - by relaxing the prior strong independent
   - identically distributed (iid)assumption of conventional VAEs
   - allowing potential correlations among extracted latent variables


## Model
- learns embedded spatial interdependence and motion continuity in video data --> creates a representation
- Shared encoder and three parallel decoder
   - Decoder: yeild three disjoint branches for predictions of future frames, object detection boxes, and instance segmentation masks

- Auxiliary branch: learn to predict future frame
   - goal: learn finer representation an increase the amount of semantic information encoded in the latent space
   - why? plays as a supportive role to guide the model towards increasing the amount of semantic information envoded in the latent space and creating information-rich latent variables
- Proposal branch: summarize and output object-level information for connecting objects over time
   - +provide attentive cues to reduct false negatives in the augment branch
- Augment branch: produce a high-quality instance segmentation masks and reliable object tracks
   - aggregates pixel-level features extracted from different layers in the VAE encoder and the Mask R-CNN network
