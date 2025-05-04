# HTTP
- Foundational protocol fo the World Wide Web
- Governs how web browsers (clients) and web servers communicate

## Client-Server Model
- Client: Typically your web browser or any application that needs to access web resources
- ***Client*** initiates the communication by sending a request to the server
- ***Server*** This is a computer program running on a machine that hosts website files (HTML, CSS, JavaScript, images, etc)
- The server listens for client requests and sends back a response
## Stateless Protocol
- Each request form a client to the server is treated as a completely independent transaction
- The server doesn't remember anything about previous requests form the same client
- If the server needs to maintain information about a user's session, this state is typically managed by thte application itself...
- ...using mechanisms like cookies, session IDs in URLs, or other techniques, and this information is sent with each request
- *Benefit*: Statelessness makes the server simpler, scalable, and reliable -  it doesn't need to keep track of numerous client sessions
## Requests and Responses
- The core of HTTP communication involves two main types of messages:
    1. *requests* sent by the client
    2. *responses* sent back by the server

## HTTP Request:
#### An HTTP request sent by a client contains several components:
- HTTP Method (Verb): Indicates the action the client wants the server to perform on a resource. Common methods include:
- GET: Retrieve data from a specified resource.
- POST: Submit data to be processed to a specified resource (often used for creating new resources or submitting forms).   
- PUT: Update an existing resource (often replacing the entire resource).
- DELETE: Delete a specified resource.
- PATCH: Partially update a resource.
- HEAD: Similar to GET, but only retrieves the headers, not the body.
- (There are other less commonly used methods as well).
#### URL (Uniform Resource Locator):
- Specifies the resource the client wants to access on the server (e.g., https://www.example.com/products/123).
- HTTP Version: Indicates the version of the HTTP protocol being used (e.g., HTTP/1.1, HTTP/2, HTTP/3).
- Request Headers: Provide additional information about the request, the client, or the desired response format. Examples include:
- User-Agent: Identifies the client software (e.g., browser name and version).
- Accept: Specifies the media types the client can understand (e.g., text/html, application/json).
- Accept-Language: Indicates the preferred languages for the response.
- Cookie: Contains cookies sent by the client to the server.
- Request Body (Optional): Contains data sent to the server (e.g., form data in a POST request, JSON data in an API request).
 
## HTTP Response:
#### An HTTP response sent by the server back to the client contains:
- HTTP Version: Indicates the HTTP version used by the server.
- Status Code: A three-digit code that indicates the outcome of the request. Common status codes include:
  - 200 OK: The request was successful.
  - 201 Created: The request was successful, and a new resource was created.   
  - 404 Not Found: The requested resource could not be found.
  - 500 Internal Server Error: The server encountered an error while processing the request.   
  - (There are many other status codes categorized by their first digit: 1xx informational, 2xx success, 3xx redirection, 4xx client error, 5xx server error).
- Response Headers: Provide additional information about the response, the server, or the content being sent. Examples include:
- Content-Type: Specifies the media type of the response body (e.g., text/html, application/json, image/jpeg).
- Content-Length: Indicates the size of the response body.
- Set-Cookie: Instructs the client to store a cookie.
- Server: Identifies the server software.
- Response Body (Optional): Contains the actual content requested by the client (e.g., the HTML of a webpage, JSON data from an API, an image file).

## URLs (Uniform Resource Locators)
- URLs are the addresses of resources on the web
- They tell the browser where to find the requested content
- A basic URL structure is: `protocol://hostname[:port]/path?query#fragment`
  - **protocol**: The scheme used to access the resource (e.g. `http`, `https`)
  - **hostname**: The domain name or IP address of the server
  - **port**: The port number on the server to connect to (default is 80 for HTTP, 443 for HTTPS)
  - **path**: The specific location of the resource on the server
  - **query**: Parameters passed to the server
  - **fragment**: A reference to a specific part within the document

## HTTP Versions
- HTTP has evolved over time and there are different versions (HTTP 1.0, 1.1, 2, 3)
- HTTPS is not a separate protocol, but rather HTTP over TLS/SSL (Transport Layer Security/Secure Sockets Layer)
