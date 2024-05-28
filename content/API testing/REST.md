# REST APIs

REST: **Representational State Transfer** is an architecture for HTTP web services

REST APIs usually follow the URL convention
- Like: `/version/class/bject-id/function`
	- Eg. `/v1/user/120/details`
- REST APIs are usually represented as JSON objects in both requests and responses.
	- Can also use other representation like XML. but rarely
- REST APIs use HTTP method to determine what to do: `GET, POST, DELETE`

> **postman** is good tool for API testing

### finding REST APIs endpoints
- reverse engineering mobile apps to find such endpoints
	- the web interface might use a different web API from the mobile version

### Caching in REST APIs
- **GET** requests should be cachable by default – until a special condition arises. Usually, browsers treat all GET requests as cacheable.
- **POST** requests are not cacheable by default but can be made cacheable if either an `Expires` header or a `Cache-Control` header with a directive, to explicitly allows caching, is added to the response.
- Responses to `PUT` and `DELETE` requests are not cacheable at all.

**cache control headers:**
- `Expires: Fri, 20 May 2016 19:20:49 GMT`
	- specifies an absolute expiry time
	- note that HTTP dates are always expressed in GMT, never in local time.
- `Cache-Control: max-age=3600`
	- The header value comprises one or more comma-separated directives. These directives determine whether a response is cacheable, and if so, by whom, and for how long e.g. max-age or s-maxage directives.
- `ETag: "abcd1234567n34jv"`
	- An _ETag_ value is an opaque string token that a server associates with a resource to uniquely identify the state of the resource over its lifetime.
	- If the resource at a given URL changes, a new `Etag` value _must_ be generated. A comparison of them can determine whether two representations of a resource are the same. If both values match the server sends back a `304` `Not Modified` status, without a body, which tells the client that the cached version of the response is still good to use (_fresh_).
- `Last-Modified: Fri, 10 May 2016 09:17:49 GMT`
	- Whereas a response’s _Date_ header indicates when the response was generated, the _Last-Modified_ header indicates when the associated resource was last changed.