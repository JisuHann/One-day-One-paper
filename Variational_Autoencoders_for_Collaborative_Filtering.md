# Variational Autoencoders for Collaborative Filtering

작성자: 한지수
### 용어 정리
- Variational Autoencoder: 데이터의 확률분포를 학습하기 위해 latent variable z를 생성하는 Autoencoder 모델    
<img src="https://i.imgur.com/PhHb2aF.jpg" width = "300">
- Multinomial variable다항 변수: binomial distribution이항 분포에서 확장하여 여러 개의 class 중 분류하는 문제
- Bayesian inference베이즈 추론: 추론 대상의 사전 확률(p(\theta))와 관계된 관측 X의 확률 분포를 통해 해당 대상의 사후 확률(p(\theta | X))를 구하기는 과정
<img src = "https://wikimedia.org/api/rest_v1/media/math/render/svg/a9deb72fb98d404146f831e7ba2aa03100cbfc8e" width = "250">  
- Collaborative filtering: similarity pattern -> 뭘 이용할지 predict
- Latent Factor Model: 사용자와 아이템을 잠재적인 차원Factor들을 이용해 나타낼 수 있다고 보는 모델, Collaborative Filtering 보다 높은 성능
- Matrix Factorization: Latent Factor Model 을 구현하는 방법 중 Matrix를 이용하여 학습
## Introduction 
- Recommender Systems 기존의 방식
    - Collaborative Filtering: inherently linear, limits their modeling capacity >> explore non-linear probabilistic latent-variable model
    - Top-N ranking loss: difficult to optimize directly 

Neural Generative model
- Use multinomial likelihood for the data distribution
- over-regularized standard VAE objective -> draw connections by proposed regularization and the information-bottleneck principle and maximum-entropy discrimination

## Model 
- Generative process: deep latent gaussian model -> generalize the latent factor model
Likelihood functions used in latent-factor collaborative filtering: Gaussian and logistic likelihood
