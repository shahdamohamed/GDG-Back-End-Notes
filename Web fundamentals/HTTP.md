# What Is the Internet vs the Web

## Definition and Key Difference

| Concept | Definition | Example |
|----------|-------------|----------|
| **Internet** | The **global network** of connected computers and devices that can communicate with each other. It’s the physical and virtual **infrastructure** — cables, routers, servers, satellites, etc. | Sending an email, using WhatsApp, or connecting to Wi-Fi all use the Internet. |
| **Web (World Wide Web)** | A **service** that runs **on top of the Internet**, made up of websites and web pages linked together using **HTTP/HTTPS**. | Visiting `www.youtube.com` or `www.wikipedia.org` uses the Web. |

---

## Simple Explanation
- The **Internet** is the **network itself** — the wires, routers, and data connections that link millions of computers worldwide.  
- The **Web** (or **WWW**) is just **one of the services** that uses the Internet to send and receive data — specifically websites and web pages.

> The Web **depends on the Internet**, but the Internet **can exist without the Web**.

---

## Example
- Sending a **WhatsApp message** or playing an **online game** → uses the **Internet**, not the Web.  
- Opening **www.google.com** → uses the **Web**, through your browser.

---

## How They Work Together
1. You connect your device to the **Internet** (via Wi-Fi, mobile data, etc.).  
2. You open a **browser** (like Chrome).  
3. The browser uses **HTTP or HTTPS** to access information stored on **web servers**.  
4. That’s how you access a website — through the **Web**, using the **Internet**.

---


# What is HTTP

HTTP (Hypertext Transfer Protocol) is the foundational protocol used for transmitting data over the web. It allows communication between a client (like a web browser) and a server, enabling the transfer of web pages, images, videos, and other resources. Here's a breakdown of HTTP and how it is started.

## Types of HTTP Messages:
1. HTTP Request.
2. HTTP Responses.

---

## 1. HTTP Request Message

The client (such as a web browser) sends an HTTP request message to a server, asking for a resource (like a web page, image, etc.).

#### - Example of an HTTP Request:
```http
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html
```

### Components of an HTTP Request Message:
- **Request Line:** Contains three main elements:
  - **HTTP Method:** Specifies the action the client wants to perform (e.g., GET, POST, PUT, DELETE).
  - **URI (Uniform Resource Identifier):** Specifies the resource being requested (e.g., /index.html).
  - **HTTP Version:** Specifies the version of HTTP being used (e.g., HTTP/1.1).
  
- **Headers:** Provide additional information about the request, such as:
  - **Host:** Specifies the domain name of the server (e.g., `Host: www.example.com`).
  - **User-Agent:** Identifies the client software (e.g., browser or other application).
  - **Accept:** Specifies what types of media (e.g., HTML, JSON) the client can accept.
  - **Content-Type:** (for POST requests) Specifies the type of data being sent (e.g., `application/x-www-form-urlencoded` for form data).

- **Body:** (Optional) Contains data being sent to the server. This is usually included in POST, PUT, or PATCH requests (e.g., form submissions, file uploads).

---

### Common HTTP Methods Used in Requests:

#### 1. GET
- **Purpose:** Retrieve information from the server.
- **Description:** The GET method is used to request data from a specified resource. It is the most commonly used HTTP method. When using GET, the request does not affect the state of the server, as it is considered a safe method. The data requested via GET is usually sent in the URL.
- **Example:** Fetching a webpage, an image, or querying a database via a URL.
  
```http
GET /page.html HTTP/1.1
Host: www.example.com
```

---

#### 2. POST
- **Purpose:** Send data to the server.
- **Description:** The POST method is used to submit data to be processed by the server. It is often used when creating a new resource (e.g., submitting a form or uploading a file). Unlike GET, the POST method sends data in the request body rather than appending it to the URL. It is not idempotent, meaning repeated identical requests may create multiple resources.
- **Example:** Submitting form data, uploading a file, creating new content.

```http
POST /submit-form HTTP/1.1
Host: www.example.com
Content-Type: application/x-www-form-urlencoded

name=John&age=25
```

---

#### 3. PUT
- **Purpose:** Update or replace a resource.
- **Description:** The PUT method is used to create or update a resource on the server. It replaces the entire resource with the new data provided. This method is idempotent, meaning making the same request multiple times will result in the same outcome.
- **Example:** Updating an existing user’s information.

```http
PUT /users/123 HTTP/1.1
Host: www.example.com
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com"
}
```

---

#### 4. DELETE
- **Purpose:** Remove a resource.
- **Description:** The DELETE method is used to delete a specified resource from the server. It is also idempotent, meaning multiple DELETE requests for the same resource will result in the same effect (resource deletion).
- **Example:** Removing a specific user from the database.

```http
DELETE /users/123 HTTP/1.1
Host: www.example.com
```

---

#### 5. PATCH
- **Purpose:** Partially update a resource.
- **Description:** The PATCH method is used to apply partial updates to a resource, as opposed to replacing it entirely (which PUT does). It allows modifications to a specific part of a resource.
- **Example:** Updating only the email of an existing user without affecting other details.

```http
PATCH /users/123 HTTP/1.1
Host: www.example.com
Content-Type: application/json

{
  "email": "newemail@example.com"
}
```

---

#### 6. HEAD
- **Purpose:** Retrieve headers without the body.
- **Description:** The HEAD method is identical to GET, but it only requests the headers and not the actual content (body). This is useful for checking if a resource exists or verifying resource metadata before downloading.
- **Example:** Checking the metadata of a webpage (e.g., Content-Length, Last-Modified) without downloading it.

```http
HEAD /index.html HTTP/1.1
Host: www.example.com
```

---

#### 7. OPTIONS
- **Purpose:** Retrieve the HTTP methods supported by the server.
- **Description:** The OPTIONS method is used to describe the communication options for the target resource. It is typically used by clients to determine the allowed methods or check for CORS (Cross-Origin Resource Sharing) configuration.
- **Example:** Finding out which HTTP methods are supported for a resource.

```http
OPTIONS /index.html HTTP/1.1
Host: www.example.com
```

---

#### 8. CONNECT
- **Purpose:** Establish a tunnel to the server.
- **Description:** The CONNECT method is used to establish a tunnel (a two-way communication channel) between the client and server, often for encrypted connections like HTTPS. It's commonly used by proxy servers to create a secure connection.
- **Example:** Establishing an SSL tunnel.

```http
CONNECT www.example.com:443 HTTP/1.1
Host: www.example.com
```

---

#### 9. TRACE
- **Purpose:** Perform a message loop-back test.
- **Description:** The TRACE method is used to perform a loop-back test along the path to the target resource. It is used mainly for debugging purposes to see how data is being processed by intermediate servers.
- **Example:** Sending a TRACE request to see how the request is altered by proxies.

```http
TRACE /index.html HTTP/1.1
Host: www.example.com
```

---

## 2. HTTP Response Message

The server replies to the client's request with an HTTP response message, containing the requested resource or an error message.

### Components of an HTTP Response Message:
- **Status Line:** Contains three main elements:
  - **HTTP Version:** The version of HTTP being used (e.g., HTTP/1.1).
  - **Status Code:** A three-digit code indicating the result of the request.
  - **Status Message:** A short message that explains the status code (e.g., "OK", "Not Found").

- **Headers:** Provide additional information about the response, such as:
  - **Content-Type:** Specifies the media type of the resource being sent (e.g., `text/html`, `application/json`).
  - **Content-Length:** Specifies the size of the resource in bytes.
  - **Server:** Identifies the server software.

- **Body:** Contains the resource being sent by the server (e.g., the HTML content of a webpage, an image, or JSON data). Not all response messages have a body (e.g., responses with a `204 No Content` status).

---

### HTTP Response Status Codes

HTTP response messages indicate the result of the client’s request. They are three-digit numbers divided into five categories:

#### 1. 1xx: Informational
These codes indicate that the server has received the request and is continuing to process it.
- `100 Continue`: The server has received the request headers, and the client should proceed with sending the request body.
- `101 Switching Protocols`: The server is complying with the client’s request to switch protocols (e.g., upgrading to HTTP/2).

---

#### 2. 2xx: Success
These codes indicate that the request was successfully received, understood, and processed by the server.
- `200 OK`: The request was successful, and the server is returning the requested resource.

```http
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234
```

- `201 Created`: The request was successful, and a new resource was created as a result (often used after POST requests).

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 567
```

- `204 No Content`: The server successfully processed the request, but there is no content to return (often used after DELETE requests).

```http
HTTP/1.1 204 No Content
```

---

#### 3. 3xx: Redirection
These codes indicate that the client must take additional action to complete the request.
- `301 Moved Permanently`: The requested resource has been moved to a new permanent URL.

```http
HTTP/1.1 301 Moved Permanently
Location: https://newsite.com/index.html
```

- `302 Found`: The requested resource is temporarily located at a different URL.

```

http
HTTP/1.1 302 Found
Location: https://temporary-location.com/index.html
```

- `304 Not Modified`: The resource has not been modified since the last request, so the client can use the cached version.

```http
HTTP/1.1 304 Not Modified
```

---

#### 4. 4xx: Client Errors
These codes indicate that there was an error in the request from the client.
- `400 Bad Request`: The server cannot process the request due to malformed syntax.

```http
HTTP/1.1 400 Bad Request
Content-Type: text/html
```

- `401 Unauthorized`: The client must authenticate itself to get the requested resource.

```http
HTTP/1.1 401 Unauthorized
WWW-Authenticate: Basic realm="Access to the site"
```

- `403 Forbidden`: The server understood the request, but it refuses to authorize it.

```http
HTTP/1.1 403 Forbidden
Content-Type: text/html
```

- `404 Not Found`: The requested resource could not be found on the server.

```http
HTTP/1.1 404 Not Found
Content-Type: text/html
```

- `405 Method Not Allowed`: The request method is not allowed for the requested resource.

```http
HTTP/1.1 405 Method Not Allowed
Allow: GET, POST
```

---

#### 5. 5xx: Server Errors
These codes indicate that the server failed to fulfill a valid request due to an error on the server’s side.
- `500 Internal Server Error`: The server encountered an unexpected condition.

```http
HTTP/1.1 500 Internal Server Error
Content-Type: text/html
```

- `502 Bad Gateway`: The server received an invalid response from an upstream server.

```http
HTTP/1.1 502 Bad Gateway
Content-Type: text/html
```

- `503 Service Unavailable`: The server is currently unable to handle the request due to overload or maintenance.

```http
HTTP/1.1 503 Service Unavailable
Retry-After: 3600
```

- `504 Gateway Timeout`: The server did not receive a timely response from the upstream server.

```http
HTTP/1.1 504 Gateway Timeout
```

---

### Summary of Common Status Codes:
- **1xx Informational:** Server is processing the request.
  - 100 Continue, 101 Switching Protocols.
- **2xx Success:** Request was successful.
  - 200 OK, 201 Created, 204 No Content.
- **3xx Redirection:** Additional action needed.
  - 301 Moved Permanently, 302 Found, 304 Not Modified.
- **4xx Client Errors:** Issues with the client’s request.
  - 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 405 Method Not Allowed.
- **5xx Server Errors:** Issues on the server’s side.
  - 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout.
 

# Example of a Real-Life HTTP Response (Login Request)

## When you attempt to log in to a website:

### Request:

```http
POST /login HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "username": "user123",
  "password": "password123"
}
```
### Possible Response 1 (Successful Login):

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 45

{
  "status": "success",
  "message": "Login successful",
  "user_id": 1234
}
```
### Possible Response 1 (Invalid Credentials):
```http
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Content-Length: 75

{
  "status": "error",
  "message": "Invalid username or password"
}
```

## Resources

- **Mozila web docs**:
  - [HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
  - [HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
  

---
