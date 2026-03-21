# HTTP Basics

## What is HTTP

In a simplified way, HTTP is the “language” systems use to communicate with each other on the web.

The websites and applications we use daily rely on constant data exchange between clients and servers.

To make sure browsers, APIs and integrations understand each other, HTTP defines how this communication should happen.


## Request and Response

Once we have a protocol that defines how communication should happen, the next step is understanding how this exchange works in practice.

In HTTP communication, there are two main components: the client and the server.

The client sends a request, and the server returns a response.

The request contains information that allows the server to understand:

- who is making the request  
- what action is being requested  
- which data should be retrieved or modified  

The response contains:

- the status of the request  
- the requested data (when applicable)  

Even though this flow seems simple, many integration issues originate at this level, such as malformed requests, missing data or incorrect assumptions between systems.



## What can go wrong

Even in this simple request-response flow, several issues can happen and impact system behavior:

- Malformed requests (invalid structure, missing fields or incorrect data types)
- Authentication or authorization failures (missing or invalid credentials)
- Network issues (timeouts, connectivity problems)
- Miscommunication between systems (different expectations about data format or behavior)
- Unexpected server errors (failures during request processing)

Understanding these failure points is essential when diagnosing issues in APIs and integrations.

Most issues in integrations are not caused by a single failure, but by small mismatches between request and response expectations.

## HTTP Methods

HTTP communication allows applications to perform CRUD operations on data — create, read, update and delete.

The type of operation is defined by the HTTP method used in the request.

There are several HTTP methods, but in the context of web systems and integrations, the most commonly used are:

- GET → retrieve data  
- POST → create or send data  
- PUT/PATCH → update data  
- DELETE → remove data  

PUT is typically used to replace the entire resource, meaning all fields should be provided in the request.

PATCH is used for partial updates, modifying only specific fields.



## Methods in practice (troubleshooting perspective)

When working with APIs and integrations, each HTTP method has its own common failure patterns.

### GET

GET requests are often affected by caching behavior.

Common issues include:

- Dynamic data being cached for too long, resulting in outdated responses  
- Static data not being cached, causing unnecessary load on the server  
- Inconsistent responses due to intermediate layers (CDNs, gateways)



### POST

POST requests are usually responsible for creating new resources and depends on server-side validation.

Common issues include:

- Invalid or unexpected payload structure  
- Missing required fields  
- Incorrect data types  
- Requests failing due to validation rules  

In addition, POST operations often require specific permissions, so authentication and authorization errors are also common.



### PUT / PATCH

Update operations can fail due to inconsistencies between what the client sends and what the server expects.

Common issues include:

- Sending incomplete data in PUT requests  
- Overwriting fields unintentionally  
- Partial updates not being applied correctly  
- Conflicts with existing data  



### DELETE

DELETE operations are usually straightforward, but can still fail due to:

- Missing permissions  
- Attempts to delete non-existent resources  
- Constraints or dependencies preventing deletion  



Understanding how each method behaves - and how it can fail - is essential when diagnosing issues in APIs and integrations.
