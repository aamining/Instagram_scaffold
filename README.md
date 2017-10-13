# README
# Instagram By Scaffold and references (association)
# eg. $ rails g scaffold Table_name description:text user:assosiation

Scope of work:

Making two tables 'User' and 'Comments'.

'Comments' are linked to 'user id'

first we need to login as a user so we have to log in by eg. devise gem

1- add to gem files

```
gem 'devise'

```

2- bundle install

3-
```
rails generate devise:install
```

4- Copy in to :config/environments/development.rb

```
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```
5-
```
rails g devise User
```
6- Now we add 'Comment' table by scaffold

```
rails g scaffold Comment description:text user:references
```
7- we have to delete the field of User_id

from: 'comments > form.html.erb

delete the user_id field which is waiting to be filled by user_id

this sort of field generating by scaffold and are avoidable just by this way.

8- NOW

'''
rake db:migrate
'''

9- add 'has_many :comments' to user model

10- add this to comments control, create methode

'''
@comment.user_id = current_user.id
'''

11- to be able to see who is this comment belong to we have to do this change in views> comments>show.html.erb

from:

<%= @comment.user%>

to:

<%= @comment.user.email %>
