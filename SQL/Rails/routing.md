# Routing
---
HTTP request arrives from client... 
...now what? 

Someone needs to tell the controller which action/method to run. This is where the **router** comes in. 

The **router** sees the HTTP verb and the URL and matches it to the controller action that should be taken. 

If no appropriate route is available, an error is thrown. 

When a request enters your Rails app, Rails will automatically group together all of the parameters in a hash called `params`. 

Routes file for the Rails app should be located in 
`config/routes.rb`

Typing `rails routes` into the command line will output all the available routes. 
&nbsp;

- Root URL is the most important route
`root to: "pancakes#index"` => controller = pancakes, index = action

- Rails writes RESTful routes
```Ruby
# in config/routes.rb
...
resources :name_of_resource
...
```

If you don't want all seven routes, specify using `only` or `except`
```Ruby
resources :posts, only [:index, :show]
resources :users, except [:index]
```
&nbsp;
