## Deep Learning Points

### 논문 읽기
- 210408: Mask R-CNN + R-CNN 정리 [pdf](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/R-CNN정리.pdf)
- 210415: MAML
- 210422: Everybody Dance Now (GAN) [md](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/Everybody_Dance_Now.md)
- 210429: StyleGAN [md](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/StyleGAN.md)
- 210506: Variational Autoencoders for Collaborative Filtering
- 210506: Objectron: A Large Scale Dataset of Object-Centric Videos in the wild with pose annotations [closed issue](https://github.com/JisuHann/Deep-Learning-Repo/issues/2)
- 210527: ViT: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale [pdf](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/R-CNN정리.pdf)
- 210603: DALL-E: Zero-Shot Text-to-Image Generation [issue](https://github.com/JisuHann/Deep-Learning-Repo/issues/5)
- 210729: Multi-Source Domain Adaptation with Collaborative Learning for Semantic Segmentation (Huawei, CVPR-2021, Vision - Semantic Segmentation) [정리](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/Multi_source_unsupervised_domain_adaptation.md)

### Theory Concept
- Real Basics of Whole Deep Learning Networks
- CNN: Object Detection/Semantic Segmentation/Instance Segmentation
  - AlexNet, ResNet, VGGNet, GoogLeNet, MobileNet
        - Skip Connection
  - YOLO, SSD 
  - R-CNN, Fast R-CNN, Faster R-CNN, Mask R-CNN  [전체 정리](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/R-CNN정리.pdf)     
        - FPN(Feature Pyramid Net)   
        - Selective Search, RPN(Region Proposal Network)   
        - RoI Pooling, RoI Align   
  - Transformer & Vision   
        - ViT: Transformer & Vision [pdf](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/R-CNN정리.pdf)
  - 3D Object Detection   
        - Objectron [closed issue](https://github.com/JisuHann/Deep-Learning-Repo/issues/2)
- NLP
  - [x] Attention, Transformer
  - [ ] BERT, GPT (내용 보충 필요) [정리](https://github.com/JisuHann/Deep-Learning-Repo/blob/main/2.%20Attention%2C%20Transformer%2C%20BERT%2C%20GPT.pdf)
  - [ ] VideoBERT [issue](https://github.com/JisuHann/Deep-Learning-Repo/issues/4)
- Multi-Modal
  - [ ] DALL-E: Zero-Shot Text-to-Image Generation [issue](https://github.com/JisuHann/Deep-Learning-Repo/issues/5)
- Self-Supervised Learning
- Generative Models (코드 구현 연습 필요)
  - [x] AutoEncoder   
        - VAE
  - [x] GAN   
        - StyleGAN
- [x] Reinforcement Learning
  - Markov Property, Markov Decision Process, Markov Reward Process
  - Dynamic Programming: Bellman Equation, Policy Iteration, Value Iteration
  - Model-Free Prediction: Monte Carlo, Temporal Difference
  - Model-Free Control: MC control, TD Control(SARSA, Q-Learning)
  - Value Function Approximation: Linear Value Function Approximation, Neural Network(DQN), Batch Reinforcement Learning
  - REINFORCE, Policy Gradient, Actor Critic
- Meta Learning

### Code Implementation(Pytorch)
