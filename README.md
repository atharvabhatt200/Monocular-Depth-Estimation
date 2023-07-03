# Monocular-Depth-Estimation
Depth estimation is a key problem in computer vision, as it allows machines to perceive and understand the three-dimensional structure of a scene. Our task is to build and train a deep learning algorithm for Depth Estimation in monocular images.

We are using transfer learning where we repurpose high performing pre-trained 
networks that are originally designed for image classification as our deep features 
encoder.

## Architecture
The employed architecture is encoder-decoder architecture.
For encoder, the input RGB image is encoded into a feature vector using the 
DenseNet-169 network pretrained on ImageNet. This vector is then fed to a 
successive series of up-sampling layers, in order to construct the final depth map at half the input resolution. These up-sampling layers and their associated skip-connections form our decoder.

## Augmentation 
- Horizontal flipping (i.e., mirroring) of images at a probability of 0.5.
- Color channel permutations, e.g., swapping the red and green channels on the input, with the probability of 0.25.

## Dataset
The Dataset used is NYU Depth v2, a dataset that provides images and depth maps for different indoor scenes captured at a resolution of 640 X 480. The dataset contains 120K training samples and 654 testing samples. We train our method on a 50K subset. The depth maps have an upper bound of 10 meters. Our network produces predictions at half the input resolution, i.e. a resolution of 320 X 240.

## Steps to run the code:
- To train the model, run the DenseDepth.ipynb notebook.
- To test the model, put the files in .png format in the ‘examples’ folder and run the test.ipynb notebook.
