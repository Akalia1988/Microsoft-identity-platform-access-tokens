# Microsoft-identity-platform-access-tokens
Azure Active directory token.

Azure Active Directory (AD)this service is used to store information about users and organizational structure.
We will use this service as our Authority service which will be responsible to secure our Resource (Web API) and issue access tokens.

The resource (Web API) should be consumed by a Client, so the client will be requesting the data from the resource (Web API), but in order for this request to be accepted by the resource, the client must send a valid access token obtained from the Authority service (Azure AD) with each request.

Register the Web API into Azure Active Directory

![image](https://user-images.githubusercontent.com/58148717/104037306-299e8480-519a-11eb-8641-2942bdfbd9aa.png)

Then a wizard of 2 steps will show up asking you to select the type of the app you want to add, in our case we are currently adding a Web API so select “Web Application and/or Web API”, then provide a name for the application, in my case I’ll call it “WebApiAzureAD”, then click next.

![image](https://user-images.githubusercontent.com/58148717/104037366-42a73580-519a-11eb-98d9-f7af64511c4a.png)

Expose our Web API to other applications

After our Web API has been added to Azure Active Directory apps, we need to do one more thing here which is exposing our permission scopes to our developers who will build clients to consume our Web API

![image](https://user-images.githubusercontent.com/58148717/104037487-5bafe680-519a-11eb-8609-d5b8d0ca10f8.png)

add another application to our Azure AD tenant and configure the permission to allow accessing the back-end API

![image](https://user-images.githubusercontent.com/58148717/104037761-6cf8f300-519a-11eb-9644-cafd84e5b571.png)

Configure the Application Permissions

we need to configure the app and specify which registered application it can access in our case we need to give the specific application permission to access our back-end API (WebApiAzureAD)

![image](https://user-images.githubusercontent.com/58148717/104038050-826e1d00-519a-11eb-8f7e-c6cce607114d.png)

Adding the registered application to our project 

![image](https://user-images.githubusercontent.com/58148717/104038281-91ed6600-519a-11eb-8720-0686b729be56.png)

the value for “ClientId” key is coming from the “Client Id” value for the client we defined in Azure AD, and the same applies for the key “RedirectUrl”.
User Requests Access with Username / Password
Application validates credentials
Application provides a signed token to the client
Client stores that token and sends it along with every request
Server verifies token and responds with data

1.Access tokens enable clients to securely call protected APIs
(JSON Web Token (JWT) is a compact, URL-safe means of representing
 claims to be transferred between two parties.  The claims in a JWT
 are encoded as a JSON object that is used as the payload of a JSON
 Web Signature (JWS) structure or as the plaintext of a JSON Web
 Encryption (JWE) structure, enabling the claims to be digitally
 signed or integrity protected with a Message Authentication Code
 (MAC) and/or encrypted)JSON is a lightweight, text-based, language-independent data interchange format.

when 3rd party will request an access token,Microsoft identity platform also returns some metadata about the access token. This information includes the expiry time and after a fixed interval that token will expire no longer be valid for API consumption(another layer of security in order to protect our data)
This data allows your app to do intelligent caching of access tokens without having to parse the access token itself.

Access tokens enable clients to securely call protected APIs

A key advantage of using Azure AD for web API is that we dont need to store our credentials in our code.
















