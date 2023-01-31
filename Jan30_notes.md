K means clustering


hueristics exist that work sometimes
## The elbow method
- as the numebr of clusters increases, the variance decreases
- plot variance vs k, check the slope to determine the best value of k
- the rate of change of decrease slows down. 
- use the value at the actual elbow as your optimal value

## Visual bag of words
- split images into fixed heuristic patches
- assign each path to a "word" in a dictionary of all encountered patches
- cluster all patches
    - normalise the image beforehand to just see the structure
    - first flatten the 2d patch into a n^2 size vector
    - SIFT also works
    - remove stop"words" (most frequently occuring patches)
        - remove these clusters, tfidf etc
    - normalise these patches
    - cluster patches together to group together similar patches (k means)
    - use these cluster patches to determine what images are
    - use the accuracy of the task  (classification eg.) to determine which cluster size is the best

## Initialization
- eg, for k means clustering, 
    - pick k random points from the dataset as initial values for the mean
    - what order do you pick them in?
        - say you pick point x as one of your means
        - compute the distances from x to all other points
        - build a cumulative distribution function, weighted on the distances of each point from x
        - pick a random number, use the cdf weighted by distances to pick another value
        - perform this procedure again to pick further points, weighted by the distances to previously chosen points

## PCA
- Principal component analysis
- Dimensionality reduction
- Maintain distances between points, preserve most information from the higher dimensional data
- Reduce this higher dimensional data to lower dimensions

- typically done by projecting to some axis/vector
- for d dimensional X , pick vectors to project data to with:
    - u.T @ X, where u.T is 1xd, thus reducing X to 1 dimension
    - find u where the variance of projected data is maximised
    - u = max_u (var(u.T @ X))
    - projecting to different vectors has different losses of information
        - eg if your data is on a line parallel to the x axis, projecting to the y axis has a variance of 0, almost all information is lost, 
        - but, projecting to the x axis loses almost no data
        - compute u.T @ covariance @ u to obtain variance

    - find the best vector by maximising u (u.T @ S @ u)maximising
