# BOP Challenge 2020 on 6D Object Localization
: pick & place project를 수행하던 도중 6D Pose Estimation에 관심이 갔고, 이에 대해 대표적인 행사가 BOP Challenge라 보기로 하였다.
BOP Challenge: the third in a series of public competitions organized with the goal to capture the status quo in the field of 6D object pose estimation from an RGB-D image.
- trend: Methods based on deep neural networks have finally caught up with methods based on point pair features, which were dominating previous editions of the challenge
     - Point Pair Features: Model Globally, Match Locally: Efficient and Robust 3D Object Recognition [paper](http://campar.in.tum.de/pub/drost2010CVPR/drost2010CVPR.pdf)
         - match pairs of oriented 3D points btw the point cloud of the test scene and the 3D object model, and aggregate the matches via a voting scheme

- DNN-based method
     - trend: have been commonly trained on "render & paste" images synthesized by openGL rendering of 3D object models randomly positioned on top of random backgrounds
     - problem: reduce the gap btw the synthetic and real domain

- CosyPose: Consistent multi-view multi-object 6D pose estimation [paper](https://arxiv.org/pdf/2008.08465.pdf)
- DenseFusion: 6D Object Pose Estimation by Iterative Dense Fusion [paper](https://arxiv.org/pdf/1901.04780v1.pdf)
- Pix2Pose: Pixel-Wise Coordinate Regression of Objects for 6D Pose Estimation [paper](https://arxiv.org/pdf/1908.07433.pdf)
