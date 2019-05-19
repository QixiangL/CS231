# Lecture2: Image Classification

Notes from QixiangL, 2019 May.19th
* Video: https://www.youtube.com/watch?v=OoUX-nOEjG0&list=PL3FW7Lu3i5JvHM8ljYj-zLfQRF3EO8sYv&index=2
* Slides: http://cs231n.stanford.edu/slides/2017/cs231n_2017_lecture2.pdf

# 0. Image Classification Overall
## 0.1 An Image Classifier
   * Given a set of images and set of discrete labels
   * Python API template :snake:
   ```python
   def classify_image(image):
   	# Some magic there?
	return class_label
   ```
## 0.2 Semantic Gap between human-vision and computer-vision
   * Human: high-level features
   * **Computer: low-level features** <br />
   	A gigantic grid of numbers between [0, 255] for each pixel (e.g. 800x600x3 for 3 channels RGB)
## 0.3 Challenges
   * Viewpoint variation: all pixel change when we change the camera
   * Illumination: dark & light
   * Deformation: tunned features, cats are liquid :ocean:
   * Occlusion: parts of the feature, cats are smart :100:
   * Background: difficult to detect the task from the background
   * Intraclass variance: difference between *orange* and *black* cats

# 1. A brief history of computer vision
*  **Evolution's Big Bang** *(543 millions years, B.C)* - begining of visions on animals
*  **Recognition** *(70-80s)*
	- [1]. Generalized Cylinder & Pictorial Structure *(1979, 1973)* - reduce the complex object into simple geometry
	- [2]. *David Lowe, 1987* - Lines with edges
* **Histogram of Gradients (HoG) & Deformable Part Model** *(Dalal & Triggs, Felzenswalb, McAllester, Ramanan, 2005, 2009)*
	- compose human and recognize them
* **Image-net dataset and IMAGENET Large Scale Visual Recognition Challenge** *(2009-now)*
	- 22K categories and 14M images, Challenge winer each year ---> find the best recognition algorithm
	   - 2012 AlexNet with ConvNet (CNN) (16.4%), 10% error rate drop from last year!
	   - 2014 Visual Geometry Group (VGG) (7.3%)
	   - 2014 GoogleNet or Inception (6.7%)
	   - 2015 Residual Networks (ResNet) (3.57%)

# 2. CS231n overview
## 2.1 What is the class about
   * CS231 focuses on one of the most important problems of visual recognition - image classification
   * Plenty of visual recognition problems related to imagine classification, such as:
	   - object detection, action classification, image captioning, ...
## 2.2 Convolutional Neural Network
   * CNN is important tool for object recognition
	   - Year 2010: NEC-UIUC
   * Why CNN boooooooooooms nowadays
	   - CNN is not a new algorithm (back in 1998 LeCun et al.)
	   - *[Reason1] faster and faster computers due to Moore's Law* <br />
	   	(i.e. CPU # of transistors: order of 6 in 1998, 9 in 2012; also the GPU)
## 2.4 Philosophy for this course
   * Practical: how to train networks at scale and on GPUs
   	   - e.g. like distributed optimization differences between CPU vs. GPU, etc

 
