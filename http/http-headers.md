## HTTP Headers

We already talked about the main agents in HTTP communication — client and server.

Even when we consider methods, status codes and request body, there is still more information exchanged between these parts. This is where headers come in.

Headers are additional information sent with the request or response. They help define how the server should process the request and how the client should handle the response.

Headers can be grouped into a few main types, as seeing bellow

## Common headers

### Authorization

Used to send authentication credentials.

Common issues:

- Missing or expired token  
  When an endpoint requires authentication, the request must include a valid token.  
  It is common to see 4xx errors when the token is expired or missing.

- Invalid or insufficient permissions  
  The token may be valid, but does not have the required permissions to access the resource.  
  This usually results in authorization errors.

- Incorrect token format  
  The header may be present, but in the wrong format (for example, missing "Bearer").  
  This can cause the request to be rejected by the server.

### Content-Type

Used to define the format of the request or response body.

Common issues:

- Wrong content type  
  The server or the client is not expecting the current format.  
  For example: the response is JSON, but the client expects XML.

- Missing content type  
  The request is sent without a content-type header, so the server cannot correctly process the body.

- Incorrect format declaration  
  The header says "application/json", but the body is not valid JSON.  
  This usually causes parsing errors on the server.
  
### Cache-Control

Used to define caching behavior in requests and responses.

Common issues:

- Stale data (outdated responses)  
  Cached data is stored for too long, so the client receives old information instead of the latest data.

- No caching for static data  
  Data that rarely changes is not cached, causing unnecessary requests and increasing server load.

- Inconsistent cache behavior  
  Different layers (client, CDN, gateway) apply different cache rules, leading to unexpected results.

- Cache not being invalidated  
  Data changes, but the cache is not updated or cleared, so users still see old data.

Commom issues: 
### Accept
### User-Agent
### Host
### Content-Length
### X-Request-ID

## Why headers matter in practice

Headers are a common source of issues in APIs and integrations.

Small mistakes in headers can completely change the behavior of a request.

For example:

- Missing or invalid authentication headers can cause authorization errors  
- Incorrect content-type can break request processing  
- Cache headers can return outdated data  
- Missing headers can lead to unexpected behavior between systems  

Because of this, checking headers should always be part of any troubleshooting process.
