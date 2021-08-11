# Incremental Few-Shot Instance Segmentation
[논문링크](https://arxiv.org/pdf/2105.05312.pdf), Model Name: iMTFA (Incremental MTFA), [code](https://github.com/danganea/iMTFA)
지금 하고 있는 연구에서 확장하고자 다음과 같은 근거로 읽게 되었다.
- 처음 보는 obj에 대한 분류를 어떻게 진행할 수 있을까-> similarity에 기반한 분류를 진행해보고 싶다. -> Few shot learning -> Few shot learning + Instance segmentation을 찾던 중에 발견

## Problem
- Instance segmentation task
- problem of learning with limited avaliable data: labeled training data for novel classes is scare
    - examples that are provided at train and test time is memory intensive

## Goal 
- match class embedding at the RoI-level using cosine similarity
- add new classes without the need for further training or access to previous training data
- class-agnostic manner
     - eliminate the need for extensive retraining process for new classes bc these can be added incrementally

## In this paper
![Architecture](https://media.arxiv-vanity.com/render-output/5104156/x1.png)
1. Instance Feature Extractor(IFE): [Train Mask R-CNN] -> [FC-layer]
    -  Input: Image
    - Output: Re-purposed RoI level 
    - transform a fixed feature extractor into an Instance feature extractor that produces discriminative embeddings that are aligned with the per-class representatives
2. Cosine-Similarity classifier  

![iMTFA](https://media.arxiv-vanity.com/render-output/5104156/x3.png)
TFA -> MTFA -> iMTFA


#### TFA(Two-stage Fine Tuning)
- First stage, Feature Extractor: Faster RCNN(trained on the base classes)
     - [network backbone] + [region proposal network(RPN)] + [RoI Feature Extractor]
- Second stage, Prediction Head
     - **[RoI classifier]** + [box regressor] 

#### MTFA(Mask-TFA)
- First stage, Feature Extractor: Mask RCNN 
     - Add [up-sampling] component and [a mask prediction branch] at the RoI level
     - [network backbone] + [region proposal network(RPN)] + [RoI Feature Extractor]
- Second stage, Prediction Head
     - **[RoI classifier]** + [box regressor] 


 #### Cosine-similarity classifier
: RoI classifier, a fully connected layer which produce classification score -> the class with lowest cosine distance (btw an RoI's embedding and the class representatives)
- On iMTFA: Class-agnostic manner
      - can add new classes by simply averaging their computed embeddings and placing them in the classification head's weight matrix 
