---
layout: default
title: Rails routes
parent: Rails
nav_order: 3
---

# Rails routes Cheatsheet

### Default format

```rb
get 'photos/:id', to: 'photos#show', defaults: { format: 'jpg' }

defaults format: :json do
  resources :photos
end
```

### Routes files

Create a new dicrectory `config/routes`

Add a routes file into this directory, for example `admin.rb`

```rb
# config/routes/admin.rb
namespace :admin
  roots 'users#index'
end
```

In the main routes file (`config/routes.rb`) we could import the routes file above like follow:

```rb
# config/routes.rb
draw :admin
```

### Listing routes

```sh
# List all routes
rails routes
rails routes --expanded # display in expanded table format

# Find routes by grep
rails routes -g new_comment
# is equivalent to
rails routes | grep new_comment

# Find routes by controller
rails routes -c users
rails routes -c admin/users
rails routes -c Comments
rails routes -c Articles::CommentsController
```

### References

- [Rails Routing from the Outside In](https://edgeguides.rubyonrails.org/routing.html)
