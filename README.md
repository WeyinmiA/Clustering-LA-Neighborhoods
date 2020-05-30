# Coursera Capstone Project for IBM Data Science Professional Certificate

**Capstone Project Notebook:** The ClusteringLA.ipynb notebook can be viewed in its fully rendered form [here!](https://nbviewer.jupyter.org/github/WeyinmiA/Coursera_Capstone/blob/master/Capstone%20Project-%20Clustering%20LA/ClusteringLA.ipynb)

## Introduction/Problem Statement
I am an incoming grad student at USC for Fall 2020 and because of the current state of affairs in the world (namely the Covid-19 global pandemic that has stunned the world!) I have not been able to visit Los Angeles, CA prior to enrolment, in order to get to know the city well before moving there for my studies. As such it has been difficult to decide where I would like to live or even the areas I might like to visit first upon arrival. 

I presume that this may be the case for a lot of other students moving to the city of LA for college, whether at USC or even UCLA. In an effort to remedy this, I have decided to dive into LA addresses data to investigate the region. The aim is to try and find any patterns that may be interesting to me or other students and that may be helpful in simply discovering more about the area.

Graduate students and undergraduate students alike who aren’t familiar with the LA area and are not sure where they would like to live in, may benefit from this explorative project!

## Data
The [LA addresses data](https://catalog.data.gov/dataset/addresses-in-the-city-of-los-angeles) is sourced from [data.lacity.org](data.lacity.org) provided by the department: Bureau of Engineering. It is used in conjunction with [Foursquare location data](https://foursquare.com). 

## Methodology
After the data has been loaded and preprocessed, a call to the Foursquare API will be made to explore and segment the neighborhoods in LA. Foursquare's **explore** function will be utilized to get the most common venue categories (within a radius of 500 metres) in each neighborhood. This will then be aggregated with the neighborhood data and subsequently used to group the neighborhoods into clusters.

The clustering algorithm of choice to complete this task will be the *k*-means. *K*-means is a simple but powerful model that is vastly used for clustering in many data science applications and is especially useful if you need to quickly discover insights from unlabeled data. A drawback to this algorithm though, is that it requires the number of clusters to be pre-specified, hence it is a somewhat naive algorithm. To compensate for this, it is evaluated using the **elbow method**. The elbow method will run k-means clustering on the dataset for a range of values for k (for example 1-10) then for each value of k it computes an average score for all clusters. This average score or distortion is the sum of the differences between each point in a cluster and the associated cluster center. Next, this is plotted and if the plot resembles an arm, then the **elbow** (the point of inflection on the curve) is a good indication that the underlying model fits best at that point.  Finally, the Folium library will be used to visualize the neighborhoods and their emerging clusters.
