---
layout: post
title: GrammyPlus
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/blocipedia.png"
short-description: Blocipedia is a wiki application inspired by Wikipedia.

---
## Summary

GrammyPlus is an iOS app that allows users to log in to their Instagram account and then displays pictures from their feed in the app.

## Problem

The goal of the project was to create an iOS app that displays a picture from a user's Instagram feed.  Users need to be able to log in and out of their Instagram account, as well as be able to refresh the app to show the most recent picture from their feed.

## Solution

The application was built using Objective-C, and Cocoapods was included to utilize the OAuth2Client service.  The first step of the project was to set up the project as a single view application.  The main area of the view utilized the UIImageView component to display the Instagram feed picture.  An initial image was included within the app so it could display before a user logs into Instagram.  For the app to access Instagram, OAuth 2.0 was used for secure login, and a custom URL scheme was used to redirect back to the app after a user logs into their account.  Since the Instagram servers did not meet Apple's security standards, NSAppTransportSecurity was used to register specific exceptions for Instagram's websites.  For data retrieval from Instagram, a NSURL Session was used along with specific URL's for a user's feed from Instagram's API.    

## Results

The final application met all of the user requirements and worked as intended.  Testing was done using Xcode's simulator throughout the implementation process.

## Conclusion

Overall, this was one of my favorite iOS projects so far.  It was very interesting to learn how to use an API that is not deeply embedded into iOS, including some of the security challenges that this presents.  I learned a lot about the current state of security technology, and was a little surprised that even mainstream companies like Instagram are still not using the most advanced security standards available.  This project definitely made me more aware of these challenges, and I plan to use this learning in future apps.  
