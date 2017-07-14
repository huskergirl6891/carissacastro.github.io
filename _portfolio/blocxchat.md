---
layout: post
title: BlocChat
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/blocchat_1x_02.png"
short-description: BlocChat is a messaging application built with AngularJS and Firebase.

---
## Summary

BlocChat is a messaging application built with AngularJS and Firebase.  This application allows users to create chat rooms and post messages within different rooms.  Message information is stored to a Firebase Realtime Database.

## Problem

The goal of the project was to create a new chat room application that sends and receives messages in real time.  The application needed to prompt users to set a username and to display a list of available chat rooms.  Users could also create a new chat room, as well as post messages to any chat room.

## Solution

The first step of the project was to set up the initial layout using HTML and CSS to include a side menu to display available chat rooms and a main messaging area to display all messages saved in the selected chat room.  A small text input area was added at the bottom for users to type in messages.  For styling, I included normalize.css to minimize the potential impact of different browsers being used.  I also used [UI Bootstrap](http://angular-ui.github.io/bootstrap/versioned-docs/2.5.0/#!#modal) and [Bootstrap CSS](http://getbootstrap.com/css/) to take advantage of the grid system, modals, and other styling features to create a responsive, clean layout.

The application was built using AngularJS, and [UI-Router](https://ui-router.github.io/ng1/docs/0.4.2/index.html#/api/ui.router) was added for switching views.  To store all of the room and message data, I set up a Firebase Realtime Database and included AngularFire for AngularJS binding to Firebase.  Within Firebase, I used a flattened data structure for more efficient, faster loading by associating each message with a room ID and username instead of nesting.  Angular factories were used to define all API queries to the Firebase database.  This included AngularFire methods to retrieve current room and message data and add rooms and messages.  To create a unobtrusive way for a user to create a new room or enter a username, modals were implemented using UI Bootstrap's $uibmodal service.  For username storage, cookies were used by including the Angular cookie module.  

## Results

The final application met all of the user requirements and worked as intended.  Testing was done throughout the implementation process as new features were added.  

## Conclusion

Overall, BlocChat was an interesting project, and I enjoyed getting to learn several new tools.  One of the most challenge parts was figuring out how to implement the first Bootstrap modal for creating a new room, and it required a lot of research and reading through documentation and example implementations.  I found several different ways to implement the modal, and at first, this made it harder to understand how each part functioned.  Eventually, after trying out several different approaches, I found a solution that worked.  Implementing the second modal for entering a username was much easier since I had a much better understanding of how to implement it.  One lesson I learned was the value of Bootstrap CSS.  This saved me a lot of time with styling, and I enjoyed trying out the various features.  I will definitely be using many of these tools on future projects!
