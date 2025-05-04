# REST
- Representational State Transfer:
- Think of REST as a set of architectural principles – like guidelines or best practices for designing networked applications
- It's not a strict protocol like HTTP itself, but rather a style that leverages existing protocols (primarily HTTP) in a specific way.
## Key Principles of REST - Six guiding constraints
#### Client-Server
- The client and server operate independently
- The client initiates requests, and server processes them and sends back responses
- This separation allows the client and server to evolve independently without affecting each other
- For example: you can change the server-side database without needing to update all the mobile apps immediately
#### Stateless
- Each request from a client to the server must contain all the information needed to understand the request
- The server does not store any client state between requests - each request is treated as independent.
- If the server needs to know about previous interactions, the client must send that information in each subsequent request
- **Benefit**: This makes the server simpler, more scalable, and more reliable.  Servers don't have to remember the state of numberous clients
#### Cacheable
- Responses from the server should indicate whether they can be cached by the client or intermediary observers (like CDNs)
- If a response if cacheable, the client can reuse the cached data for subsequent identical requests, improving perfrimance and reducing server load
- HTTP provides mechanisms (like cache-control headers) to define caching policies
#### Layered Systems
- The client interacts with the end server but might not know if there are intermediate layers (like proxies, load balancers, security gateways) handling the requests
- These intermediary layers can perform various functions (caching, security, load balancing) without the client needing to be aware
- This adds flexibility and scalability to the architecture
#### Uniform Interface
- This is the most crucial principle and encompasses several aspects that make the API predicatable and easy to use
- **Resource Identification**: Resources are identified using URLs (Uniform Resource Locators)...these URLs should be consistent and intuitive (e.g. `/users`, `/products/123`, `/orders`)
- **Resource Manipulation through Representations**: Clients don't directly manipulate server-side data
- Instead, they exchange representations of resources
- Common representations include JSON, XML
- The client sends a representation to the server to update a resource, and the server sends back a representation of the resource's current state
- **Self-Descriptive Messages**: Each message should contain enough information to understand it
- This often involves using standard HTTP methods and media types (e.g. `Content-Type: application/json`)
- **Hypermedia as the Engine of Application State (HATEOAS) (Optional but ideal)** Responses shold contain links to other related resources or actions.  This allows clients to discover the available API capabilities dynamically without needing hardcoded URLs
- While often considered ideal, HATEOAS isn't always fully implemented in all RESTful APIs
#### Code on Demand (Optional)
- Servers can optionally send executable code (like JavaScript) to the client, which the client can then execute
- This extends client functionality but is less commonly used than the other principles

## How REST uses HTTP
- Restful APIs heavily rely on the standard HTTP methods to perform actions on resources:
#### HTTP Methods
- **GET**: Used to retrieve a representation for a resource (e.g. get information about a user)
- **POST**: Used to create a new resource (e.g. create a new user or submit an order)
- **PUT**: Used to update an existing resource, often replacing the entire resource with the provided representation
- **DELETE**: Used to delete a resource
- **PATCH**: Used to partially update an existing resource, modifying only specific attributes
#### HTTP Status Codes
- `200` for success
- `201` for created
- `404` Not Found
- `500` Internal Server Error
#### Benefits of using REST
- Simplicity - RESTful APIs are generally easier to understand and use
- Scalability - The stateless nature of REST makes it easier to scal server-side applications
- Flexibility - REST supports various data formats (JSON, XML, etc.)
- Interoperability - REST is widely adopted, making it easier for different systems and platforms to communicate
- Cacheability - LEveraging HTTP caching mechanisms improves performance and reduces server load
- Evolvability - The client-server separation allows both sides to evolve independently