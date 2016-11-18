K-Means Clustering:

The goal of this project was to implement a framework in java for performing k-means clustering using Hadoop MapReduce. 

K-means clustering is a classical clustering algorithm that uses an expectation maximization like technique to partition a number of data points into k clusters. 
K-means clustering is commonly used for a number of classification applications.  Because k-means is run on such large data sets, and because of certain characteristics of the algorithm, it is a good candidate for parallelization.


In this problem, we have considered inputs a set of n 1-dimensional points and desired clusters of size 3.

Once the k initial centers are chosen, the distance is calculated(Euclidean distance) from every point in the set to each of the 3 centers & point with the corresponding center is emitted by the mapper. Reducer collect all of the points of a particular centroid and calculate a new centroid and emit.


Termination Condition:
When difference between old and new centroid is less than or equal to 0.1

		
Algorithm: 
Step1: Initially randomly centroid is selected based on data. In our execution we take 3.
Step2: The Input file contains initial centroid and data. 
Step3: In Mapper class "configure" function is used to first open the file and read the centroids and store in the data structure(we used ArrayList)
Step4: Mapper read the data file and emit the nearest centroid with the point to the reducer. 
Step5: Reducer collect all this data and calculate the new corresponding centroids and emit. 
Step6: In the job configuration, we are reading both files and checking 
		if difference between old and new centroid is less than 0.1 then(Formulae for closest data point ci={j:d(xj,µi)=d(xj,µl),l?i,j=1,...,n})
			convergence is reached 
	    else 
		    repeat step 2 with new centroids.
		  

Samples
For Centroid, this should be fine:
50.0
60.0
70.0

For data something like this simple should work:
50
53
49
59
63
59
63
75
48
55
57