# Team Names
Catherine Weaver
Sara Shonkwiler
Jose Zavala

# Learning a Racing Strategy from the Geometric Features of a Racetrack
Finding a trajectory that minimizes the lap time of a car around a racetrack is a key step in optimal control of racecars. Formulating the minimum time problem can be difficult to solve because of the nonlinear vehicle dynamics. However, the problem can be simplified into two steps: path planning and velocity maximization. In this code we assume the optimal path has already been found, and we try to learn a method to calculate the maximum velocity a vehicle can achieve given its path. Three hyperparameters control the models learnt:
•	La: number of lookahead points 
•	Lb: number of lookbehind points
•	ds: distance between waypoints
# Important features of the code
## Construction of Feature Matrix
Important functions:
construct_phi(data_dic, feature_keys,La,Lb,ds):
Function to construct feature matrix:
•	data_dic: dictionary containing all data with keys shown above
•	feature_keys: list containing keys to choose for feature matrix
•	La: number of lookahead points 
•	Lb: number of lookbehind points
•	ds: distance between waypoints

construct_mega_phi(feature_keys,La,Lb,ds,train_course):
Function to construct the feature matrix of any given train course.
•	phi: feature matrix with all courses in train_course
•	phi_course: course identifier for elements of phi
###	Zero Model
Reference model created as an upper bound to the error. Predicts velocity to be always equal to zero.
###	Average Model
Baseline model created as a reference error. Predicts velocity to always be the average value of the actual measured velocities.
###	Ordinary Least Squares
Runs a linear regression on the raw features, equivalent to using polynomial features of degree 1.
###	Ridge Regression
Runs a ridge regression for different values of alpha (the regularization variable) for the polynomial features of degree 1.
###	Polynomial features order 2 – 4
Runs an ordinary least squares problem with polynomial features of orders 2-4.
###	Ridge Regression for polynomial degree 2
Runs a ridge regression for different values of alpha (the regularization variable) for the polynomial features of degree 2.
###	Ridge Regression for polynomial degree 3
Runs a ridge regression for different values of alpha (the regularization variable) for the polynomial features of degree 2.
###	Lasso
Attempts LASSO regression for polynomial features of degree 1 and 2.

##	Hyperparameter Search
Varies the three hyperparameters, La, Lb, and ds one at a time keeping the rest constant, in order to find the optimal set of hyperparameters to use.
#	How to change the models learnt
Three hyperparameters govern the models learnt: La, Lb, and ds. These three hyperparameters are defined in the section “Choose what data goes into the feature matrix”, and changing these will change the models learnt from the data.



