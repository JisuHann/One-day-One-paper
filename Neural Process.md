# Conditional Neural Process
: a conditional distribution over functions trained to model the empirical conditional distributions of functions f~P given a set of observations
- learns to model only a factored prediction of the mean and variances disregrading the covariance btw target points
## Difference with Bayesian approach
- don't implement Bayesian inference directly
- Equal point: the ability to extract prior knowledge directly from training data tied with scalability at test time
- Bayesian approach - difficult to design appropriate priors and stochastic processes are computationally expensive

# Convolutional Conditional Neural Process
: a member of the NP family that models translation equivariance in the data
- extend the thory of neural representations of sets to include **functional representation** 
- NP(embed in finite dimensional vector space) vs. ConvCNP(embed into an infinite dimensional function space)
