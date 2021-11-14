# MQA: Answering the Question via Robotic Manipulation (RSS 2021)
[paper](http://www.roboticsproceedings.org/rss17/p044.pdf)

## Goal
- task: Manipulation Question Answering
  - Robot performs manipulation actions to change the environment in order to answer a given question
  - Question: COUNTING, EXISTENCE, SPATIAL, LOGIC
## Idea: MQA
: robot is required to find the answer by performing manipulation actions to actively explore the environment, rather than simply doing some predefined actions for the interaction
![image](https://dengyh16code.github.io/images/MQAweb/algorithm.png)
### Question Answering(QA) module
: robot should understand the semantic information of the given question and visual environment
![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCb-pPZapnuVEg7Q3tUp8mUDPDe7EhlDT5Ew&usqp=CAU)
- Network
  - Two image(I_start, I_stop): CNN
  - Question: 2-layer LSTM network
  - Image-question similarity - attention-weighted image features combined with question encoding
### Manipulation(M) module
- Deep Q Network(DQN) is designed to generate manipulation actions for the robot to interact with the environment
1. state space: continuous space that comes from two sources: visual encoding of RGBD images and question
2. action space: 9 specific pushing actions on each location (robot choose to push the object from 8 directions)
3. Reward design: based on the complexity of the scene(A Q-value heatmap)


## Results
- Scene generation on Simulated environement 
  - objects are thrown into the bin randomly 
