# Lecture2: Image Classification

Notes from QixiangL, 2019 May.19th
* Video: https://www.youtube.com/watch?v=OoUX-nOEjG0&list=PL3FW7Lu3i5JvHM8ljYj-zLfQRF3EO8sYv&index=2
* Slides: http://cs231n.stanford.edu/slides/2017/cs231n_2017_lecture2.pdf

# 0. Image Classification Overall
## 0.1 An Image Classifier
   * Given a set of images and set of discrete labels
   * Python API (quite brute and non-scalable):snake:
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
## 0.4 Data-Driven Approach
   * Collect a dataset of images and labels
   * Use Machine Learning to train a classifier
   * Evaluate the classifier on new images
   * Python API:snake:
   ```python
   def train(images, labels):
   """ Memorize all data and labels """
   	# Machine learning!
	return model
	
   def predict(model, test_images)
   """ Predict on test images """
   	# Use model to predict labels
	return test_labels
   ```

# 1. Nearest Neighbor Model
## 1.1 Model and Programming
*  Two step programming:
   - Train step: memorize all data and labels
   - Predict step: predict the label of the most similar training image
*  **CIFAR10** example dataset <br />
	10 classes, 50000 training images, 10000 testing images
* Distance Metric: minimam the L1 distance for image labeling
![L1_distance](https://github.com/QixiangL/CS231/blob/master/QixiangL-s%20learning/lec2_images/L1_distance.png)
* Python API:snake:
   - train: memorize training data.
   - predict: for each test image, find **closest** train image and predict **label of nearest image**. 
```python
import numpy as np

class NearestNeighbor:
	def __init__(self):
		pass
	
	def train(self, X, y):
		""" 
		X: NxD matrix, where each row is example and each column is feature
		y: Nx1 row, where each row is label
		"""
		# the nearest neighbor classfier simply remembers all the training data
		self.Xtrue = X
		self.ytrue = y
	
	def predict(slef, X):
		num_test = X.shape[0]
		# lets make sure that the output type matches the input type
		Ypred = np.zeros(num_test, dtype = self.ytrue.dtype)
		
		# loop over all test rows
		for i in xrange(num_test):
			# find the nearest training image to the i'th test image
			# using the L1 distance (sum of absolute value difference)
			distances = np.sum(no.abs(self.Xtrue - X[i, :]), axis = 1)
			min_index = np.argmin(distances) # get the index with smallest distance
			Ypred[i] = self.ytrue[min_index] # predict the label of the nearest example
		
		return Ypred
```
* Remarks
   - With N examples, computational complexity for train is O(1) and prdict is O(N).
   - This is bad because we want **FAST** on prediction and **SLOW** for training is ok.
   
## 1.2 K-Nearest Neighbors
* L1 & L2 Distance Metric
![distance metric](https://github.com/QixiangL/CS231/blob/master/QixiangL-s%20learning/lec2_images/L1_L2.png)
   - L1 (Manhattan) is dependent on the coordinate
   - L2 (Euclidean) is non-dependent on coordinate.
* Hyperparameters <br />
	*Choices about the algorithm that we set rather than learn.*
   - what is the best value of **k** to use?
   - what is the best **distance** to use?
* Setting Hyperparameters
   - **Idea #1:** 
   	choose hyperparameters that work best on **Full** data. :x:
   - **Idea #2:** <br />
   	Split data into **train** and **test**; choose hyperparameters that work best on **test** data. :x:
   - **Idea #3: Validation** <br />
   	Split data into **train**, **val**, and **test**; choose hyperparameters on **val** and evaluate on test. :heavy_check_mark:
   - **Idea #4: Cross-Validation** <br />
   	Split data into **folds**, try each fold as validation and average the results. :ballot_box_with_check:
![hyperparamters](https://github.com/QixiangL/CS231/blob/master/QixiangL-s%20learning/lec2_images/hyperparamters.png)

## 1.3 Summary
* k-NN on images **never used**
   - Very slow at test time
   - Cannot tell differenece on even simplest image distortion
   - Curse of dimensionality
* What we learn about k-NN
   - In **Image classification** we start with a **training set** of images and labels, and must predict labels on the **test set**
   - The **K-Nearest Neighbors** classifier predicts labels based on nearest training examples
   - Distance metric and K are **hyperparameters**
   - Choose hyperparameters using the **validation set**; only run on the test set once at the very end!

# 2. Linear Classification
## 2.1 Parametric Approach
   * Just a simplest linear dot-product to argmax the score at the output layer
   ![linear classifier](https://github.com/QixiangL/CS231/blob/master/QixiangL-s%20learning/lec2_images/linear_classifier.png)
## 2.2 Hard cases for a linear classifier
   * Parity problem or XOR problem
   * Multimodal data
## 2.3 Coming up:
   * Loss function
   * Optimization
   * ConvNets
