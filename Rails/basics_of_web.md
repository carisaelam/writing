# Basics of the web

---

### The basics of HTTP

- HTTP = _Hypertext Transfer Protocol_
- "Ask" and "Receive" conversation between browser and server
- Foundation of the modern web
- "Client" = browser
- Browser raises a request for content => server sends a response back to browser
- Request and response are both sent as text that is readable
- HTTP protocol is **stateless**. It doesn't hold onto information. Each HTTP request has to "carry" all of the necessary information with it. This info gets "carried" using something called **headers**.
- Default port for HTTP is port 80

|Version|Description|
|---------------|-------|
|HTTP/0.9|Original version; deprecated|
|HTTP/1.1|Revised in 2014; allows single request per TCP/IP connection|
|HTTP/2.0|Current edition; allows multiple simultaneous requests (multiplexing)|
  &nbsp;

- HTTP/2.0 allows browser to request the script and the style at the same time in a single TCP connection, making it much faster than previous iterations of the protocol 
- Requests are sent specified with **Uniform Resource Locators (URLs)** which points to the protocol, host(domain), port(often hidden), path, and query parameters. 
- URLs don't ***do*** anything. They are just a nicely packaged way to frame a request. 

**HTTP Requests**
Consists of 
1. Request line (verb, path, HTTP version) 
Example = `GET /articles/rails-basics HTTP/2.0`

2. Headers (addition info about message, requester, communication format)
Example = `Host: www.rails.com Connection: keep-alive Pragma: no-cache Accept: text/html, application/xhtml+xml`

3. Body (optional - content of the request, separated from the headers by a blank line)


  &nbsp;

**HTTP Responses**
Consists of
1. Status line (status code to describe success or failure, HTTP version, brief description)
2. Headers (additional info about response)
3. Body (optional - content; ex. binary data or HTML content of page)
Example response: 
`HTTP/2.0 200 OK`  
  &nbsp;

**Status Codes**
1**: Informational Messages 
2**: Successful 
3**: Redirection (client needs to take additional action)
4**: Client Error (invalid resource or bad request)
5**: Server Error 
  &nbsp;
  
**GET requests with Fetch**
```
let response = await fetch('https://somewebsite.com/blahblah.json')
let data = await response.json()
console.log(data)
```  
  &nbsp;

**POST requests with Fetch**
```
let response = await fetch('https://somewebsite.com/profile', {
  method: 'POST', 
  headers: {
    'Content-Type': 'application/json',
  }, 
  body: JSON.stringify(data), 
})

if (! response.ok) {
  console.log(`POST failed with status ${response.status}`)
}
```
  &nbsp;
  
  
 
### The 4 most commonly used HTTP verbs
**GET**: fetch resource from server; no body; URL carries all required info 

**POST**: create new resource; has optional payload 

**PUT**: update existing resource; has optional payload 

**DELETE**: deletes existing resource 



### The 7 RESTful routes of Rails
**REST** stands for *Representational State Transfer*
There are only seven things you would want to do to a resource via the web. Using a blog as an example: 
  1. GET all the posts ('index')
  2. GET a specific post ('show')
  3. GET the create post page ('new')
  4. POST the data you filled out for a new post ('create')
  5. GET the edit post page ('edit')
  6. PUT the edited data back to the server ('update')
  7. DELETE one specific post ('destroy')
  ** words in parentheses correspond to rails controller actions

This is "RESTful" thinking, and Rails is programmed to do this really well as long as your data and requests align with this model. 

&nbsp;

### The different components of a URL
**URL: `https://www.google.com/search?q=how+to+make+waffles`**
`https` = protocol 
`google.com` = domain 
`/search` = path 
`?q=how+to+make+waffles` = query/parameters

&nbsp;

### The basics of MVC
MVC ==> Organization 
**M**odel, **V**iew, **C**ontroller

Functions of a web application are split into these three parts, and each part is its own Ruby class. Such OOP. 

1. Browser makes a request
Example `http://somesite.com/video/show/20`

2. Server receives request and routes it to the correct controller as defined in the `config/routes.rb`. Server uses dispatcher to create a new controller, call the action, and give it the parameters. 

3. Controllers parse the requests and gives orders to the models

4. Models are Ruby classes that communicate with the database, store data, validate data, etc. 

5. Views are the 'frontend'...what the user actually sees and can interact with. They are just displaying what the controller has given them. 

6. Controller returns the response to the server which sends HTTP response to user. 

***"Fat model, skinny controller"***




### APIs
**APIs are software-to-software interfaces**
User does not see the API in action, they just benefit from the results. 
If a server wants data from another website, it asks for it using the website's API. 
An API is just the way two applications talk to one another. 


### Cookies
**Cookies** help websites remember who you are across multiple requests 
Because requests are completely independent, they don't have a way on their own of all linking together under one pot that represents you. 
Your browsers sends cookies to the website with each request. 
This is how websites maintain a form of "state" 
Without cookies, you would have to re-login to websites after every single request. 

### Authentication vs. Authorization 
**Authentication** - determining who the user is by retrieving the cookie they send you and using it to find the user in your database

**Authorization** - limits what the user can see based on their permission level 

## Helpful links

[The Odin Project: A Railsy Web Refresher](https://www.theodinproject.com/lessons/ruby-on-rails-a-railsy-web-refresher)
[HTTP Basics Article by Pavan Podila](https://code.tutsplus.com/http-the-protocol-every-web-developer-must-know-part-1--net-31177t)
&nbsp;
[Explanation of MVC](https://betterexplained.com/articles/intermediate-rails-understanding-models-views-and-controllers/)
