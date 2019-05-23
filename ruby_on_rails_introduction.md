## [Ruby on rails introduction](https://rubyonrails.org/)
Rails is a web application development framework written in the Ruby programming language.
- Don't Repeat yourself(DRY)
- Convention Over Configuration

## Top command in ruby on rails
~~~~ruby
 rails new `- your name -` #rails new blog -d=postgresql
 rails generate controller `-your name-` #rails -g controller blogs
 rails generate model `-your name`- #rails -g model blog
 rails generate migration `-your name-` #rails -g createPostModel
 rails generate scaffold `-your name-`#rails -g scaffold blogs

 rails server
 rails route
 rails console

 rails db:create
 rails db:migrate
 rails db:drop
 rails db:rollback 
 rails db:schema:load

 rspec # BDD test development
 binding.pry # debugger

~~~~
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


ref: [https://medium.freecodecamp.org/understanding-the-basics-of-ruby-on-rails-http-mvc-and-routes-359b8d809c7a](https://medium.freecodecamp.org/understanding-the-basics-of-ruby-on-rails-http-mvc-and-routes-359b8d809c7a)


## Know about gem

Gem is a library.

[**RubyGems**](https://rubygems.org/) is the Ruby community’s gem hosting service

Example gem file

    gem 'rspec', '~> major,minor,patch'
    gem 'rspec', '~> 3.8.0'


### \# Tracking error
  - [airbrake](https://github.com/airbrake/airbrake/)

### \# Manage environment
  - [config](https://github.com/railsconfig/config/)

### \# Paginate
  - [bootstrap-kaminari-views](https://github.com/matenia/bootstrap-kaminari-views/)
  - [kaminari](https://github.com/kaminari/kaminari/)
  - [kaminari-grape](https://github.com/kaminari/kaminari-grape/)

### \# Form
  - [simple_form](https://rubygems.org/gems/simple_form)

### \# User Authorization
  - [devise](https://github.com/plataformatec/devise/)
  - [cancancan](https://rubygems.org/gems/cancancan)
  - [has_secure_token](https://github.com/robertomiranda/has_secure_token/)

### \# Social Authorization 
  - [omniauth](https://github.com/omniauth/omniauth/)

### \# Cache
  - [redis](https://github.com/redis/redis-rb/)

### \# Cron-job
  - [sidekiq](https://github.com/mperham/sidekiq/)

### \# React with rails
  - [react-rails](https://github.com/reactjs/react-rails/)

### \# Document
  - [axlsx](https://github.com/randym/axlsx/)
  - [axlsx_rails](https://github.com/straydogstudio/axlsx_rails/)
  - [prawn](https://github.com/prawnpdf/prawn/)
  - [prawn-table](https://github.com/prawnpdf/prawn-table/)
  - [roo](https://github.com/roo-rb/roo/)

### \# Breadcrumbs navigation
  - [breadcrumbs_on_rails](https://rubygems.org/gems/breadcrumbs_on_rails)

### \# service
  - [grape](https://github.com/ruby-grape/grape/)


# Development, Test

### \# Pretty print your Ruby objects with style
  - [awesome_print](https://github.com/awesome-print/awesome_print/)
  - [better_errors](https://github.com/BetterErrors/better_errors/)

### \# Loading .env
  - [dotenv-rails](https://github.com/bkeepers/dotenv/)

### \# Debugger
  - [pry-byebug](https://rubygems.org/gems/pry-byebug)

### \# BDD
  - [rspec](https://github.com/rspec/rspec/)

### \# Best practice rules
  - [rubocop](https://github.com/rubocop-hq/rubocop/)

### \# monitor test coverage
  - [simplecov](https://rubygems.org/gems/simplecov)

### \# mock request
  - [vcr](https://github.com/vcr/vcr/)

