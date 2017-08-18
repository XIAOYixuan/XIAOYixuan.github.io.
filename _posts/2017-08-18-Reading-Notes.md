---
title: reading notes
tags: [Object Recognition, Pose Estimation, PaperNotes]
---
Problem: How to achieve real-time performance in 3d object recognitions/pose estimation problem?

### Real Time Head Pose Estimation with Random Regression Forests

Formulate pose estimation as a regression problem, address it via random regression forests.

Need to train on a bunch of synthetic data. Not suitable for multiple object recognition on small devices. (or just for had head pose estimation?) Also has some specific assumptions, for example, clean background with just one head(not even the body part), high quality depth info.


### Real-Time Face Pose Estimation from Single Range Images

Novel error function for training poses. Then accelerate it by GPU(nice). 
But again, high quality depth info. Just for face pose estimation.

More algo:
Real time head pose estimation from consumer depth cameras(n discriminative random regression forests)
Real-time input of 3D pose and gestures of a user's hand and its applications for HCI (pre trained net)
Real-time face pose estimation from single range images(GPU)

### Fast and automatic object pose estimation for range images on the GPU

First record patters of objects created from diff directions. Then detect objects in range images by searching for patterns. GPU needed. ICP.
Global feature based. 

Not precise enough. Not so efficient as PPF.

### Learning Methods for Generic Object Recognition with Invariance to Pose and Lighting

CovNet, SVM, NN on raw pixel(grayscale) or PCA featured. GPU for real-time performance.

Not what we want. More like objection detection. "3D" with diff pose.

### Fast 3d recognition and pose using the viewpoint feature histogram

VFH. Global features. Fast KNN.

Sounds nice. But  global features? Occlusion prob. Training time.

### Real-time pose estimation of 3D objects from camera images using neural networks

1998

Illuminiation strongly affect the performance.

