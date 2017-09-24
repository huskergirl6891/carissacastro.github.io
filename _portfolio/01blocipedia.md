---
layout: post
title: Blocipedia
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/blocipedia.png"
short-description: Blocipedia is a wiki application inspired by Wikipedia.

---
## Summary

Blocipedia is an application that allows users to create and edit wikis.  Users can also upgrade to a Premium account to create private wikis and add collaborators.

## Problem

The goal of the project was to develop an application that allows users to create, view, and edit wikis, similar to Wikipedia.  Anyone should be able to view public wikis, but users would need to sign up for a free account using a valid email address to create and edit wikis.  Users could also upgrade to a premium account to create private wikis and add other users as collaborators to their private wikis.

## Solution

The application was built using Ruby on Rails with MVC architecture.  The first step of the project was to set up the various models.  I chose three models - User, Wiki, and Collaborator - to represent the data that would be stored for this application.  For user authentication, I used the [Devise](https://github.com/plataformatec/devise) gem to set up the User model, views and controller that allows users to sign up for Blocipedia.  I also used the Devise gem to incorporate email confirmation, as well as allowing registered users to sign in and out of the application.  For the Wiki resource, I implemented standard CRUD operations through the controller and associated views.  This included a main index view to display all wikis, a show view to display an individual wiki, and new/edit views with forms to allow users to create and edit wikis.  For the text forms, I used the [Redcarpet](https://github.com/vmg/redcarpet) gem to parse Markdown syntax.

To ensure users had appropriate access based upon their role (guest, standard, premium, or admin), I used the [Pundit](https://github.com/elabs/pundit) gem, which uses policy classes to only allow controller actions based upon defined roles.  For upgrading users to a premium account, I integrated [Stripe](https://stripe.com/) using the Stripe gem and API.  For premium accounts, privacy controls were put in place to ensure only premium or admin users had access to change a wiki's private attribute.  To allow premium users to add other users as collaborators to private wikis, I used the Collaborator model to relate wikis and users through a Has Many Throughs relationship.  ActiveRecord was used for all of these associations.

## Results

The final application met all of the user requirements and worked as intended.  Test-driven development was done using [RSpec](http://rspec.info/), and I used the [Faker](https://github.com/stympy/faker) gem to seed the development database for easier visual testing as features were added.

## Conclusion

Overall, Blocipedia is my favorite project so far.  I loved developing a project that used a database for real-time data manipulation, and I really enjoyed working with Ruby on Rails.  While it was good to learn how to implement several of these features from scratch in previous smaller projects, I enjoyed working with several gems that had common features already implemented.  At the same time, I was surprised at how hard it was to incorporate some of the gems.  Some had better documentation than others, but even ones with great resources don't always cover every issue that might come up.  I had to spend a lot of time looking up examples of how others used the gem.  One of the biggest issues came up while trying to get some of my RSpec tests to pass.  After doing some research online and talking with my mentor, I was able to narrow down the problem to some compatibility issues with RSpec and Devise.  I ended up having to modify my testing plan, and do some manual testing on the controller actions that were impacted by Devise.  Despite this setback, I am proud of the end result and look forward to using Ruby on Rails to build more applications!
