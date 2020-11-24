---
layout: post
title:      "List App Project"
date:       2020-11-24 21:33:54 +0000
permalink:  list_app_project
---


My Javascript project was a simple list app that allows a user to create and delete lists and add in tasks. This was an app I'd been wanting to make for awhile and was glad I finally got a chance to do so with this project. 
<br>
<br>

After working with Rails so much in the last project, it was very easy to set up the backend and I spent the bulk of the project working with the frontend and navigaing the dom. It took me awhile to decide on a file structure and I ended up doing a lot of testing a long the way. One thing that really helped me was finding a simple way to clean up my test data and start fresh with my origional seeds. Up until you build out an apps  `delete`   functionality, the database can get messy with test data. 
<br> 

I used the following simple code to fix this problem: 
<br>


1. Add 'ModelName.delete_all'  to your 'db/seeds.rb' file for every model's data that you want to gone. 


My seeds file looked like this:
<br>
<br>

```
--> db/seeds.rb

List.delete_all
Item.delete_all

// seeds data goes on the lines below

```
<br>

2. Then run the following code in the terminal

```
--> terminal 
rake db:seed
```
<br>
Thats it! The database was just completely whiped of all data and then repopulated with seed data.  Having this command handy was a really helped me during this project because I could test and debug  in browser without having to build out delete right away.  

<br>

<br>
