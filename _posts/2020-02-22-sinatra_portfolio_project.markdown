---
layout: post
title:      "Sinatra Portfolio Project - Tux"
date:       2020-02-22 09:37:39 -0500
permalink:  sinatra_portfolio_project
---


I decided to revolve my project around something travel related, and created a Travel CRUD app where the user can keep track of their destinations and add a log about it. A user fills out the destination and content, then they can: sign up, log in, see all their destinations, create destinations and edit them. They shoudn't be able to edit other users' pages and I attempted to use bcrypt to secure their password, as well as make sure the user is authenticated. I wanted to make it as simple as I can (MVP) so that I will get the understanding that Flatiron school expects of me. When I'm a little more comfortable, I'll definitely dive into it more. 

As with the first project, watching instructors create a project from start to finish, reading other projects and such has been the biggest help. In starting, I think it's best for me to start from the outside in, which includes the overview of the project and what I want it to do, working on the models and the database, then the views and controllers. I will try to be more independent in creating my next one, and attempt to stop using the training wheels provided by Flatiron School. 

Overall this was an awesome experience creating a simple Sinatra CRUD app, and I will definitely try to enhance this project after submission to advance my understanding behind it. I believe I have a good understanding of Sinatra, ActiveRecord, etc., and will need to solidify my understanding. The only thing worrying me at this stage in the curriculum is I have so much to learn, and getting stuck can be a major letdown and give me doubts for the future. However, I see that I am making progress in my goal to learn software engineering.

### Tux

Tux is a Ruby gem that starts a console for the sinatra app and loads an environment for your project. In the tux console you can access your database, instantiate your classes, test associations and methods, and perform CRUD actions all through the terminal to test the code for your app and ensure things are working the way you want them to. 

First install the gem: 

`gem install tux`

Require it in your Gemfile:

`gem 'tux'`

In the terminal, make sure you're in the project directory and run bundle install:

`bundle install`

And in the directory of your app run tux in the terminal:

`tux`

In the tux console, you can use ActiveRecord and Ruby methods, which is great to try and understand the associations between the model classes. 

I see I have access to my database, can instantiate new destination or user objects, and delete and edit them just as I can through the web browser, and perform CRUD actions. I can test out all the ActiveRecord and Sinatra methods in my project. When first entering the tux console, I entered `destination = Destination.last` to see the last destination created, which gave me:

`=> #<Destination id: 24, destination: "test", content: "test", user_id: 8, created_at: "2020-03-02 16:53:12", updated_at: "2020-03-02 16:53:12">`

I knew this was created during the assessment, and then I typed `destination.methods` to see how many methods are available to use for my Destination class that was inherited by ActiveRecord. A huge array of methods were given! I recognized a few of them and ran `destination.valid? => true` and ran `destination._validators` which gave:

`=> {:destination=>[#<ActiveRecord::Validations::PresenceValidator:0x00007fed9a58e2d0 @attributes=[:destination], @options={}>], :content=>[#<ActiveRecord::Validations::PresenceValidator:0x00007fed9a58d880 @attributes=[:content], @options={}>]}`

During the assessment, we added presence validations for the destination and content attributes in the Destination class, and I see that the presence validators are there for both of them.

I then used the `.first` method on a destination: `destination = Destination.first` which returned the first destination that is currently in the database:  

`=> #<Destination id: 6, destination: "Peru", content: "I'm here in Lima!!!", user_id: 4, created_at: "2020-02-28 20:17:37", updated_at: "2020-02-28 20:21:31">`

I ran `destination.content` which returned the string `=> "I'm here in Lima!!!"` from that user, and ran `destination.user` which returned the instance of the user that created the content:

`=> #<User id: 4, username: "Vicky", password_digest: "$2a$12$6eT6MFakTryM0s3SUl6QGu50p3riP6Bkysolu10GCqQ...", created_at: "2020-02-28 17:03:20", updated_at: "2020-02-28 17:03:20">`

Then I ran `destination.user.username` which gave the username of `=> "Vicky"`. 

Using tux was very helpful in understanding the associations between my models and testing the code I can use in creating them in my controllers as well as in my models.

