# Coursera Capstone Project for IBM Data Science Professional Certificate

**Capstone Project Notebook:** The ClusteringLA.ipynb notebook can be viewed in its fully rendered form [here!](https://nbviewer.jupyter.org/github/WeyinmiA/Coursera_Capstone/blob/master/Capstone%20Project-%20Clustering%20LA/ClusteringLA.ipynb)

## Introduction/Problem Statement
I am an incoming grad student at USC for Fall 2020 and because of the current state of affairs in the world (namely the Covid-19 global pandemic that has stunned the world!) I have not been able to visit Los Angeles, CA prior to enrolment, in order to get to know the city well before moving there for my studies. As such it has been difficult to decide where I would like to live or even the areas I might like to visit first upon arrival. 

I presume that this may be the case for a lot of other students moving to the city of LA for college, whether at USC or even UCLA. In an effort to remedy this, I have decided to dive into LA addresses data to investigate the region. The aim is to try and find any patterns that may be interesting to me or other students and that may be helpful in simply discovering more about the area.

Graduate students and undergraduate students alike who aren’t familiar with the LA area and are not sure where they would like to live in, may benefit from this explorative project!

## Data
The [LA addresses data](https://catalog.data.gov/dataset/addresses-in-the-city-of-los-angeles) is sourced from [data.lacity.org](data.lacity.org) provided by the department: Bureau of Engineering. It is used in conjunction with [Foursquare location data](https://foursquare.com). 

## Methodology
After the data has been loaded and preprocessed, a call to the Foursquare API will be made to explore and segment the neighborhoods in LA. Foursquare's **explore** function will be utilized to get the most common venue categories (within a radius of 500 metres) in each neighborhood. This will then be aggregated with the neighborhood data and subsequently used to group the neighborhoods into clusters. The clustering algorithm of choice to complete this task will be the *k*-means. Finally, the Folium library will be used to visualize the neighborhoods and their emerging clusters.
