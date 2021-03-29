# Kanwisher Lab Interview

### 1. Visual fMRI responses
#### Question
We would like to measure whether the brain activity in response to a long stimulus is different than the activity in response to a short stimulus. Our study volunteer looked at visual stimuli of either 0.5, 2, or 4 s duration. The provided variables contain the mean fMRI signal in our region of interest (ROI) sampled every 100 ms (meanROI), the time at which the stimuli occurred in seconds (stimtime), and the duration of each stimulus in seconds (stimdur). Plot the mean response of the fMRI signal to the different types of stimuli. Please also provide the script you wrote to plot this, in the language of your choice. How does the fMRI response depend on the stimulus duration?

#### Answer

### 2. Calculating image dissimilarity
#### Question
We would like to compare a set of stimuli to each other in terms of their similarity in low-level visual features. To do this, we would like you to first, run an edge-detection algorithm on the images in the folder “Question2”, and second, create a Representational Dissimilarity Matrix (RDM) based on the output of the edge detection algorithm. An RDM is a matrix of the pairwise distances between each image. (Hint: since there are 10 images, you should end up with a 10x10 matrix.) We would like you to use the Pearson correlation distance. The edge detection algorithm you choose does not matter, but please document your decision. As the final output of this analysis, create a plot of the RDM using the function imagesc and save it as an image or pdf.  

#### Answer

### 3. Brain Surfing
#### Question
Your fellow lab mates, Alyssa and Ben, are trying to use the latest version of the Freesurfer brain imaging software. They think that they have got it installed properly, but when they try to run preprocessing (using the command preproc-sess), they receive the following error
``` 
ERROR: cannot find either fslmaths or avwmaths
ERROR: mkbrainmask failed
ERROR: mkbrainmaks-sess failed
```
What is going on here? How can you check to make sure that there are no other problems with running this application? 

#### Answer

### 4. Debugging Matlab code
#### Question
Debug the Matlab code graph_toolbox_output.m so that it creates the bar graph shown in toolbox_barplot.png

#### Answer

### 5: Project organization
#### Question
For a recent project that you worked on (preferably, research-related), please describe how you organized the data and associated documentation for the project. Describe the data and files as if you were passing them off to someone else who will need to make sense of them and start working with the data and directories you've created. You can include any info or descriptions that you think would be helpful. For example, it may be helpful to include screenshots of data and code directories with explanations.

#### Answer

### 6: Freeform 
#### Question
Tell us about a particularly difficult technical problem that you solved. How did you solve it? 

#### Answer

### 7: Visualizing Artificial Neural Networks 
#### Question
The included jupyter notebook (VisualizingNetworks.ipynb) requires python=3.7 and the latest stable release of PyTorch (1.8.0) including several python libraries (jupyter, pytorch, random, scipy, torchvision, matplotlib, numpy). Run the code on your computer (each cell in the order it is presented) to see the final cell output a series of visualizations of the network (this will download an ImageNet pretrained VGG16 model onto your computer and may take 10 minutes to run the visualization). Please describe this visualization and how it is achieved? (Hint: What are the images of? How are the images produced? Why are they changing with each iteration? How are they initialized? What is the optimization?)

#### Answer

### BONUS (Optional):
#### Question
Can you change the code to instead visualize 1 or 2 units of the last convolutional layer (the conv2d with index 28 of the Sequential module in vgg16 i.e. vgg16.features[28])? Include your code and provide plots of your visualizations. (Hint: You cannot use the entire model as before, instead you will need to use the portion that ends with the specified convolutional layer and use as output the features of the units from this layer as your new targets). If you get stuck with the coding, you are welcome to describe your answer/solution as best as possible as your submission for this bonus question.

#### Answer
