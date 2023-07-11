# What is Flask

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/300830d4-f187-44f0-ba7d-41418bcdfcce)


# `Introduction to Postman for API Development`

## `What is Postman?`
`Postman is an API(application programming interface) development tool which helps to build, test and modify APIs. It is used by over 5 million developers every month to make their API development easy and simple. It has the ability to make various types of HTTP requests(GET, POST, PUT, PATCH), saving environments for later use, converting the API to code for various languages(like JavaScript, Python).`

## `lets get started !!` 
## `Installing Postman on Windows`
## `Step 1: Visit the https://www.postman.com/ website using any web browser. `

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/c9eaf3a0-f329-4ef9-8e8f-7077cd555f37)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/bd6bbee0-38cb-4dee-9fde-1eab6aa4ae69)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/13b7661a-d6d9-4173-84e1-084ed12457b7)


## `Step 4: Now check for the executable file in downloads in your system and run it.`

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/977b11d6-3dcd-4f55-a4b2-59c84e392a02)


## `Step 5: Create or sign in account`

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a38028ee-e56c-4f29-944b-2be1dcb46509)


## `Step 6: When you click on sign in option you will redirect on google verification link: just click`

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/1250f3d9-75ec-478f-9500-870a6cfb4b3b)


## `Automatically log in application:`
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/64d175d1-97ce-4dbb-a73d-9ca3735205de)


## `How to use Postman to execute APIs`
`Below is the Postman Workspace. Let’s explore the step by step process on How to use Postman and different features of the Postman tool!`

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/15f40e75-848f-491d-b8c4-e7e9ac8e5c19)


`<ol>
<li> <b>New</b> – This is where you will create a new request, collection or environment.</li>
<li> <b>Import</b> – This is used to import a collection or environment. There are options such as import from file, folder, link or paste raw text.</li>
<li> <b>Runner</b> – Automation tests can be executed through the Collection Runner. This will be discussed further in the next lesson.</li>
<li>   <b>Open New </b>– Open a new tab, Postman Window or Runner Window by clicking this button.</li>
<li> <b>My Workspace</b> – You can create a new workspace individually or as a team.</li>
<li> <b>Invite</b> – Collaborate on a workspace by inviting team members.</li>
<li> <b>History</b> – Past requests that you have sent will be displayed in History. This makes it easy to track actions that you have done.</li>
<li> <b>Collections</b> – Organize your test suite by creating collections. Each collection may have subfolders and multiple requests. A request or folder can also be duplicated as well.</li>
<li> <b>Request tab </b>– This displays the title of the request you are working on. By default, “Untitled Request” would be displayed for requests without titles.</li>
<li> <b>HTTP Request </b>– Clicking this would display a dropdown list of different requests such as GET, POST, COPY, DELETE, etc. In Postman API testing, the most commonly used requests are GET and POST.</li>
<li> <b>Request URL </b>– Also known as an endpoint, this is where you will identify the link to where the API will communicate with.</li>
<li> <b>Save </b>– If there are changes to a request, clicking save is a must so that new changes will not be lost or overwritten.</li>
<li> <b>Params </b>– This is where you will write parameters needed for a request such as key values.</li>
<li> <b>Authorization </b>– In order to access APIs, proper authorization is needed. It may be in the form of a username and password, bearer token, etc.</li>
<li> <b>Headers </b>– You can set headers such as content type JSON depending on the needs of the organization.</li>
<li> <b>Body </b>– This is where one can customize details in a request commonly used in POST request.</li>
<li> <b>Pre-request Script </b>– These are scripts that will be executed before the request. Usually, pre-request scripts for the setting environment are used to ensure that tests will be run in the correct environment.</li>
<li> <b>Tests </b>– These are scripts executed during the request. It is important to have tests as it sets up checkpoints to verify if response status is ok, retrieved data is as expected and other tests.</li>
</ol>`

Working with GET Requests
Get requests are used to retrieve information from the given URL. There will be no changes done to the endpoint.

We will use the following URL for all examples in this Postman tutorial

# Free API
https://www.youtube.com/watch?v=lId_LdQ8wXU&list=PLeBsfMNV_8I_2k18tE9nDzkOEYcImQvjm&index=25
https://github.com/vdespa/introduction-to-postman-course/blob/main/simple-books-api.md

# API Status
HTTP defines these standard status codes that can be used to convey the results of a client’s request. The status codes are divided into five categories.

**1xx**: `Informational `– Communicates transfer protocol-level information.<br>
**2xx**: `Success `– Indicates that the client’s request was accepted successfully.<br>
**3xx**: `Redirection `– Indicates that the client must take some additional action in order to complete their request.<br>
**4xx**: `Client Error `– This category of error status codes points the finger at clients.<br>
**5xx**: `Server Error` – The server takes responsibility for these error status codes.<br>

# 1xx: Informational – Communicates transfer protocol-level information.
<table class="mtr-table mtr-tr-th" style="align-text:left"><tbody><tr><th data-mtr-content="Status Code" class="mtr-th-tag"><div class="mtr-cell-content">Status Code</div></th><th data-mtr-content="Description" class="mtr-th-tag"><div class="mtr-cell-content">Description</div></th></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>100 Continue</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">An interim response. Indicates to the client that the initial part of the request has been received and has not yet been rejected by the server. The client SHOULD continue by sending the remainder of the request or, if the request has already been completed, ignore this response. The server MUST send a final response after the request has been completed.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>101 Switching Protocol</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Sent in response to an <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Protocol_upgrade_mechanism">Upgrade</a> request header from the client, and indicates the protocol the server is switching to.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>102 Processing (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the server has received and is processing the request, but no response is available yet.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>103 Early Hints</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Primarily intended to be used with the <code>Link</code> header. It suggests the user agent start preloading the resources while the server prepares a final response.</div></td></tr></tbody></table> 

# 2xx: Success – Indicates that the client’s request was accepted successfully.
<figure class="wp-block-table"><table class="mtr-table mtr-tr-th"><tbody><tr><th data-mtr-content="Status Code" class="mtr-th-tag"><div class="mtr-cell-content">Status Code</div></th><th data-mtr-content="Description" class="mtr-th-tag"><div class="mtr-cell-content">Description</div></th></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>200 OK</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the request has succeeded.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>201 Created</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the request has succeeded and a new resource has been created as a result.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>202 Accepted</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the request has been received but not completed yet. It is typically used in log running requests and batch processing.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>203 Non-Authoritative Information</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the returned metainformation in the entity-header is not the definitive set as available from the origin server, but is gathered from a local or a third-party copy. The set presented MAY be a subset or superset of the original version.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>204 No Content</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server has fulfilled the request but does not need to return a response body. The server may return the updated meta information.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>205 Reset Content</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates the client to reset the document which sent this request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>206 Partial Content</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">It is used when the <code>Range</code> header is sent from the client to request only part of a resource.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>207 Multi-Status (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">An indicator to a client that multiple operations happened, and that the status for each operation can be found in the body of the response.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>208 Already Reported (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Allows a client to tell the server that the same resource (with the same binding) was mentioned earlier. It never appears as a true HTTP response code in the status line, and only appears in bodies.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>226 IM Used</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server has fulfilled a GET request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance.</div></td></tr></tbody></table></figure>

# 3xx: Redirection – Indicates that the client must take some additional action in order to complete their request.
<figure class="wp-block-table"><table class="mtr-table mtr-tr-th"><tbody><tr><th data-mtr-content="Status Code" class="mtr-th-tag"><div class="mtr-cell-content">Status Code</div></th><th data-mtr-content="Description" class="mtr-th-tag"><div class="mtr-cell-content">Description</div></th></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>300 Multiple Choices</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The request has more than one possible response. The user-agent or user should choose one of them.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>301 Moved Permanently</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The URL of the requested resource has been changed permanently. The new URL is given by the <code>Location</code> header field in the response. This response is cacheable unless indicated otherwise.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>302 Found</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The URL of the requested resource has been changed temporarily. The new URL is given by the <code>Location</code> field in the response. This response is only cacheable if indicated by a <code>Cache-Control</code> or <code>Expires</code> header field.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>303 See Other</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The response can be found under a different URI and SHOULD be retrieved using a GET method on that resource.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>304 Not Modified</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates the client that the response has not been modified, so the client can continue to use the same cached version of the response.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>305 Use Proxy (Deprecated)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that a requested response must be accessed by a proxy.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>306 (Unused)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">It is a reserved status code and is not used anymore.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>307 Temporary Redirect</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates the client to get the requested resource at another URI with same method that was used in the prior request. It is similar to <code>302 Found</code> with one exception that the same HTTP method will be used that was used in the prior request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>308 Permanent Redirect (experimental)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the resource is now permanently located at another URI, specified by the <code>Location</code> header. It is similar to <code>301 Moved Permanently</code> with one exception that the same HTTP method will be used that was used in the prior request.</div></td></tr></tbody></table></figure>

# 4xx: Client Error – This category of error status codes points the finger at clients.
<figure class="wp-block-table"><table class="mtr-table mtr-tr-th"><tbody><tr><th data-mtr-content="Status Code" class="mtr-th-tag"><div class="mtr-cell-content">Status Code</div></th><th data-mtr-content="Description" class="mtr-th-tag"><div class="mtr-cell-content">Description</div></th></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>400 Bad Request</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The request could not be understood by the server due to incorrect syntax. The client SHOULD NOT repeat the request without modifications.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>401 Unauthorized</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the request requires user authentication information. The client MAY repeat the request with a suitable Authorization header field</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>402 Payment Required (Experimental)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Reserved for future use. It is aimed for using in the digital payment systems.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>403 Forbidden</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Unauthorized request. The client does not have access rights to the content. Unlike 401, the client’s identity is known to the server.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>404 Not Found</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server can not find the requested resource.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>405 Method Not Allowed</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The request HTTP method is known by the server but has been disabled and cannot be used for that resource.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>406 Not Acceptable</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server doesn’t find any content that conforms to the criteria given by the user agent in the <code>Accept</code> header sent in the request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>407 Proxy Authentication Required</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the client must first authenticate itself with the proxy.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>408 Request Timeout</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the server did not receive a complete request from the client within the server’s allotted timeout period.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>409 Conflict</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The request could not be completed due to a conflict with the current state of the resource.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>410 Gone</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The requested resource is no longer available at the server.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>411 Length Required</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server refuses to accept the request without a defined Content- Length. The client MAY repeat the request if it adds a valid <code>Content-Length</code> header field.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>412 Precondition Failed</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The client has indicated preconditions in its headers which the server does not meet.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>413 Request Entity Too Large</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Request entity is larger than limits defined by server.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>414 Request-URI Too Long</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The URI requested by the client is longer than the server can interpret.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>415 Unsupported Media Type</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The media-type in <code>Content-type</code> of the request is not supported by the server.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>416 Requested Range Not Satisfiable</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The range specified by the <code>Range</code> header field in the request can’t be fulfilled.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>417 Expectation Failed</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The expectation indicated by the <code>Expect</code> request header field can’t be met by the server.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>418 I’m a teapot (RFC 2324)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">It was defined as April’s lool joke and is not expected to be implemented by actual HTTP servers. (<a href="https://tools.ietf.org/html/rfc2324">RFC 2324</a>)</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>420 Enhance Your Calm (Twitter)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Returned by the Twitter Search and Trends API when the client is being rate limited.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>422 Unprocessable Entity (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server understands the content type and syntax of the request entity, but still server is unable to process the request for some reason.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>423 Locked (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The resource that is being accessed is locked.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>424 Failed Dependency (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The request failed due to failure of a previous request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>425 Too Early (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the server is unwilling to risk processing a request that might be replayed.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>426 Upgrade Required</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server refuses to perform the request. The server will process the request after the client upgrades to a different protocol.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>428 Precondition Required</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The origin server requires the request to be conditional.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>429 Too Many Requests</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The user has sent too many requests in a given amount of time (“rate limiting”).</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>431 Request Header Fields Too Large</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server is unwilling to process the request because its header fields are too large.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>444 No Response (Nginx)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The Nginx server returns no information to the client and closes the connection.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>449 Retry With (Microsoft)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The request should be retried after performing the appropriate action.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>450 Blocked by Windows Parental Controls (Microsoft)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Windows Parental Controls are turned on and are blocking access to the given webpage.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>451 Unavailable For Legal Reasons</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The user-agent requested a resource that cannot legally be provided.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>499 Client Closed Request (Nginx)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The connection is closed by the client while HTTP server is processing its request, making the server unable to send the HTTP header back.</div></td></tr></tbody></table></figure>

# 5xx: Server Error – The server takes responsibility for these error status codes.
<figure class="wp-block-table"><table class="mtr-table mtr-tr-th"><tbody><tr><th data-mtr-content="Status Code" class="mtr-th-tag"><div class="mtr-cell-content">Status Code</div></th><th data-mtr-content="Description" class="mtr-th-tag"><div class="mtr-cell-content">Description</div></th></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>500 Internal Server Error</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server encountered an unexpected condition that prevented it from fulfilling the request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>501 Not Implemented</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The HTTP method is not supported by the server and cannot be handled.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>502 Bad Gateway</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server got an invalid response while working as a gateway to get the response needed to handle the request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>503 Service Unavailable</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server is not ready to handle the request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>504 Gateway Timeout</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server is acting as a gateway and cannot get a response in time for a request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>505 HTTP Version Not Supported (Experimental)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The HTTP version used in the request is not supported by the server.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>506 Variant Also Negotiates (Experimental)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the server has an internal configuration error: the chosen variant resource is configured to engage in transparent content negotiation itself, and is therefore not a proper endpoint in the negotiation process.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>507 Insufficient Storage (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The method could not be performed on the resource because the server is unable to store the representation needed to successfully complete the request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>508 Loop Detected (WebDAV)</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">The server detected an infinite loop while processing the request.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>510 Not Extended</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Further extensions to the request are required for the server to fulfill it.</div></td></tr><tr><td data-mtr-content="Status Code" class="mtr-td-tag"><div class="mtr-cell-content"> <strong>511 Network Authentication Required</strong></div></td><td data-mtr-content="Description" class="mtr-td-tag"><div class="mtr-cell-content">Indicates that the client needs to authenticate to gain network access.</div></td></tr></tbody></table></figure>

# API Testing with Postman

# 1.) `GET` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/7f4fd1b3-3d5f-4844-97d4-61ae6b443a42)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/06b4dde1-a278-4fba-98b3-f4e78ad03b82)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/7d6e2e83-60d9-4e7c-a3db-edfdffa5c87b)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/551df4ff-1aa9-4e93-aba9-4a4db99be45d)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/d00d4881-6a43-4765-9df5-cad3c63f5956)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/cbabcc4b-2f48-4fca-b7ad-24af6b013c5b)


# 2.) `POST` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/219ff046-5057-4411-984d-32657a1bba77)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/13ae9d75-7531-4cea-8715-a366291574f8)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/51caeb7d-30dc-4d90-9e55-283087b422d8)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/4f728332-335f-4663-b36d-d2826811a16c)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/7e6687b1-80e1-4121-adfe-d219d857a7fe)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/39e3626f-0977-4b45-9531-ac2d469a7ded)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/183d9895-29dc-48ea-a6fd-54702c8514dd)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/1f05bf09-ba21-42c0-a745-dde253a2751a)


# 3.) `PATCH` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/27736754-c22b-49d4-ab96-6c2caeb0879a)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a550cb6f-180e-443b-aae1-f85986f39a68)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/63441551-612f-402f-8f3e-ddd94dc8523a)


# 4.) `DELETE` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/58872a6d-a2d4-4d65-8fba-fa0287598fb2)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/369ed739-56b3-438d-a44f-f9069dade1ce)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/1aa769fa-7ae9-4e14-97c9-2100aea9901b)


# API Development with Flask App
---
# Setup Flask on your `localhost`
---
1. If you haven't yet, go ahead and install [Python](https://www.python.org/downloads/). (Your Python version should be 3.4.x or higher.)

      **Important** (Windows users):
      Please make sure to add the Python path to Windows Path. Read more here
      Also, Windows installer now includes an option to add python.exe to the system search path. When you install Python, select the "Add Python 3.x to PATH" option. If selected, the install directory will be added to your PATH.

      **Important** (Mac/Linux users): 
      Mac and Linux systems have Python 2.x installed already. When you type and run `python` on the terminal, it will run the Python2 interpreter. To launch Python 3, run `python3` and to run the `python3` installer run `pip3`.

2. Open a terminal or command line window. 
   Run the following commands to install `flask` and `flask-sqlalchemy`. 

    on `Windows`:
    ```
    pip install flask
    pip install flask-wtf
    pip install flask-sqlalchemy
    ```

# What is Protocol

## Is this protocol
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a78ed314-6cc8-4217-bb37-350df19ab664)

## Protocol: 

A protocol is a set of rules and guidelines for communicating data. Rules are defined for each step in the process during communication between two or more computers. Networks have to follow these rules to successfully transmit data.

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/d77cc2b9-ac80-46c4-93f2-2807473fac0f)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/1065dd88-7ad4-4508-aa71-24ceff46debc)



```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return "<h1>Hello!</h1>"

@app.route('/course')
def course():
    return '<h1>Hello class!</h1>'

@app.route('/course/<string:name>')
def mycourse(name):
    return '<h1>Hello, {0} class!</h1>'.format(name)

@app.route('/appname')
def appname():
    return "<h1>Application name:--> {}</h1>".format(__name__)

if __name__ == '__main__':
    app.run()


```
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/efb91a2c-4b11-4ce1-aca5-ef16fc34b2dd)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a213322b-f511-4528-9419-84d7c594a560)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/6276a77b-cfa9-4380-9fa9-0203da893b0e)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/df36601b-f30c-4ee9-bb4a-d55b79c3deee)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/9bf83c5d-d94b-4c9f-a189-312f82062aa2)



```python

```


```python
import json
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return json.dumps({'name': 'alice',
                       'email': 'alice@outlook.com'})

app.run()
```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/4d9cefb1-f4fe-48e6-b230-d70d55424ba6)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/504ab103-bcd5-456c-a058-bb93f0a9760a)


## What is jsonify
jsonify is a function provided by Flask, a popular web framework for Python. It is used to convert Python objects into JSON (JavaScript Object Notation) format, which is a lightweight data interchange format commonly used in web APIs.


```python
import json
from flask import Flask, jsonify
app = Flask(__name__)
@app.route('/')
def index():
    return jsonify({'name': 'alice',
                    'email': 'alice@outlook.com'})

app.run()
```


```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api/data')
def get_data():
    data = {
        'name': 'John Doe',
        'age': 25,
        'city': 'New York'
    }
    return jsonify(data)

if __name__ == '__main__':
    app.run()

```


```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route("/calcu/<int:n>")
def calculate(n):
    result = {"Value":n**n,
             "Type":"int"}
    print(result)
    return jsonify(result)

@app.route("/name/<string:fname>")
def name(fname):
    result = {"Name":fname}
    return result

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/18e138bc-f5e3-4649-8135-270263fb2e15)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a516849f-f3ee-479b-83c0-58c425333fb5)


# Request method
<hr>
We know that there are six commonly used HTTP request methods, which are

* GET
* POST
* PUT
* DELETE
* PATCH
* HEAD

The code that we just had had to deal with GET by default (the browser defaults to using GET), so how do you program the other requests?

Like this:

`@app.route('/', methods=['POST'])`<br>
`@app.route('/', methods=['DELETE'])`<br>
`@app.route('/', methods=['PUT'])`

# GET Method


```python
from flask import Flask, jsonify

app = Flask(__name__)

users = [
    {'id': 1, 'name': 'John Doe'},
    {'id': 2, 'name': 'Jane Smith'}
]

@app.route('/api', methods=['GET'])
def get_users():
    return jsonify(users)


if __name__ == '__main__':
    app.run(port=3000)

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/8bb1c764-2f72-4599-b8a2-f1b0518b3342)



```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api', methods=['GET','POST'])
def get_users():
    return jsonify([
        {'id': 1, 'name': 'John Doe'},
        {'id': 2, 'name': 'Jane Smith'}
    ])

if __name__ == '__main__':
    app.run(port=3000)

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/89ad5d12-8230-4dc5-95f6-44cbaf044f31)



```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api', methods=['GET'])
def get_users():
    users = []
    users.append({'id': 1, 'name': 'John Doe'})
    users.append({'id': 2, 'name': 'Jane Smith'})
    return jsonify(users)

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/4291dc52-365a-45a2-98f9-83f334e59a6e)



```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api', methods=['GET'])
def get_users():
    users = []
    users.append({'id': 1, 'name': 'John Doe'})
    users.append({'id': 2, 'name': 'Jane Smith'})
    users.append({'id': 3, 'name': 'Alice Johnson'})
    return jsonify({'users': users})

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/8941f4a9-6efa-4de4-ab27-812307684f28)


# POST Method


```python
from flask import Flask

app = Flask(__name__)

@app.route('/api/users', methods=['POST'])
def create_user():
    return 'Creating a new user'

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/2eed3210-f225-48f7-ab55-6ca4a39d2a89)



```python
from flask import Flask

app = Flask(__name__)

@app.route('/api/users', methods=['POST'])
def create_user():
    return jsonify({"message": "Creating a new user"})

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/1470f1c1-ca77-4059-8af4-0d271f08a6dd)



```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/api/users', methods=['POST'])
def create_user():
    data = request.json
    name = data.get('name')
    return f"Creating a new user: {name}"

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/5c180e44-2429-409d-9454-f2b4b6e2f908)



```python
from flask import Flask, request, jsonify

app = Flask(__name__)

users = []

# @app.route('/api/users', methods=['POST'])
@app.post('/api/users')
def create_user():
    data = request.json
    name = data.get('name')
    email = data.get('email')
    new_user = {'name': name, 'email': email}
    users.append(new_user)
    return jsonify(new_user), 202

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/360fb399-df81-4009-afa0-e49c6629aabe)



```python
from flask import Flask, request, jsonify

app = Flask(__name__)

users = []

@app.route('/api/users', methods=['POST'])
def create_user():
    new_user = request.get_json()
    users.append(new_user)
    print(users)
    return jsonify(new_user), 201

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/f7f85432-5c96-4a04-b81c-5bdb92dd7e97)



```python
from flask import Flask, request, jsonify

app = Flask(__name__)

users = []

@app.route('/api/users', methods=['POST'])
def create_user():
    new_user = request.get_json()
    users.append(new_user)
    return jsonify(new_user), 201

@app.route('/api/users/all', methods=['GET'])
def get_all_users():
    return jsonify(users)

if __name__ == '__main__':
    app.run()

```

# `POST`
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/47ffa337-0ddd-41e9-977e-2da75f677f71)

# `GET`
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/65acf006-bd7a-44d1-bdba-b160c5220238)



```python
from flask import Flask, request, render_template

app = Flask(__name__)

@app.route("/formlogin", methods=['GET', 'POST'])
def login():
    if request.method == "POST":
        uname = request.form['username']
        password = request.form['user_password']
        if uname == "admin" and password == "123":
            return "Welcome " + uname
        else:
            return "Try again"
    else:
        return render_template('form.html')

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/524585fb-28d7-41d0-837f-bc4270535081)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/435db0ac-e799-412a-95e7-0dbd5de98b7f)
![imag![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/641d760a-4e8d-4911-a38b-080bae4ce306)



```python
from flask import Flask, request, render_template

app = Flask(__name__)

@app.get("/formlogin")
def login():
    return render_template('form.html')
    print("Runing.........")
    uname = request.form['uname']
    password = request.form['password']
    print(uname,password)
    if uname == "admin" and password == "123":
        return "Welcome " + uname
    else:
        return "Try again"

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/5ae2240a-f0fa-47af-b462-17641dfc0788)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/5f583477-0e44-42a4-b3d4-0460bfeae71f)


# PUT Method


```python
from flask import Flask

app = Flask(__name__)

@app.route('/api/users/<int:user_id>', methods=['PUT'])
def update_user(user_id):
    return f'Updating user with ID: {user_id}'

if __name__ == '__main__':
    app.run()

```
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/6fd298f3-93b8-4a84-996b-265766412e2e)



```python
from flask import Flask, request, jsonify

app = Flask(__name__)

users = [
    {"id": 1, "name": "John Doe"},
    {"id": 2, "name": "Jane Smith"},
    {"id": 3, "name": "Doe"},
    {"id": 4, "name": "Smith"},
    {"id": 5, "name": "John"},
    {"id": 7, "name": "Jane"}
]
print(users)
@app.route('/api/users/<int:user_id>', methods=['PUT'])
def update_user(user_id):
    data = request.json
    for user in users:
        if user['id'] == user_id:
            user.update(data)
            print(users)
            return jsonify(user)
    return jsonify({'message': 'User not found'}), 404

if __name__ == '__main__':
    app.run(port=3000)

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/92a5a94b-a24f-40f7-9ee1-a2695b1afaec)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/573ea83d-9e15-4aa2-9896-04b70393247a)



```python
from flask import Flask, request, jsonify

app = Flask(__name__)

users = [
    {'id': 1, 'name': 'John Doe'},
    {'id': 2, 'name': 'Jane Smith'}
]

@app.route('/api/users/<int:user_id>', methods=['PUT'])
def update_user(user_id):
    data = request.get_json()
    for user in users:
        if user['id'] == user_id:
            user['name'] = data['name']
            return jsonify(user)
    return jsonify({'message': 'User not found'}), 404

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/ea399433-e5cf-4003-9f15-9380d41a9f6c)



```python
from flask import Flask, request, jsonify

app = Flask(__name__)

users = [
    {'id': 1, 'name': 'John Doe'},
    {'id': 2, 'name': 'Jane Smith'}
]

@app.route('/api/users/<int:user_id>', methods=['PUT'])
def update_user(user_id):
    data = request.get_json()
    for user in users:
        if user['id'] == user_id:
            user.update(data)
            return jsonify(user)
    return jsonify({'message': 'User not found'}), 404

@app.route('/api/users/all', methods=['GET'])
def get_all_users():
    return jsonify(users)

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/f87960a1-c78e-47c6-b218-3b898c7a93c1)


```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/api/users/<id>', methods=['PUT'])
def update_user(id):
    data = request.json
    name = data['name']
    email = data['email']
    user = {'id': id, 'name': name, 'email': email}
    return jsonify(user)

if __name__ == '__main__':
    app.run()
```
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/d9756835-22b1-47ad-b697-a161eb246c5d)


# DELETE Method




```python
from flask import Flask

app = Flask(__name__)

@app.route('/api/users/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    return f'Deleting user with ID: {user_id}'

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/944c1971-9937-433f-9276-721ae23f114c)



```python
from flask import Flask, jsonify

app = Flask(__name__)

users = [
    {"id": 1, "name": "John Doe"},
    {"id": 2, "name": "Jane Smith"},
    {"id": 3, "name": "Doe"},
    {"id": 4, "name": "Smith"},
    {"id": 5, "name": "John"},
    {"id": 7, "name": "Jane"}
]
print(users)

@app.route('/api/users/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    for user in users:
        if user['id'] == user_id:
            users.remove(user)
            print(users)
            return jsonify({'message': 'User deleted'})
    return jsonify({'message': 'User not found'}), 404

if __name__ == '__main__':
    app.run()

```

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/e0818526-9c1e-4b6b-815e-c28a38feb2e1)

# Now Making Script That Can Used All Methods

```python
from flask import Flask, request, jsonify
import mysql.connector
from pprint import pprint

app = Flask(__name__)

db = mysql.connector.connect(
    host="127.0.0.1",
    user="root",
    password="admin",
    database="temp_data",
)

# Create a table in the database if it doesn't exist
def create_table():
    cur = db.cursor()
    cur.execute("CREATE TABLE IF NOT EXISTS temp_emp_3 (ID INT PRIMARY KEY AUTO_INCREMENT, Name VARCHAR(100), Email VARCHAR(100), Address VARCHAR(100))")
    db.commit()
    cur.close()

# API route to get all users
@app.route('/api/users', methods=['GET'])
def get_users():
    cur = db.cursor()
    cur.execute("SELECT * FROM temp_emp_3")
    users = cur.fetchall()
    print(users)
    cur.close()
    user_list = []
    for user in users:
        user_dict = {
            'id': user[0],
            'name': user[1],
            'email':user[2],
            'address': user[3]
        }
        user_list.append(user_dict)
    pprint(user_list)
    return jsonify(user_list)

# API route to create a new user
@app.route('/api/users/add', methods=['POST'])
def create_user():
    name = request.json.get('name')
    email = request.json.get('email')
    addr = request.json.get("address")
    print(name,email,addr)
    cur = db.cursor()
    cur.execute("INSERT INTO temp_emp_3 (Name,Email,Address) VALUES (%s,%s,%s)", (name,email,addr))
    db.commit()
    cur.close()
    return jsonify({'message': 'User created successfully'})

# API route to update an existing user
@app.route('/api/users/update/<string:user_id>', methods=['PUT'])
def update_user(user_id):
    name = request.json.get('name')
    email = request.json.get('email')
    addr = request.json.get('address')
    cur = db.cursor()
    cur.execute("UPDATE temp_emp_3 SET Name = %s, Email = %s, Address = %s WHERE ID = %s", (name, email,addr, user_id))
    db.commit()
    cur.close()
    return jsonify({'message': 'User updated successfully'})

# API route to delete a user
@app.route('/api/users/delete/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    cur = db.cursor()
    cur.execute("DELETE FROM temp_emp_3 WHERE id = %s" %(user_id))
    db.commit()
    cur.close()
    return jsonify({'message': 'User deleted successfully'})

if __name__ == '__main__':
    create_table()
    app.run(host="127.0.0.1",port=3000)

```

# OUPUT `GET` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/ace218b0-285e-40b2-a095-a77f9ea22821)

# OUPUT `POST` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/642ee444-3e0d-42ba-bce0-75e5f5a07580)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/cf55462f-a5fa-4ca6-9b7c-2c3cb386ca1c)

# OUTPUT `PUT` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/bbd064ff-354b-484f-9560-a5e47ec18d13)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/4e11cd76-d8fc-46de-b8e6-e3f84cd0e58c)

# OUTPUT `DELETE` Method:
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/e60d83cb-d789-4115-bec1-474bbe38c33a)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/1565b48d-4494-48eb-b8cd-0fc497973f83)


# Now Deploying API script into `pythonanywhere.com`

![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/d715dde0-f7ff-4c11-b1da-ee3a2cd493b0)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/9457bf21-3f4a-4cd0-87a8-9bdbb1db7d3b)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/f2ba9132-0115-4c83-93dc-4c1c66c1f746)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/0bce4e90-7964-4d42-a728-8647a8a792d0)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a59cd8cc-d878-421f-b292-ee6b337485f8)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/c14ea896-60d2-43ca-83e7-3dcc758985c7)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/2fe17db1-6121-42d1-aa0e-deef63c608e9)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/f5c852e3-217c-4c3b-85f3-8df7773c2a56)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/5e37db1f-5857-4229-8167-62e068e3b592)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/e8328405-c938-4359-80fe-6e8ecac214d2)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/7b0bd521-3b74-4c2c-bea2-2860a2d964c4)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/2fe85e28-b094-47bd-9b6e-2ef9a8aa5959)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/3dc50fb3-36cb-4755-b040-cb2cfc23fe32)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/9ceccd1c-b80e-4da9-8752-fadcfa4beb5c)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a51342fd-c679-4ae3-969c-51d5a6772105)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/02a87e13-b5bd-4ae7-a70b-8b417612d4de)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/f02826c7-7e3a-47b7-80e1-952f26f3c056)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/c9463db9-a959-4175-911f-67d0711e63cc)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a5ffe4cb-aba0-4917-ae56-7efc972070ac)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/8059551d-db12-4845-9695-b7ef50abe2c7)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/36fbceca-ec3e-4b8c-828f-57e17d2a1826)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/1f38109c-b220-4712-8352-ecfa8e974b79)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/e26a0433-845e-4278-8020-6ccbbd349da8)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/0225618f-2eed-4f8c-ab1b-096a4cd708be)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/ef2190f8-75b5-4a50-96d2-582b14883a3d)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/71a18d96-d8a8-4e19-93e2-321b2a612dac)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/8a7aa96c-b41c-4c3c-9b0b-ed877d790b28)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/d17cfecf-dc38-450d-bc80-9173e0b3257c)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/6100d08f-3453-4b16-b268-ba95ed0d7669)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/8ab0c9cf-e1b3-4ee1-b3e1-ea48fe122efe)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/3ce29301-0294-4190-9270-5828871978f1)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/51bcd4ef-ce3a-474e-9daa-05548c48a5a1)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a75a104a-394f-4b1d-ad78-117a04b02afa)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/e035777a-5e20-46c8-b825-6bf91af0262c)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/e56dfe94-30b4-4762-bcd6-86a49ce61fe2)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/a54f3405-b213-47da-8728-50dac1125681)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/f4707672-95be-445f-832f-c22642330f34)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/d6fcb2f2-9c08-4306-ab76-c84e3a09ac7f)
![image](https://github.com/MuhammadRaheelNaseem/Flask-API-Development/assets/63813881/8e20d293-e8e8-4547-a4ac-118861561b3e)
