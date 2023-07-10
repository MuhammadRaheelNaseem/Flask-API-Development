# What is Flask

![image.png](attachment:image.png)

# `Introduction to Postman for API Development`

## `What is Postman?`
`Postman is an API(application programming interface) development tool which helps to build, test and modify APIs. It is used by over 5 million developers every month to make their API development easy and simple. It has the ability to make various types of HTTP requests(GET, POST, PUT, PATCH), saving environments for later use, converting the API to code for various languages(like JavaScript, Python).`

## `lets get started !!` 
## `Installing Postman on Windows`
## `Step 1: Visit the https://www.postman.com/ website using any web browser. `

![image.png](attachment:image.png)
![image-2.png](attachment:image-2.png)
![image-3.png](attachment:image-3.png)

## `Step 4: Now check for the executable file in downloads in your system and run it.`

![image-4.png](attachment:image-4.png)

## `Step 5: Create or sign in account`

![image-5.png](attachment:image-5.png)

## `Step 6: When you click on sign in option you will redirect on google verification link: just click`

![image-6.png](attachment:image-6.png)

## `Automatically log in application:`

![image-7.png](attachment:image-7.png)

## `How to use Postman to execute APIs`
`Below is the Postman Workspace. Let’s explore the step by step process on How to use Postman and different features of the Postman tool!`

![image-8.png](attachment:image-8.png)

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
![image.png](attachment:image.png)
![image-2.png](attachment:image-2.png)
![image-3.png](attachment:image-3.png)
![image-4.png](attachment:image-4.png)
![image-5.png](attachment:image-5.png)
![image-6.png](attachment:image-6.png)

# 2.) `POST` Method:
![image-7.png](attachment:image-7.png)
![image-8.png](attachment:image-8.png)
![image-10.png](attachment:image-10.png)
![image-9.png](attachment:image-9.png)
![image-11.png](attachment:image-11.png)
![image-12.png](attachment:image-12.png)
![image-13.png](attachment:image-13.png)
![image-14.png](attachment:image-14.png)

# 3.) `PATCH` Method:
![image-15.png](attachment:image-15.png)
![image-16.png](attachment:image-16.png)
![image-17.png](attachment:image-17.png)

# 4.) `DELETE` Method:
![image-18.png](attachment:image-18.png)
![image-19.png](attachment:image-19.png)
![image-20.png](attachment:image-20.png)

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



```python

```


```python

```


```python

```

# What is Protocol

## Is this protocol
![image.png](attachment:image.png)

## Protocol: 

A protocol is a set of rules and guidelines for communicating data. Rules are defined for each step in the process during communication between two or more computers. Networks have to follow these rules to successfully transmit data.

![image.png](attachment:image.png)
![image-3.png](attachment:image-3.png)


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

![image.png](attachment:image.png)
![image-2.png](attachment:image-2.png)
![image-3.png](attachment:image-3.png)
![image-4.png](attachment:image-4.png)
![image-5.png](attachment:image-5.png)


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

![image-2.png](attachment:image-2.png)
![image-3.png](attachment:image-3.png)

## what is jsonify
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

![image-2.png](attachment:image-2.png)
![image.png](attachment:image.png)

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

![image.png](attachment:image.png)


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

![image.png](attachment:image.png)


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

![image.png](attachment:image.png)


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

![image.png](attachment:image.png) 

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

![image.png](attachment:image.png) 


```python
from flask import Flask

app = Flask(__name__)

@app.route('/api/users', methods=['POST'])
def create_user():
    return jsonify({"message": "Creating a new user"})

if __name__ == '__main__':
    app.run()

```

![image.png](attachment:image.png) 


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

![image.png](attachment:image.png) 


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

![image.png](attachment:image.png) 


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

![image.png](attachment:image.png) 


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

`POST`
![image-2.png](attachment:image-2.png)
`GET`
![image.png](attachment:image.png) 


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

![image-3.png](attachment:image-3.png)
![image.png](attachment:image.png)
![image-2.png](attachment:image-2.png)


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

![image.png](attachment:image.png)
![image-2.png](attachment:image-2.png)

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

![image.png](attachment:image.png)


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

![image.png](attachment:image.png)
![image-2.png](attachment:image-2.png)


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

![image.png](attachment:image.png) 


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


```python

```

# DELETE Method


```python

```


```python
from flask import Flask

app = Flask(__name__)

@app.route('/api/users/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    return f'Deleting user with ID: {user_id}'

if __name__ == '__main__':
    app.run()

```

![image.png](attachment:image.png)


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

![image.png](attachment:image.png)


```python
# from flask import Flask, request, jsonify
import mysql.connector
from pprint import pprint

db = mysql.connector.connect(
    host="mraheel.mysql.pythonanywhere-services.com",
    user="mraheel",
    password="Raheel42101@",
    port=3306
)
```


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
![image.png](attachment:image.png)
# OUPUT `POST` Method:
![image-2.png](attachment:image-2.png)
![image-4.png](attachment:image-4.png)
# OUTPUT `PUT` Method:
![image-5.png](attachment:image-5.png)
![image-6.png](attachment:image-6.png)
# OUTPUT `DELETE` Method:
![image-7.png](attachment:image-7.png)
![image-8.png](attachment:image-8.png)

# Now Deploying API script into `pythonanywhere.com`
![image.png](attachment:image.png)
![image-2.png](attachment:image-2.png)
![image-3.png](attachment:image-3.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image-2.png](attachment:image-2.png)

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image-2.png](attachment:image-2.png)

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image.png](attachment:image.png) 

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image-2.png](attachment:image-2.png)
![image.png](attachment:image.png)
![image-3.png](attachment:image-3.png)
![image-4.png](attachment:image-4.png)
![image-6.png](attachment:image-6.png)
![image-5.png](attachment:image-5.png)
![image-7.png](attachment:image-7.png)
![image-8.png](attachment:image-8.png)
