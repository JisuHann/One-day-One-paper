# A Survey of Uncertainty in Deep Neural Networks
[논문](https://arxiv.org/abs/2107.03342)
: robot의 interactive perception에 사용될 instance segmentation의 성능이 항상 완벽할 수 없다. uncertainty를 가져와 이를 이용한 접근법을 사용하고자 읽게 되었다.
## Uncertainty 종류
1. Model Uncertainty (e.g. insufficient model structure, lack of knowledge) 
    1. the DNN building process
             - the errors in the architecture specification of the DNN (e.g. number of parameters, deeper networks)
             - the errors in the training procedure of the DNN (e.g. batch size, learning rate)
    2. the applied inference process
             - the errors caused by unknown data (e.g. different task/domain)
2. Data Uncertainty (from the data e.g. image resolution, false labeling)
    1. the data acquisition process
             - Variability in the real world situation
                               - Neural networks are sensitive to distribution shift which leads to significant changes in the performance of a neural network
             - Error and Noise in Measurement Systems
                               - limited information in the measurements (e.g. image resolution, false labeling)
3. Distributional Uncertainty
: uncertainty on the actual network output, uncertainty that is caused by the change in the input-data distribution

## Neural Network Uncertainty Quantification Methods
1. Single deterministic methods
             - External Methods
             - Internal Methods
2. Bayesian methods (: DNNs where two forward passes of the same sample generally lead to different results)
             - Variational Inference
             - Sampling Methods
             - Laplace Approximation
3. Ensemble methods
             - Weight Sharing
             - Reduce Members
             - Training Strategies
4. Test-time augmentation methods

## Bayesian Methods
- Goal: predictive performance(Maximum posterior) of neural networks with the Bayesian learning (opposed to learning via maximum likelihood principle)
1. Variational Inference
             - Goal: (bc posterior is not tractable) approximate the posterior distribution by optimizing over a family of tractable distributions (: parametric distribution, Multivariate Normal Distribution)
             - Monte Carlo Dropout (MC Dropout)
2. Sampling Methods(Monte Carlo methods)
             - Goal: sampling 하면서 목표 distribution에 근사, deliver a representation of the target random variable from which realizations can be sampled.
             - Markov Chain Monte Carlo Sampling (MCMC), Hamiltonian Monte Carlo/Hybrid Monte Carlo (HMC)  ⇒  too expensive --> Stochastic Gradient Markov Chain Monte Carlo (SG-MCMC)
3. Laplace Approximation
             - Goal: estimate the posterior distribution over the parameters of neural networks
             - by taking the second-order Taylor series expansion of the log posterior over the weights around the MAP estimate given some data

