---
layout: post
title:      "Understanding_of_Authenticate.authenticate"
date:       2020-07-27 02:26:42 +0000
permalink:  understanding_of_authenticate_authenticate
---


Upon looking back at my project, the choices I made, and doing my overall review there was one major concept that I felt like I didn't fully understand why I did it or really how it worked, that's the .authenticate method. After researching it some more I think that it's almost such a self explanatory and easy concept that I wanted to over complicate it for myself.

Basically, whenever we are writing the code for an app that will allow the user to create something unique to them the best way to do that is to get the user to register a profile. We then want to make sure that user 1 can only make changes to the items that belong to them and not to user 2 so we would write in logic making sure the user associated with the thing is the one logged in before they could make any edits. However, that logic doesn't do any good if the login logic is flawed and will allow anyone to pose as the user, that is where SecurePassword and .authenticate come into play. 

When the user signs up for our app typically we will want to require they use something to identify them such as an email or username as well as have them create a password that allows us to verify the person logging in is actually the person behind that profile. In order to add an extra layer of protection and to prevent storing plain text passwords we encrypt the password using the Bcrypt gem. By installing this gem we gain access to has_secure_password which adds the .authenticate method to our app. When we are having a user login we would then use the .authenticate method to check the inputted password (however we code the logic to take that input in as an argument) against the password that is encrypted for that user, if they match then we allow the user to login and give them the ability to make changes to thier items, otherwise we give some error message and/or ask the user try again. 


