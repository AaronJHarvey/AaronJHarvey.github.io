---
layout: post
title:      "Javascript and Rails"
date:       2020-11-19 01:11:33 +0000
permalink:  javascript_and_rails
---

What a period it has been since the last project. Personally and in terms of the world sometimes it felt like everything and everyone was going off the rails...pun intended and at times it made it difficult to focus on learning. Nonetheless I took it in stride and learned what it takes to function in Javascript. 

When it came planning my project I somehow simultaneously had a million ideas and no ideas. That's the beautiful (and scary) thing about JavaScript you can do just about anything you can think of. Ultimately, because I wanted to make something practical and something that honestly could help me pretty immediately if I wanted to use it I made a gift list keeper. What that means is my project allows a user to input the name of a gift they are planning to purchase, the store they can purchase it, and choose the person they want to purchase it for, from there it renders a list of all the items you have added to the list along with the store and the intended recipient. 

In order to accomplish this I had to first build a back end MVC app that allows these new items to be created and associated properly. Once this is done I published it as an API by rendering it as JSON data, this will later allow me to pull that data and use it in my Javascript code and make it usable for the user. Once I had MVC app created and working I then turned to the Javascript. Where I needed to begin with an event listener so the page would render data when it recognized that it was loaded. I needed to give it information to render which is where the getGifts function went to the above mentioned API and gathered the information found there assigning the attributes to their respective pieces of the gifts already in the database. 

However in order to have the capabilities for a user to add to the database thus adding to their giftlist I needed to create a form that would use the inputted information from the user and assign it to the appropriate categories in the database. To do this I created a form handler that would target each of the needed id's in the form and hold on to the data until it was needed during the postFetch function which sends those data pieces to the database. 


