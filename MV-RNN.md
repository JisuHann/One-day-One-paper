# 3D Attention-Driven Depth Acquisition for Object Identification

task: Fine-grained Object classification

## Recurrent 3D attention model (3D-RAM)
![](https://d3i71xaburhd42.cloudfront.net/27a13dd9169776fa9a23477010204cbcecc5a935/3-Figure2-1.png)

: 3D attention model for active 3D object identification with multi-view depth acquisition
- input: depth image
- output
   1. shape classification based on classification hierarchy
   2. NBV (most informative region)
- trained by synthetic 3D model 

#### Shape hierarchy
   - organize the shape collection with a hierarchy of coarse-to-fine MV-CNN classifiers
   - Learning enhanced features particularly effective for the fine-grained task of the current level (by fine-tuning the one inherited from its parent node)

#### Part-level attention
   - attention of the views in 3D space pointing to a 3D object
   - to tolerate object occlusion, robust against partial occlusion
   - learn at each node focus-driven features

### 1. View-level attention: MV-RNN
: select NBV for depth acquisition targeting at  an object of interest, sequential NBV regression based on RNN
- each step
   1. acquires a depth image
   2. integrates(aggregates) the order-aware information of all past views
   2. conducts the shape classification - Shape hierarchy
   3. regress the NBV - Recurrent attention model for NBV regression

- Recurrent attention model for NBV regression
Repeat
   1. input processing
   2. view(information) aggregation network & view glimpse network
      - devise max-pooling based recurrent units to achieve powerful view aggregation
      - the glimpse integration of depth images and view parameters is postponed after view aggregation
   3. Action generation: NBV network
      - input: current state of above recurrent network
      - Output: vector of NBV parameters

#### View-based observation
- to achieve continuous view planning
- On the full viewing space parameterized on a viewing sphere around a 3D model in training or an object of interest during testing
- input: 2.5D depth image
- Output: captured 2.5D depth image for the object of interest 

### 2. Region-level attention
: concentrates on the discriminative regions in each view for part-based recognition
- instance-level shape classification, after the view aggregation layer

