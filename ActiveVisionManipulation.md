# Reinforcement Learning of Active Vision for Manipulating Objects under Occlusions (CoRL2018)
## Task
- Problem
  1. Training with vanilla CNN architectures failed to learn the task of object pushing in the presence of even simple distractors  
  2. failed to learn the task of object pushing in the presence of even simple distractors, that occasionally occlude the object 
## Idea
- Artificial agents that learn to jointly control their gripper and camera in order to reinforcement learn manipulation policies in the presence of occlusions from distractor objects
   - distractor object: the object that occlude the object of interest and cause it to disappear from the field of view
- Hand/eye controllers that learn to move the camera to keep the object within the field of view and visible, in coordination to manipulating it to achieve the desired goal
   - Consider pushing an object to target environments with distractors  

## Model
- Actor-critic architecture 
   - incorporate structural biases of object-centric attention
   - incorporate a trained object detector module


## Problem Formulation
- Givens:
  - Gripper
  - Camera (Not fixed)
  - Cluttered environments
- Unknowns:
  - Manipulation policies
  - Camera Control policies: facilitate state estimation by learning to increase visibility of the main object the agent interacts with, in coordination to the manipulation actions of the agents
- Constraint:

## Results
