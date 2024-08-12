# Views

The **V** in MVC
The **view** is basically boilerplate HTML that you stick variables from the controller into before sending it to the browser.

In a Rails project, views can be found at this location:
`app/views/controller_name/action_name.html.erb`
`controller_name` = name of the controller
`action_name` = method inside the controller that ran right before the render

**Layouts** hold the basic tags and elements that are needed in all of the webpages. It is like the shell around each page. The `yield` method represents the spot where the view template gets inserted. 
Examples include `<HEAD>` tags, `<DOCTYPE>` declaration, navbars, footers, etc. 

An example layout: 
```Ruby 
<!DOCTYPE html>
<html>
  <head>
    <title>MyFirstRailsApp</title>
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>

    <%= stylesheet_link_tag "application", "data-turbo-track": "reload" %>
    <%= javascript_importmap_tags %>
  </head>

  <body>
    <%= yield %>
  </body>
</html>

```

**Embedded Ruby** (ERB) is the HTML with the `<%=` `%>` tags. Everything inside the tags gets executed as if it was normal Ruby. 
Example
```Ruby
@user = {"first_name": "joe", "last_name": "smith" }

<%=@user.first_name %> = "joe"
```

**Differences between the tags**
`<%` = executes the code but doesn't display anything in HTML 
`<%=` = executes the code AND displays in HTML 
`<%#` = comment 

ERB is a **preprocessor**. It is processed and done before the final HTML is sent to the browser. 