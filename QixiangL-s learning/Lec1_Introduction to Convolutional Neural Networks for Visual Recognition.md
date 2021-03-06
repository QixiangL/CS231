# Lecture1: Introduction to Convolutional Neural Network for Visual Recognition

Notes from QixiangL, 2019 Jan.30th
* Video: https://www.youtube.com/watch?v=vT1JzLTH4G4&list=PL3FW7Lu3i5JvHM8ljYj-zLfQRF3EO8sYv&index=1
* Slides: http://cs231n.stanford.edu/slides/2017/cs231n_2017_lecture1.pdf

# 0. About this course
## 0.1 Reasons for studying vision data
   * evolutional data size, so we need to understand vision data
   * hard like "black matter", difficult for algorithms to understand vision data
## 0.2 Application-map for computer vision
   * Biology neuroscience
   * Psychology: cognitive sciences
   * Computer Science: graphics, algorithms, theory, ... , systems, architecture, ...
   * Mathematics: information retrieval, machine learning
   * Engineering: robotics, speech, NLP
   * Physics: optics, image processing 
## 0.3 CS231n
   * Neural network (aka "deep learning") class on imagine classification

# 1. A brief history of computer vision
*  **Evolution's Big Bang** *(543 millions years, B.C)* - begining of visions on animals
*  **Camera Obscura** *(16-19th century A.D)* - human making mechanical "black box" to project imagines
*  **Mechanism of Vision** *(Hubel & Wiesel, 1959)* - vision mechanical by studying cat's brain
*  **Block World** *(Larry Robert, 1963)* -  the first ph.D theory about vision recoginition
*  **Vision** *(David Marr, 1970s)* 
	- Input imagine ---> Primal sketch (edge imagine)---> 2.5d sketch ---> 3d model representation
*  **Recognition** *(70-80s)*
	- [1]. Generalized Cylinder & Pictorial Structure *(1979, 1973)* - reduce the complex object into simple geometry
	- [2]. *David Lowe, 1987* - Lines with edges
* **Normalized Cut** *(Shi & Malik, 1997)* - groups the pixel of 1 object for recognition
	- [1] graph theory algorithm
	- [2] image segmentation
* **Face Detection** *(Paul Viola & Michael Jones, 2001)*
	- [1] machine learning techniques in 1990-2000 <br />
	  supprot vector machines (SVM), boosting, graphical models, neural networks
	- [2] AdaBoost algorithm
* **SIFT Feature** *(David Lowe, 1999)* - "SIFT" & Object Recognition
	- [1] object has "Critical features" that is diagnostic and invariant to changes
	- [2] identify the entire object ---> simplified to ---> find the critical features and do identify
* **Spatial Pyramid Matching** *(Lazebnik, Schmid & Ponce, 2006)* - holistic scenery imagine
* **Histogram of Gradients (HoG) & Deformable Part Model** *(Dalal & Triggs, Felzenswalb, McAllester, Ramanan, 2005, 2009)*
	- compose human and recognize them
* **PASCAL Visual Object Challenge (20 object categories)** *(2006-2012)*
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
	   - Year 2012: SuperVision (AlexNet) or CNN (7-8 layers)
	   - Year 2014: GoogleNet and VGG (16-19 layers)
	   - Year 2015: Residual Networks (ResNet) (152 layers)
   * Convolutional Neural Networks (CNN) were not invented overnight
	   - coming from 2012 and tuning and tweaking since then
   * Why CNN boooooooooooms nowadays
	   - CNN is not a new algorithm (back in 1998 LeCun et al.)
	   - *[Reason1] faster and faster computers due to Moore's Law* <br />
	   	(i.e. CPU # of transistors: order of 6 in 1998, 9 in 2012; also the GPU)
	   - *[Reason2] higher pixel image to feed algorithms that are hungry for data* <br />
		(i.e. # of pixels used in trainning: order of 7 in 1998, 14 in 2012)
## 2.3 Other fancy things in the course
   * the quest for visual intelligence goes far beyond object recognition
## 2.4 Philosophy for this course
   * Thorough and Detailed: understand how to write from scratch, debug and train CNN
   * Practical: how to train networks at scale and on GPUs
   	   - e.g. like distributed optimization differences between CPU vs. GPU, etc
	   - software tools such as Caffe, TensorFlow, and (Py)Torch
   * State of the art: new and fancy research world
   * Fun: fun topics such as Image Captioning (using RNN), also DeepDream, NeuralStyle, etc. 	

 
