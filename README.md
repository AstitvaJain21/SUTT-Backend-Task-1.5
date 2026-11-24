# SUTT TASK 1.5

Understanding how backend server works, and a basic framework for a website using Django.

## Q1. What actually happens, step by step, when you type a URL into your browser and hit Enter?

1. The browser parsses the URL: It split the URL into prtocol, domain, and path.
2. The browser then checks if it is a known IP address (as IP is the medium through which we can access servers) , if it does not get an IP it asks DNS resolver for the address. 
3. Now the browser connects the server to a port(442 for HTTPS , 80 for HTTP) using a three way handshake. For HTTPS there is one more step in which the brwoser and server share some encription keys.
4. After a conection is established, the browser sends a HTTP request.
5. Now the server sends a HTTP response according to the request executing any backend logic if required.
6. Lastly the browser renders the page by processing HTML and CSS file.


## Q2.  What are the client and the server, and how do they talk to each other?

A client is a software that starts the conversation by sending a request. Common client can be web browsers.

A server is program that recieves the requests , process it and give a response.

Client and server communicate using a `request -> response` pattern. The process is:
- Client sends a request
- Server recieves the request
- Server process the request
- Server sends a response
- Client recieves the response

## Q3. What is HTTP? What's inside a request and a response?

HTTP stands for HyperText Transfer Protocol. It is the set of rules a client and server follow to exchange messages on the web.

A HTTP request is a message sent by client to server asking it too perform an action or an information. It contains:
1. A request line which specifies:
- Kind of action(GET, POST etc.)
- Path of action
- Version of HTTP model
2. Headers
3. Blank Line (seprates header from body)
4. Body (empty for GET and specifies changes for PUT or POST)

After receiving and processing the request, the server sends an HTTP response to the client. It contains:
1. Status line
- HTTP version
- Status Code
- Status message
2. Headers
3. Blank line (seprates header from body)
4. Body (content)


## Q4. What's the difference between GET and POST, and when would you use each?

### GET: Used to retrieve data
Example:
- Loading a website
- Search
- Filtering

### POST: Submit data / cause a change
Example:
- Uploading Files
- Creating a post or comment
- Submitting a like or vote

## Q5. What do status codes like 200, 302, 404 and 500 mean?

The first category of the status code specify the type of response:
- 2XX: Success
- 3XX: Redirection
- 4XX: Client Error
- 5XX: Server Error

Majorly used status code are:
- 200: OK (recieving some data)
- 201: Created (a post or comment)
- 204: No content (Deleting a data)
- 302: Found (the resource is temporarily at a different URL)
- 400: Bad request (invalid request) 
- 401: Unauthorised (not logged in or authorised)
- 403: Forbidden (logged in but not permitted)
- 404: Not Found (the URL is empty)
- 500: Internal Server Error (error hile processing data)
- 503: Service Unavailable (server is temporarily unable to handle requests)

## Q6. What jobs do HTML, CSS and JavaScript each do on a page?

- HTML: Builds a framework for the webpage 
- CSS: Helps in making the Webpage look good
- JavaScript: Makes the webpage interactive (like buttons etc.)

## Q7. How does a website remember who you are between pages? (Look up cookies and sessions.)

HTTP has no memory. HTTP does not remember previous request sso in every request instead of doing everything all again cookies are stored in a browser and session are stored in server to resolve this.

Cookies are small piece of information stored by a browser. as a `name-value` pair. Whenever a new request is initiated cookies relevent to the request are shared with it.

Session is a way by which a server stores all the information about a user's interaction in a website. 

When a request in generated the server sends a response along with a session ID stored in a cookie. And session acts as a logbook of what the user did during that particular session.

## Q8. In Django, how does a request travel through URLs, views, models and templates before a response comes back?

When a request is generated i.e. you enter a URL in browser with domain `http://127.0.0.1:8000...` which points to our computer. Then the following process is followed:
1. `urls.py`: when a URL is entered, Django opens mysite/urls.py and look for the website in it and as soon as the URL matches it calles the corresponding views.
2. `views.py`: views acts as a coordinator and recieves the request and process the input by redirecting it to the respective program
3. `models.py`: When data is needed to modified view calls model.
4. `template`: view return the data in HTML form to present it in a form like tabular template is called.

## Q9. Why did the tutorial add {% csrf_token %} to the voting form?

It is added to protect the site from CSRF which is an attack from a malicious site which tries to perform unwated task in our site.