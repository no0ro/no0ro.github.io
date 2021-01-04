---
layout: post
title:      "Kombucha Thoughts"
date:       2020-11-05 20:39:05 -0500
permalink:  kombucha_thoughts
---


For my Rails project I made a web app for kombucha drinkers to keep track of what they've drank, review and rate their drink experience, and then be able to view what other users think of the kombuchas as well.
<br>
<br>


When I started this project, Rails felt like a blur. I understood the parts of the program individually, but didn't fully understand how it all fit together. So I took it slow and tried to really understand what was happening behind the "magic".  
<br>

I choose not to use the popular Authentication Gem `Devise` in an effort to better understand the Login/Signup/Logout process and application of dreaded OmniAuth.  Much to my surprise, it turns out OmniAuth isn't very complicated, but just _very specific_. Specific to the provider (ie. Github, Google, Facebook, etc.) and specific to the exact code/formatting you need to use. For example, I ran into a bug in my `.env` file where I accidentally added a space between `CLIENT_ID` and `CLIENT_SECRET` and it completely haulted my progress for hours. 
<br>
<br>

In my project, I added Google and Github OmniAuth functionality. The implementation of OmniAuth is just more of what we've already been doing - sifting through a hash for specific key/value pairs which we assign to variables, and if all validations pass, we'll set the user's id to be the session id and log the user in. 
<br>
<br>

##### Here is how I got to the OmniAuth users hash:

1)  Explore the OmniAuth hash by placing a `byebug` in `SessionsController#omniauth`

```
# SessionsController 

def omniauth
    byebug
end 
```
<br>
_Dont forget to add byebug to your Gemfile if it is not already there_
```
# Gemfile 

gem 'byebug'

```

<br>
2) Once I hit the `byebug` I accessed the OmniAuth request via the `request` keyword (similar what we'd think of as `params`).  I referenced omniauth  by calling on the `.env` part of the request. So the full command to get to the user hash looks like this:
<br>
<br>

```
pp request.env['omniauth.auth]

```

<br>
_^^ TIP: `pp` stands for "pretty print" and it will format the hash so it's "human readable"_

<br>
<br>
3) I then added that code to my `SessionsController` in a `private` method so I could easily access my user hash. 
<br>

```
    private 

    def auth
        request.env['omniauth.auth']
    end
```




