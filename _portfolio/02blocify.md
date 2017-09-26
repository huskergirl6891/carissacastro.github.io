---
layout: post
title: Blocify
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/blocify.png"
short-description: Blocify uses machine learning to predict favorite songs.

---
## Summary

Blocify is an application that uses machine learning to predict if a song will be liked by a user.

## Problem

The main goal of the project was to develop an application that used machine learning to solve a problem.  As my capstone web development project, I had the freedom to select the scope of the entire project and wanted to learn about the basics of machine learning as well as the details of how to incorporate a machine learning model into a Rails application.  After creating and testing several types of models, I came up with the scope of predicting if a user would like a song.  The user would enter a song title and request a prediction.  The application would then display the results of the prediction in real time.

## Solution

The first part of the project was selecting a machine learning tool and developing the model.  After researching options, I chose [AWS Machine Learning](https://aws.amazon.com/machine-learning/?nc2=h_m1), as it is developer-friendly and has extensive documentation for the [machine learning service](http://docs.aws.amazon.com/machine-learning/latest/dg/tutorial.html).  I planned to build the application with Ruby on Rails, and the AWS [Rails API](http://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/MachineLearning.html) has good support for machine learning.  

The next step was finding data and creating a model.  I decided to use data from my own Spotify song preferences as the training source.  Spotify songs have several attributes such as "danceability", "key", and "tempo", which meant I didn't have to come up with my own attributes.  Also, songs used to generate predictions would have the same attributes and could easily be requested from Spotify.  Inspired by [this post](https://opendatascience.com/blog/a-machine-learning-deep-dive-into-my-spotify-data/), I wrote a Python script that uses Spotify's API and [Spotipy](https://github.com/plamere/spotipy), a Python library for Spotify, to pull several playlists with song data and writes everything to a CSV file, which is the format required by AWS.  I then rated each song with a 0 (don't like) or 1 (do like).  This CSV file was uploaded to AWS S3, and then I followed the steps to link the file to AWS Machine Learning.  The actual model creation took less than 5 minutes, and a summary and an evaluation of the model can be viewed through the AWS console.

Once the model was ready, I created the Rails application that would interface with AWS to generate a prediction.  The main part of the application is a simple form for entry of a song title.  Once the user enters the title, the input is used in a Spotify search API call, and the Spotify song and attributes are returned.  This song data is then passed to the AWS ML model through the open endpoint, and a real-time prediction, either 0 or 1, is returned and displayed as "Yes" or "No" to the user.  

To minimize repeat API calls to Spotify and AWS, I created a database for the application to store the song name and prediction result when the API calls are made.  The current list of predictions stored in the database is displayed for the user, and basic CRUD operations are available to manage the stored data.  The ability to create and delete endpoints with buttons was added to allow for the 2 -3 minute delay in the creation of the endpoint as well as to minimize the cost of leaving an endpoint open.

## Results

The final application met all of the initial goals and requirements and worked as intended.  One area for improvement would be in the quality of the model, which gave an accurate prediction ~50% of the time.  To improve this, a much larger training data set would likely be needed.

## Conclusion

Overall, this was such a fun project to develop.  One big reason was that I came up with the entire scope myself, which allowed me to explore the use of machine learning in a practical way.  I will be writing a post that goes into more detail about this early part of the project, including some of the exploratory work I did to learn AWS ML, but in general, this was my favorite part of the project. Machine learning is fascinating to me, and this allowed me to dive into using it, while learning basic concepts at the same time.  The application development for the API integration was challenging, especially since I needed two different API calls to work at the same time.  I was able to get each part working independently first, which made the integration step very simple.  While there are still many ways to improve the application, I'm proud of how my ideas came together and actually worked!
