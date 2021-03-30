# Kanwisher Lab Interview

### 1. Visual fMRI responses
#### Question
We would like to measure whether the brain activity in response to a long stimulus is different than the activity in response to a short stimulus. Our study volunteer looked at visual stimuli of either 0.5, 2, or 4 s duration. The provided variables contain the mean fMRI signal in our region of interest (ROI) sampled every 100 ms (meanROI), the time at which the stimuli occurred in seconds (stimtime), and the duration of each stimulus in seconds (stimdur). Plot the mean response of the fMRI signal to the different types of stimuli. Please also provide the script you wrote to plot this, in the language of your choice. How does the fMRI response depend on the stimulus duration?

#### Answer

[Refer to code in Answers.ipynb]

At first I thought about using a box plot but then I found [this](https://seaborn.pydata.org/generated/seaborn.violinplot.html) in the related section of the Seaborn box plot documentation. I think this is a perfect visualization for this purpose. 

The fMRI response seems to increase with stimulus duration, with the caveat that the non-stimulus mean ROI response is occasionally very high outside of the ongoing presence of a stimulus. Perhaps these high responses occurs just after a stimulus has ended? It would be interesting to examine the post-stimulus mean ROI response to see. Any way, disregarding this caveat, the non-stimulus ROI response as a distribution (quartiles and mean) increases.

### 2. Calculating image dissimilarity
#### Question
We would like to compare a set of stimuli to each other in terms of their similarity in low-level visual features. To do this, we would like you to first, run an edge-detection algorithm on the images in the folder “Question2”, and second, create a Representational Dissimilarity Matrix (RDM) based on the output of the edge detection algorithm. An RDM is a matrix of the pairwise distances between each image. (Hint: since there are 10 images, you should end up with a 10x10 matrix.) We would like you to use the Pearson correlation distance. The edge detection algorithm you choose does not matter, but please document your decision. As the final output of this analysis, create a plot of the RDM using the function imagesc and save it as an image or pdf.  

#### Answer

[Refer to code in Answers.ipynb]

From my computer vision experience, I recall using various kinds of edge detection algorithms with Scikit-Image. I referred to [the documentation](https://scikit-image.org/docs/dev/api/skimage.filters.html) to find the right algorithm. I settled on Sobel, because I found it suited my needs well and notably it is better than the Roberts algorithm which I recall having some issue with beforehand in terms of quality of output. 

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

It looks like there are missing tools. First, I will Google the error to see if this error has come up before. At first I thought that fslmaths is missing as a result of a missing commandline tool called [FSL Utils](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/Fslutils). But then I found [this](https://www.mail-archive.com/search?l=freesurfer@nmr.mgh.harvard.edu&q=subject:%22Re%5C%3A+%5C%5BFreesurfer%5C%5D+preprocessing+question%22&o=newest&f=1). After reading through a long series of questions and answers, I find the most helpful portion where one user asks "does $FREESURFER_HOME/bin/fslmaths.fsl exist?", to which the person responds no, and so the user suggests the following: 
"That is weird. You can get a copy from here
ftp://surfer.nmr.mgh.harvard.edu/transfer/outgoing/flat/greve/fslmaths.fsl.mac
copy it to
$FREESURFER_HOME/bin/fslmaths.fsl"

[Here](https://www.mail-archive.com/freesurfer@nmr.mgh.harvard.edu/msg10640.html) I found an identical error to one Alyssa and Ben found. The respondent advises that FSL needs to be installed. So, I would try running FSL and then install it if it is missing before deciding what to do next.

Regarding how we can check if there are no other problems with running this application, we can check that expected executables are in fact executable. For example, `-x <file>` on Linux.  

### 4. Debugging Matlab code
#### Question
Debug the Matlab code graph_toolbox_output.m so that it creates the bar graph shown in toolbox_barplot.png

#### Answer

Full disclaimer: I have never used MATLAB. I have never been instructed in MATLAB, and I have always used Python in any task that MATLAB might have been used for. 

I did not have MATLAB on my laptop, so I had to register online and download it, which took considerable time. Unfortunately, I pretty quickly found myself unable to debug the code. I found the first one (a missing square bracket on line 51 or graph_toolbox_output.m), however right after that I realized that I was going to need to sit down and learn more than just the functional basics of MATLAB. I would like to add that I consider myself an excellent software engineer, and I feel capable of learning any language with study. I apologize for not completing this question. Please also know that if MATLAB is important to this job as I take it to be given this question, then I will absolutely learn in on my own in between now and June. 

### 5: Project organization
#### Question
For a recent project that you worked on (preferably, research-related), please describe how you organized the data and associated documentation for the project. Describe the data and files as if you were passing them off to someone else who will need to make sense of them and start working with the data and directories you've created. You can include any info or descriptions that you think would be helpful. For example, it may be helpful to include screenshots of data and code directories with explanations.

#### Answer
Having worked as a data scientist both at a start-up and as a freelancer, I have learned just how important it is to organize, standardize, and document one's code. Even for my personal projects that only end up on my personal GitHub, I always thoughtfully organize my projects, especially if I have reason to believe that other people will look at them. Namely, I have adopted a few protocols of sorts. Given that I work primarily in Python, they are:
1. [Poetry (packaging and dependency manager)](https://python-poetry.org/)
* When it is up to me, I use the Poetry package manager for developing projects. After a lot of trial and error, I have found Poetry to consistently provide the best development experience in terms of dependency management / resolution as well as its development environment isolation capability. So, I have  . Naturally, I am a huge fan of the [pyproject.toml convention of PEP 518](https://www.python.org/dev/peps/pep-0518/). 
* Note: I do not use Poetry for one-off projects that don't require continuous development. For example, for this interview project I am used venv as my virtual environment and have included a simple requirements.txt file rather than a full pyproject.toml file.
2. Cookiecutter (project template utility)
* I use Cookiecutter project templates for different kinds of projects. Not only does this make project creation quick and save on development time, it also forces thoughtful standardization. In 2019, I attended a data science conference called ODSC West. There I learned about a data science project structure convention called Cookiecutter Data Science. While I do not adopt their exact project structure, this largely inspired my own use of Cookiecutter project templates. I use them both in my work for clients and my own personal projects. Here are some examples on my GitHub: [example project template](https://github.com/ianscottknight/cookiecutter-data-science-poetry-template/tree/main/%7B%7B%20cookiecutter.project_slug%20%7D%7D), [example resultant project](https://github.com/ianscottknight/phonology2vec).
3. [README](https://www.makeareadme.com/)
* I always include a straightforward README if I believe another person will be looking at what I have made. 
* The READMEs visible on each page of the Git repositories I linked above should instantly clarify their respective project structures.
4. [CHANGELOG](https://keepachangelog.com/en/1.0.0/)
* I typically use a changelog for paid projects.
5. [Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
* I use Git hooks to ensure clean, standardized code bases. My favorites are [Black](https://github.com/psf/black) and [nbstripout for clearing Jupyter notebook outputs](https://github.com/kynan/nbstripout).

To answer the specific question, I will refer to [one of my personal projects](https://github.com/ianscottknight/phonology2vec), which explains in the README how to acquire the data and an outline of the whole project structure. 

### 6: Freeform 
#### Question
Tell us about a particularly difficult technical problem that you solved. How did you solve it? 

#### Answer
I used to work at an indoor farm in San Jose, California with the mission of using computer vision, machine learning, and robotics to make plants grow better, faster. I was hired as the sole data scientist, and my principal task was to design and create the entire data pipeline from scratch. By data pipeline, I mean everything going on in between plants growing and what actions a robot should take to make it grow better. It was a huge problem, but here's a quick summary of how I did it:
* Data acquisition: We used an array of FLIR machine vision cameras attached to the arm of a robot that would drop down and capture images of plants growing on vertical columns twice a day. I wrote the scripts for capturing these images, which were run on a Raspberry Pi controlling the robot. 
* Data storage & processing: Raw images were uploaded to AWS S3 for storage, organized by date and physical coordinates in the grow structure. I set this up to trigger a script that would extract individual plant images from each raw image. These images were then uploaded to a separate S3 bucket which would trigger another script that would orchestrate several model inference scripts.
* Feature learning: This was by far the most difficult aspect of the whole task. When I was first hired, I was very happy to learn that the start-up had plant scientists working full-time on-site who would be able to answer all my questions. What I learned next surprised me: growing plants, at least in the indoor farming context, is much more of an art than a science. I found it impossible to get these plant scientists to give me a satisfactory theory of plant growth that I could turn into code. It was just so complicated; which features mattered differed by species, by "cultivar", by what the end use of the plant was (e.g. food, cosmetic ingredient, etc.), etc. So, I worked very hard to develop a high-level abstraction of the growth process, and arrived at a model which basically involved a directed graph of states which were unlocked by the plant exhibiting a certain range of features. Some features were computer vision-derived (e.g. surface area, color distribution of superpixels, blob extraction / blemish detection). Others had to be provided by humans. More on that in the next section. 
* Data labeling: We set up a laboratory where (unlucky) grad students were hired to label physical plants extracted from the grow structure with the their true feature values (those which were human label-able, that is). It was basically an assembly line. I made a user interface to help automate the process. This was eventually mostly replaced by a UI allowing labelers to draw boundaries around regions of interest and attach a specific label (they would create the label option it if it didn't already exist).
* Model development: Since it wasn't practical to label every plant / plant image, I created several models for predicting various aspects of plant state from an image. My first naive approach was to create an individual convolutional neural network for every feature to be predicted and train each from scratch. Then I moved to using running transfer learning on a CNN pre-trained on ImageNet. This worked reasonably well, but became difficult to manage as plant state became more complex. So, I moved to a single CNN with multi-output regression. From here, it was possible to predict the plant state of a plant in the grow structure just by taking a picture of it. I later found that this scheme was most useful when combined with unsupervised anomaly detection for triggering alerts for human inspection of the image. This proved to be successful. Before I left the start-up in November 2019, I was working on implementing a factorization machines model where every row was a plant state + timestamp and the output was a label of plant quality for use as food. 

### 7: Visualizing Artificial Neural Networks 
#### Question
The included jupyter notebook (VisualizingNetworks.ipynb) requires python=3.7 and the latest stable release of PyTorch (1.8.0) including several python libraries (jupyter, pytorch, random, scipy, torchvision, matplotlib, numpy). Run the code on your computer (each cell in the order it is presented) to see the final cell output a series of visualizations of the network (this will download an ImageNet pretrained VGG16 model onto your computer and may take 10 minutes to run the visualization). Please describe this visualization and how it is achieved? (Hint: What are the images of? How are the images produced? Why are they changing with each iteration? How are they initialized? What is the optimization?)

#### Answer

In essence, this visualization procedure is showing us what the trained VGG16 network believes is more and more probable with every iteration to be a member of the indexed class `target_y` corresponding to a particular network output neuron (i.e. the neuron that should activate strongly when the network is fed an image of that class). More specifically, it is iteratively updating the pixels of the image in such a way that `score` increases, which is the activation of the class neuron minus the L2 norm of the image. The norm component of `score` is parametrized by `l2_reg`, such that a higher `l2_reg` causes a stronger regularization effect. This works by basically punishing liberal deviation of many pixels from the mean and therefore encouraging more conservative alteration of pixels, i.e. the ones that matter more in determining the class score should they be updated. Once `score` is calculated, the gradient of the image with respect to `score` is derived through backpropogation, meaning that the partial derivative of each parameter of the network with respect to `score` is calculated iteratively, moving from the end of the network to the beginning and then to the image. It is important to note that the images (3 channel, 224x224 pixels) are initialized randomly, with mean 0 and standard deviation of 1. Also, the image is blurred and jittered slightly with each iteration. Since the network is trained to have its output class neurons activate strongly according to the content of the image, it makes sense that the image would change with increasing iterations of the visualization procedure, as the random image is not particularly gorilla-esque, for example, and therefore it can become more stimulating to the gorilla output neuron by this procedure. 

### BONUS (Optional):
#### Question
Can you change the code to instead visualize 1 or 2 units of the last convolutional layer (the conv2d with index 28 of the Sequential module in vgg16 i.e. vgg16.features[28])? Include your code and provide plots of your visualizations. (Hint: You cannot use the entire model as before, instead you will need to use the portion that ends with the specified convolutional layer and use as output the features of the units from this layer as your new targets). If you get stuck with the coding, you are welcome to describe your answer/solution as best as possible as your submission for this bonus question.

#### Answer

[Refer to code in VisualizingNetworks.ipynb]

I was able to accomplish this by using PyTorch hooks, which interestingly I independently used in a personal project of mine (trying to implement Deep Dream on the MNIST dataset for kicks). I specifically registered a hook on the conv at index 28 of the sequential module. Then I swapped the activation component of `score` with the sum of output of the registered hook (i.e. the conv). I kept the subtraction of the L2 norm of the image, as well.
