---
layout: post
title:      "Ruby on Rails Project"
date:       2020-03-27 13:42:26 -0400
permalink:  ruby_on_rails_project
---


For this Ruby on Rails Project, I attempted to keep it simple in order to more easily grasp the concepts we're required to learn. I wanted to do a Gratitude Journal where a user has signup, login and logout capabilities through the app and Omniauth through Google, do full CRUD on their gratitudes and comment on other users' gratitudes. A Gratitude Journal is a simple habit of writing three things you're grateful for a few times a week. The idea behind this journal is to promote positive thinking, self-esteem, and improve resiliency to negative situations.

I started off the project by creating my users and authentication system through the Devise gem, and Omniauth through Google. Omniauth was a great experience, and it was really cool to see how it was done since so many apps and websites use the same system. The most troubling part was creating my models and figuring out their associations, more specifically the Join table. My three models are User, Gratitude, and Comment.

I figured there were many ways in going about creating a Join, but in keeping it simple I decided to create a Comment model. I'm already familiar with the has_many and belongs_to relationship from Sinatra. In this case, to have a `has_many :model, through: :model_two`  or many-to-many relationships, a join table is necessary and a Comment model would join the User to a Gratitude. One of the key requirements of a join table is having two belongs_to associations and in my case was: 

```
class Comment < ApplicationRecord
    belongs_to :user
    belongs_to :gratitude
end
```

This extends the functionality of the User and Gratitude models and provides the has_many through comments relationship. Methods such as `gratitude.comments` and `comments.gratitude` are possible with the Join table, A user can create and own many comments that they have on another gratitude. To try and further my understanding, I ran `rails c -s` in my project and checked my associations with my seeded data:

I assigned these variables to the first instantiated objects of each models:

`c = Comment.first`

`g = Gratitude.first`

`u = User.first`

Then, I checked my associations by calling:

```
c.user => #<User id: 1, email: "93geraldtee@gmail.com", created_at: "2020-03-25 01:59:13", updated_at: "2020-03-25 01:59:13"> 
```

This returned the first comment's User (Comment belongs_to User).

```
g.user => #<User id: 1, email: "93geraldtee@gmail.com", created_at: "2020-03-25 01:59:13", updated_at: "2020-03-25 01:59:13">
```

Returned the first Gratitude's User (Gratitude belongs_to User).

```
u.comments => #<ActiveRecord::Associations::CollectionProxy [#<Comment id: 1, content: "That's really great man!", user_id: 1, gratitude_id: 1, created_at: "2020-03-26 14:34:17", updated_at: "2020-03-26 14:34:17">, #<Comment id: 2, content: "This is a test!", user_id: 1, gratitude_id: 1, created_at: "2020-03-26 17:29:58", updated_at: "2020-03-26 17:29:58"> ...
```

This returned all the first User's comments that he posted, which indicates the join table and has_many through association. A User has many comments, through a post. Here you can see that the comment holds the foreign key of both the User and Gratitude models.

There was a few more concepts I had to grasp such as nested routes and scope methods, but overall, the join table and associations seemed to be the most important in understanding. Although it took a lot of debugging, practice and research to solidify the concepts, it was pretty eye-opening to research how complex concepts can get even when the idea of it seems straightforward.
