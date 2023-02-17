# Unsupervised Machine Learning Challenge
![image](https://user-images.githubusercontent.com/112406455/219126717-b00f77f9-f3f2-44f2-86ef-bbadebe6b0de.png)
## Background
You are on the data science team of a medical research company that’s interested in finding better ways to predict myopia, or nearsightedness. Your team has tried—and failed—to improve their classification model when training on the whole dataset. However, they believe that there might be distinct groups of patients that would be better to analyze separately. So, your supervisor has asked you to explore this possibility by using unsupervised learning.

You have been provided with raw data, so you’ll first need to process it to fit the machine learning models. You will use several clustering algorithms to explore whether the patients can be placed into distinct groups. Then, you’ll create a visualization to share your findings with your team and other key stakeholders.
## Instructions
This activity is broken down into four parts:

* Part 1: Prepare the Data.

* Part 2: Apply Dimensionality Reduction.

* Part 3: Perform a Cluster Analysis with K-means.

* Part 4: Make a Recommendation.

### Part 1: Prepare the Data
1. Read `myopia.csv` into a Pandas DataFrame.

<img width="1213" alt="Screenshot 2023-02-16 at 8 58 16 PM" src="https://user-images.githubusercontent.com/112406455/219539057-660af87f-d464-48a1-8f59-f41dbe248f0d.png">

2. Remove the "MYOPIC" column from the dataset.

<img width="1212" alt="Screenshot 2023-02-16 at 8 58 27 PM" src="https://user-images.githubusercontent.com/112406455/219539179-2667f6b1-b9db-4c0b-a47c-41e4b7f6b724.png">

3. Standardize your dataset so that columns that contain larger values do not influence the outcome more than columns with smaller values.

<img width="1215" alt="Screenshot 2023-02-16 at 8 58 35 PM" src="https://user-images.githubusercontent.com/112406455/219539338-3116a49d-35c9-4f3f-bdfb-4224fbaa0c23.png">


### Part 2: Apply Dimensionality Reduction
1. Perform dimensionality reduction with PCA. How did the number of the features change?

<img width="1213" alt="Screenshot 2023-02-16 at 8 58 58 PM" src="https://user-images.githubusercontent.com/112406455/219539499-07d2df09-4ccf-4959-88b2-a20f55c47a3a.png">

* After performing dimensionality reduction with PCA on the myopia dataset, the number of features was reduced by four, from the original number of features in the dataset. This technique reduced the dimensionality of the data while retaining most of the variance in the dataset, resulting in a more manageable set of features for subsequent analysis.

2. Further reduce the dataset dimensions with t-SNE and visually inspect the results. To do this, run t-SNE on the principal components, which is the output of the PCA transformation.

<img width="1212" alt="Screenshot 2023-02-16 at 8 58 44 PM" src="https://user-images.githubusercontent.com/112406455/219540118-fdb16d40-38cf-4ba1-a895-d665e805cc74.png">

3. Create a scatter plot of the t-SNE output. Are there distinct clusters?

<img width="1213" alt="Screenshot 2023-02-16 at 8 59 05 PM" src="https://user-images.githubusercontent.com/112406455/219540320-a23529ef-91bd-4443-9028-9c50052ff875.png">

* The scatter plot of the t-SNE output did not reveal any apparent clusters in the myopia dataset. While t-SNE is a powerful tool for visualizing high-dimensional data, it is possible that the underlying structure of the dataset is not well-suited for clustering or that the t-SNE algorithm did not identify the clusters effectively. Therefore, further analysis with other unsupervised machine learning techniques is required to identify potential clusters in the dataset.

### Part 3: Perform a Cluster Analysis with K-means
Create an elbow plot to identify the best number of clusters. Make sure to do the following:
* Use a `for` loop to determine the inertia for each `k` between 1 through 10.

<img width="1213" alt="Screenshot 2023-02-16 at 8 59 25 PM" src="https://user-images.githubusercontent.com/112406455/219540680-a7b5fa80-9f5c-45d5-80a4-f47c58102bd5.png">

* If possible, determine where the elbow of the plot is, and at which value of `k` it appears.

<img width="1210" alt="Screenshot 2023-02-16 at 8 59 36 PM" src="https://user-images.githubusercontent.com/112406455/219540801-52a18151-a9fd-4a0a-9c2d-e601193676cf.png">

To visualize the clusters a custom function `get_clusters()` was created to perform K-Means clustering and assign each data point to a cluster. The resulting clustered data was stored in a new DataFrame called `cluster_data`, which contained the t-SNE features and class labels from the original dataset. The `get_clusters()` function was called with `k=3` and `cluster_data` as input to perform the K-Means clustering. The resulting clustered data was then visualized using a scatter plot that displayed the t-SNE features on the x- and y-axes, with predicted cluster labels color-coded as points. 

<img width="1211" alt="Screenshot 2023-02-16 at 8 59 51 PM" src="https://user-images.githubusercontent.com/112406455/219542381-5315ab9b-646f-418f-a429-61f34a61644a.png">

### Part 4: Make a Recommendation
Based on your findings, write up a brief (one or two sentences) recommendation for your supervisor in your Jupyter Notebook. Can the patients be clustered? If so, into how many clusters?
* Based on my analysis, it appears that the patients can be clustered into three distinct groups using K-Means clustering on the t-SNE features. I arrived at this number by plotting an elbow curve of the inertia values for each k, which indicated that the elbow point is at k=3. Therefore, I recommend clustering the patients into three groups for further analysis.
## References
Reduced dataset from [Orinda Longitudinal Study of Myopia conducted by the US National Eye Institute](https://clinicaltrials.gov/ct2/show/NCT00000169)
