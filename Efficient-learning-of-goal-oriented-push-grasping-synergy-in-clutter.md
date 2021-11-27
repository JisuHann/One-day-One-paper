# Efficient learning of goal-oriented push-grasping synergy in clutter (RA-L2021)
[paper](https://arxiv.org/pdf/2103.05405v3.pdf)
### Task: Grasping a goal object in cluttered scene
### Problem Formulation
- Givens
   - Fixed RGB-D camera 
   - Robot manipulator (UR5 arm with an ROBOTIQ-85 gripper in V-REP)
   - Goal object mask
- Unknowns:
   - push-grasping policy for grasping a specific object in clutter
- Constraint:
   - Limit the push number up to five in an episode with a grasp at the end


### Methodology
- Goal-conditioned MDP:  learn a push-grasping policy for grasping a specific object in clutter
- Goal-conditioned hierarchical reinforcement learning formulation with high sample efficiency
   - Grasping discriminator:  Scoring current state for goal object grasping 
      - Input: Color heightmap, depth heightmap, Goal object mask 
      - Output: Grasp or push → Pixel-wise Grasp =(position of end-effector,orientation of end-effector)
   - Pushing generator (adversarial training manner)
      - Input:  Color heightmap, depth heightmap, Goal object mask 
      - Output: Push Q map → Push = (start position, pushing orientation with a fixed pushing length)
      - Design rewards for pushing by applying adversarial training
      - Positive reward: improvement of grasp q-value is greater than threshold


### Results
- Speed: ???
- Accuracy:  Good(Higher than baselines)
- Robustness: Good (High capability on novel objects unseen during training)
