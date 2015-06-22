##### Lighthouse Labs Web Immersion Class: Week 5 Day 1

# Rails

## Origin

The Rails framework was developed by David Heinemeier Hansson and released in 2004.

Hansson had been hired to develop a new web-based project management system for a company called 37signals. Using a then-obscure language called Ruby, Hansson developed the Rails framework to speed the development of the new application.  The project management tool would eventually become [Basecamp](https://basecamp.com/).

## Motivations

Rails is a very opinionated framework, as evidenced by its name.  It makes many of the low-level decisions for the programmer, allowing the programmer to focus on the logic for the task at hand.

Rails believes in:

- convention over configuration (CoC)
- don't repeat yourself (DRY)
- the active record pattern.
- Model-view-controller pattern

Much of this stems from the fact that web application architecture is complex and needs to be simplified to enable one person to rapidly develop complete web applications.

## Definition

Rails is a web application framework that favours convention over configuration.  It makes many low-level plumbing decisions with regards to databases and assets that allow the developer to focus on the business logic.

## Usage

To create a new project

```
rails new <project_name>
```

To launch the rails server; navigate to the new directory and enter

```
rails server
```

Rails generators allow to you generate new scaffolding, controllers, models, views and migrations, among other things.  To use a rails generator enter:

```
rails g <generator_name> <generator params>
```

For example to generate scaffolding for a new model enter:

```
rails g scaffold Contact email full_name
```

Important generators are:

- *scaffold*: generates the model, views and controller for a resource
- *controller*: generates a controller and its routes
- *model*: generates a model and its field, along with the migration
- *migration*: generates a migration file.  Includes schema changes if you name it correctly.

### Environments

Rails is configured out-of-the-box to run in three environments:

- *test*: used for running automated tests; the database will be created and destroyed constantly.  Here you can put additional instrumentation such as code coverage that allows you to see what lines of code are executed (not included by default).
- *development*: used to run the server on your local machine.  This environment is by default configured to not compile assets and connect to a local database.
- *production*: this environment fully processes your assets and will point to the production database, among other things.

### Routes

Rails has embraced RESTful API design and the generated HTTP routes reflect this.  Have a look at the ```resources``` routes helper and examine the routes that it generates.

In class we create a RESTful resource by adding:


```
#config/routes.rb

Rails.application.routes.draw do
  resources :contacts
end
```

Which effectively generated:

```
#config/routes.rb

Rails.application.routes.draw do
  get '/contacts' => 'contacts#index', :as => :contacts
  get '/contacts/new' => 'contacts#new', :as => :new_contact
  get '/contacts/:id/edit' => 'contacts#edit', :as => :edit_contact
  get '/contacts/:id' => 'contacts#show'
  post '/contacts' => 'contacts#create'
  patch '/contacts/:id' => 'contacts#update', :as => :contact
  delete '/contacts/:id' => 'contacts#destroy'
end
```

## Resources

The [Rails Guides](http://guides.rubyonrails.org) are a fantastic resource; I encourage you to read them end-to-end, at least quickly, to get a sense of what tools you have available to you.
