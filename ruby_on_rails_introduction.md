## [Ruby on rails introduction](https://rubyonrails.org/)
Rails is a web application development framework written in the Ruby programming language.
- Don't Repeat yourself(DRY)
- Convention Over Configuration

## Restful route

```
  resources :articles
```

~~~~ruby
bin/rails routes
       Prefix Verb   URI Pattern                  Controller#Action
welcome_index GET    /welcome/index(.:format)     welcome#index
     articles GET    /articles(.:format)          articles#index
              POST   /articles(.:format)          articles#create
  new_article GET    /articles/new(.:format)      articles#new
 edit_article GET    /articles/:id/edit(.:format) articles#edit
      article GET    /articles/:id(.:format)      articles#show
              PATCH  /articles/:id(.:format)      articles#update
              PUT    /articles/:id(.:format)      articles#update
              DELETE /articles/:id(.:format)      articles#destroy
         root GET    /                            welcome#index
~~~~
## MVC

![rails-achetecture](https://cdn-images-1.medium.com/max/1600/1*KK61kGXrkaFBDfY7uWukyQ.png)


ref: [**https://medium.freecodecamp.org/understanding-the-basics-of-ruby-on-rails-http-mvc-and-routes-359b8d809c7a**](https://medium.freecodecamp.org/understanding-the-basics-of-ruby-on-rails-http-mvc-and-routes-359b8d809c7a)


## Know about gem

Gem is a library.

[**RubyGems**](https://rubygems.org/) is the Ruby community’s gem hosting service

Example gem file

    gem 'rspec', '~> major,minor,patch'
    gem 'rspec', '~> 3.8.0'

```
# Tracking error
  airbrake

# Manage environment
  config

# Paginate
  bootstrap-kaminari-views
  kaminari
  kaminari-grape

# Form
  simple_form

# User Authorization
  devise
  cancancan
  has_secure_token

# Social Authorization 
  omiauth

# Cache
  redis

# Cron-job
  sidekiq

# Tracking error
  airbrake

# React with rails
  react-rails

# Document
  axlsx
  axlsx_rails
  prawn
  prawn-table
  roo

# service
  grape

```

```
Development, Test

awesome_print
better_errors
dotenv-rails
pry-byebug
rspec
rubocop
simplecov
vcr
```
