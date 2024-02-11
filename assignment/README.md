# What are the most common HTTP headers?

* HTTP headers play a crucial role in server and client behavior throughout the request and response cycle. Request headers are sent by the client to the server and contain information and instructions related to the requested resource, while response headers are sent by the server to the client and provide metadata, instructions, and additional information about the response itself.
# Some of the most commonly used request headers are:

* Accept
The Accept header defines the media types that the client is able to accept from the server. For instance, Accept: application/json, text/html indicates that the client prefers JSON or HTML responses. This information allows the server to send a resource representation that meets the client’s needs.

* User-Agent
The User-Agent header identifies the web browser or client application that is making the request, which enables the server to tailor its response to the client. For instance, if the User-Agent header indicates that the request is coming from the Chrome browser, the server may include CSS prefixes for CSS properties that are compatible with Chrome.

* Authorization
The Authorization header is used to send the client’s credentials to the server when the client is attempting to access a protected resource. For instance, the client might include a JSON Web Token (JWT) as the value of the header, which the server will then verify before returning the requested resource.

* Content-Type
The Content-Type header identifies the media type of the content in the request body. For instance, Content-Type: application/json indicates that the request body contains JSON data. This information helps the server successfully interpret and process the payload.

* Cookie
The client can use the Cookie header to send previously stored cookies back to the server. The server then uses these cookies to associate the request with a specific user or session. This header plays an important role in delivering personalized experiences, as it enables the server to remember a user’s login state or language preference.
 ![Screenshot (554)](https://github.com/Subhransupanda2000/servlet/assets/123824203/7b45a867-f526-4ecc-a63b-bbaa99d88483)

# Basic Authentication
Basic authentication is a simple authentication mechanism used in HTTP protocol. It allows a client to provide credentials (username and password) when making an HTTP request to a server. The server then validates these credentials before processing the request. Here's how it works:

Client Request: When a client wants to access a protected resource on the server, it includes an Authorization header in the HTTP request. The header contains the word "Basic" followed by a space and a base64-encoded string representation of the username and password concatenated with a colon (username:password).

Server Validation: Upon receiving the request, the server extracts the username and password from the Authorization header. It then verifies the credentials against its authentication system, such as a user database or directory service.

Response: If the credentials are valid, the server grants access to the requested resource and returns the appropriate response (e.g., status code 200 OK). If the credentials are invalid, the server returns a status code indicating authentication failure (e.g., 401 Unauthorized) along with a WWW-Authenticate header to prompt the client to provide valid credentials.

# Bearer Token
A bearer token is a type of access token commonly used in authentication and authorization mechanisms, particularly in OAuth 2.0 and JSON Web Token (JWT) based systems. It is called a "bearer" token because whoever possesses it can use it to access protected resources, much like a bearer of a physical token.

Working of a bearer token:

Obtaining a Token: A client (such as a user agent or a third-party application) obtains a bearer token from an authorization server by presenting credentials or through some other authentication mechanism.

Using the Token: The client includes the bearer token in the HTTP Authorization header when making requests to access protected resources on a resource server. The token is usually included in the form of Bearer .

Validation: Upon receiving a request with a bearer token, the resource server validates the token to ensure its authenticity and integrity. This typically involves verifying the token's signature (if it's a JWT) or consulting with the authorization server to confirm the token's validity.

Access Control: Once the bearer token is successfully validated, the resource server grants access to the requested resource based on the permissions associated with the token.
# Authentication:

Authentication is the process of verifying the identity of a user, system, or entity attempting to access a resource or service.
It ensures that the user is who they claim to be before granting access to protected resources.
Authentication mechanisms typically involve presenting credentials, such as usernames, passwords, tokens, or biometric data, and validating them against a trusted source, such as a user database or identity provider.
Successful authentication establishes trust in the identity of the user, allowing them to proceed with accessing authorized resources.
# Authorization:

Authorization is the process of determining what actions or resources a user is allowed to access or perform after they have been authenticated.
It involves enforcing access control policies based on the authenticated user's identity, roles, permissions, or other attributes.
Authorization mechanisms define rules and policies that govern who can access specific resources, what operations they can perform, and under what conditions.
Authorization typically occurs after authentication and relies on information about the user's identity and associated permissions.
# What is jwt?
* JSON Web Token (JWT) authentication is a stateless method of securely transmitting information between parties as a JavaScript Object Notation (JSON) object. It is often used to authenticate and authorize users in web applications and APIs.
# Idempotent
In the context of HTTP, idempotent methods are HTTP methods where making the same request multiple times has the same effect as making it once. This property simplifies error handling and recovery, particularly in scenarios where requests may be retried due to network issues or other failures. Here are the idempotent methods in HTTP:

* GET:

Purpose: Retrieve data from the specified resource.
Idempotent: Yes (Multiple identical requests have the same effect as a single request).
Safe: Yes (Should not have any side effects on the server).
* HEAD:

Purpose: Retrieve headers of a resource without the response body.
Idempotent: Yes (Multiple identical requests have the same effect as a single request).
Safe: Yes (Should not have any side effects on the server).
* PUT:

Purpose: Update a resource or create a new resource if it does not exist.
Idempotent: Yes (Multiple identical requests have the same effect as a single request).
Safe: No (May have side effects on the server).
* DELETE:

Purpose: Request the removal of a resource identified by the URI.
Idempotent: Yes (Multiple identical requests have the same effect as a single request).
Safe: No (May have side effects on the server).
* OPTIONS:

Purpose: Describe the communication options for the target resource.
Idempotent: Yes (Multiple identical requests have the same effect as a single request).
Safe: Yes (Should not have any side effects on the server).
* TRACE:

Purpose: Echo the received request for diagnostic purposes.
Idempotent: Yes (Multiple identical requests have the same effect as a single request).
Safe: Yes (Should not have any side effects on the server).
# Status code:
* 200 OK: Request successful, server fulfilled the client's request.
* 201 Created: New resource created successfully.
* 202 Accepted: Request accepted for processing, but not completed yet.
* 500 Internal Server Error: Server encountered an unexpected condition.
* 502 Bad Gateway: Server received an invalid response from an upstream server.
* 503 Service Unavailable: Server currently unable to handle the request.
* 404 Not Found: Requested resource not found on the server.
* 406 Not Acceptable: Server cannot generate a response meeting client's criteria.
* 415 Unsupported Media Type: Server refuses to accept request due to unsupported media type.
* 302 Found: Requested resource temporarily moved to a different URI.

 ![Screenshot (552)](https://github.com/Subhransupanda2000/servlet/assets/123824203/59bb9c2d-a6d8-4689-9815-53d2653b0800)
 ![Screenshot (553)](https://github.com/Subhransupanda2000/servlet/assets/123824203/8a148961-90fa-4d96-81a9-bf2b8ee4b87a)
![Screenshot (554)](https://github.com/Subhransupanda2000/servlet/assets/123824203/7b45a867-f526-4ecc-a63b-bbaa99d88483)
```
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.cors.CorsConfiguration;
import org.springframework.web.cors.UrlBasedCorsConfigurationSource;
import org.springframework.web.filter.CorsFilter;

@Configuration
public class CorsConfig {

    @Bean
    public CorsFilter corsFilter() {
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        CorsConfiguration config = new CorsConfiguration();

        // Allow all origins, headers, and methods for demonstration purposes.
        config.addAllowedOrigin("*");
        config.addAllowedHeader("*");
        config.addAllowedMethod("*");

        source.registerCorsConfiguration("/**", config);
        return new CorsFilter(source);
    }
}

```
CORS is a security feature implemented by web browsers to restrict webpages from making requests to a different domain than the one that served the original webpage. It is a security mechanism implemented in web browsers to prevent a web page from making requests to a different domain than the one that served the web page. CORS is enforced by web browsers, not by the server.

When a web application hosted on one domain (origin) makes a request for resources to a different domain, the browser may block the request due to the Same-Origin Policy. CORS allows servers to specify which origins are permitted to access their resources and which HTTP methods (e.g., GET, POST) are allowed.

Why CORS is Used:

CORS is used to enable secure cross-origin requests and data transfers between browsers and servers. It allows servers to specify who can access their resources and under what conditions. This is crucial for ensuring that sensitive data is not exposed to unauthorized domains.





