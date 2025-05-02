## Program 1: Flask Setup and Basic Routing

**Goal:** Set up a Flask application and create basic routes. This program will ensure Flask is installed, start a minimal app, and demonstrate simple routing (including a dynamic route).

### Code

```python
# app1.py - Basic Flask setup and routing

from flask import Flask

app = Flask(__name__)  # Initialize Flask application

# Define a simple route for the home page
@app.route('/')
def home():
    return "Welcome to the Flask API Lecture Series!"

# Define another route that accepts a dynamic segment <name>
@app.route('/hello/<name>')
def greet(name):
    # Return a greeting for the provided name
    return f"Hello, {name}!"

# Run the app in debug mode (for development convenience)
if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We first import `Flask` from the `flask` package and create an `app` instance using `app = Flask(__name__)`. The `__name__` argument tells Flask to use the current module as the application – this is needed to locate resources and templates relative to the app.
* Using the `@app.route()` decorator, we bind URL paths to view functions. For example, `@app.route('/')` associates the URL **/** (root) with the `home()` function. When a client requests the root URL, Flask will invoke `home()` and send its return value back as the response.
* The `home()` function returns a simple welcome string. Flask will convert this string into an HTTP response sent to the client.
* The second route `'/hello/<name>'` demonstrates a **dynamic route**. The `<name>` part in the URL path means this route will match any URL of the form `/hello/`**something**, and the `something` will be passed into the `greet(name)` function as the variable `name`. For example, requesting `/hello/John` will call `greet("John")` and return `"Hello, John!"`. Flask automatically URL-encodes/decodes the `<name>` segment, so it can handle spaces or special characters in the name if properly encoded.
* The `if __name__ == '__main__':` block ensures the Flask development server runs only when we execute this script directly. `app.run(debug=True)` starts the server on the default port 5000 in debug mode, which auto-reloads on code changes and provides an interactive debugger for errors (useful during development).

### Testing with Postman

1. **Run the application**: Make sure you have Flask installed (`pip install Flask`). Save the code as `app1.py` and run it with `python app1.py`. You should see Flask’s startup message indicating the server is running on `http://127.0.0.1:5000/` (or `localhost:5000`).
2. **Test the home route**: In Postman (or your web browser), send a GET request to `http://localhost:5000/`. You should receive a **200 OK** response with the body **"Welcome to the Flask API Lecture Series!"**.

   * In Postman, you can create a new GET request, enter the URL, and hit Send. The response body will appear in the output section.
3. **Test the dynamic route**: Send a GET request to `http://localhost:5000/hello/Flask`. You should get **"Hello, Flask!"** in the response. Try changing the name in the URL (for example, `/hello/Alice`) to see the response update accordingly. This confirms our dynamic routing works for any name provided.
4. **Edge case**: If you omit the name (e.g., just `/hello/`), Flask will return a **404 Not Found** error because the route expects a `<name>` segment. You can see the 404 status in Postman’s response. (Flask’s routing requires the dynamic part since we didn’t provide a default.)

This basic setup verifies that Flask is installed and routing is functioning. In the next program, we will extend this app to handle different HTTP methods and JSON data.

## Program 2: Handling GET and POST Requests with JSON Payloads

**Goal:** Introduce handling of GET vs POST methods in Flask routes, and how to accept and return JSON data. We will create two routes: one that processes URL query parameters (for a GET request) and one that accepts a JSON body in a POST request.

### Code

```python
# app2.py - Handling GET query parameters and POST JSON payloads

from flask import Flask, request, jsonify

app = Flask(__name__)

# GET route that reads query parameters
@app.route('/square', methods=['GET'])
def square_number():
    # Get the 'number' query parameter from the URL
    num_str = request.args.get('number')  # Returns None if 'number' not provided
    if num_str is None:
        # If no number is provided, return a 400 Bad Request
        return jsonify({"error": "Missing 'number' query parameter"}), 400
    try:
        num = int(num_str)
    except ValueError:
        # If the value is not an integer, return 400 with an error message
        return jsonify({"error": "Invalid 'number' parameter, must be an integer"}), 400

    result = num * num
    # Return the result as JSON
    return jsonify({"number": num, "square": result})  # Flask will send 200 OK by default

# POST route that accepts a JSON payload and echoes it
@app.route('/echo', methods=['POST'])
def echo():
    # Parse JSON from request body
    data = request.get_json()
    if data is None:
        # If request body is not valid JSON or empty, return 400
        return jsonify({"error": "Request body must be JSON"}), 400

    # For demonstration, just return the received JSON data with a message
    response = {
        "received": data,
        "message": "JSON received successfully"
    }
    return jsonify(response), 200

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We import `request` and `jsonify` from Flask. The `request` object gives us access to the incoming HTTP request (including query parameters, headers, body data, etc.), and `jsonify` is a helper to create JSON responses easily.
* We define a GET route `/square` that expects a query parameter `number`. We explicitly set `methods=['GET']` to ensure this route only handles GET requests (Flask defaults to GET if not specified).

  * Inside `square_number()`, we use `request.args.get('number')` to retrieve the query parameter named "number" from the URL. `request.args` is a dictionary-like object (ImmutableMultiDict) containing query string keys and values. Using the `.get()` method is safer than direct indexing because it returns `None` if the key is missing instead of raising an error.
  * If `number` is missing, we return a JSON error message and a **400 Bad Request** status. In Flask, you can return a tuple `(<response_body>, <status_code>)` directly from a view function. We use `jsonify({"error": ...})` to create a JSON response for the error, and provide `400` as the status code.
  * If `number` is provided, we attempt to convert it to an integer. If conversion fails (e.g., `?number=abc`), we return another 400 error with a message indicating the parameter must be an integer.
  * If all is well, we compute the square of the number and return a JSON response containing both the original number and its square. For example, if `number=5`, our response JSON will be `{"number": 5, "square": 25}`. We use `jsonify` which will set the `Content-Type: application/json` header and by default return a 200 OK status (since we didn’t specify a different status).
* We also define a POST route `/echo` that expects a JSON payload in the request body.

  * We call `request.get_json()` to parse the incoming JSON data. Flask’s `get_json()` method will return a Python dictionary (or list) parsed from the JSON, or `None` if the content is not valid JSON or if the `Content-Type` is not `application/json`.
  * If `data is None`, we return a 400 error indicating the body must be JSON. (In Postman, forgetting to set the body to raw JSON or a typo in JSON can trigger this.)
  * If JSON is received, we prepare a response dictionary containing the received data and a confirmation message. This shows how to echo back data or further process it as needed.
  * We return the response dictionary as JSON with a 200 OK status. (Using `jsonify(response), 200` explicitly sets the status, but in this case it would be 200 even if we omitted the status since 200 is default for a successful return.)
* Note: We did not specify `methods` for `/echo`, but provided only `methods=['POST']`. Flask by default will respond with 405 Method Not Allowed if someone tries to GET `/echo` since we restricted it to POST.

### Testing with Postman

**Setup**: Run `app2.py` with `python app2.py`. The server will run on port 5000 as before.

1. **Testing the GET route (`/square`)**:

   * In Postman, create a GET request to `http://localhost:5000/square`.
   * First, send it without any query parameter. You should receive a **400 Bad Request** response with JSON body:
     `{"error": "Missing 'number' query parameter"}`. This confirms our validation for missing params works.
   * Now add a query parameter. In Postman, you can use the **Params** tab: enter key as `number` and value as, say, `7`. (This will append `?number=7` to the URL.) Send the request again. You should get a **200 OK** response with JSON:
     `{"number": 7, "square": 49}`.
   * Test an invalid input: set `number` to `abc` and send. The response should be 400 with `{"error": "Invalid 'number' parameter, must be an integer"}`.
   * This shows the route reading query parameters and returning JSON with appropriate status codes.
2. **Testing the POST route (`/echo`)**:

   * In Postman, create a POST request to `http://localhost:5000/echo`.
   * Under the **Body** tab, select **raw** and choose **JSON (application/json)** from the dropdown. This ensures the `Content-Type` header is set to `application/json`.
   * Now provide a JSON body. For example:

     ```json
     {
       "course": "Flask API",
       "lesson": 2,
       "items": ["GET", "POST", "JSON"]
     }
     ```
   * Send the request. The response should be **200 OK** with a JSON body that contains the same data under `"received"` and a message, for example:

     ```json
     {
       "message": "JSON received successfully",
       "received": {
         "course": "Flask API",
         "lesson": 2,
         "items": ["GET", "POST", "JSON"]
       }
     }
     ```

     This confirms the server correctly parsed and returned the JSON.
   * Test sending an improper request: for example, change the body to plain text or remove the JSON header. If the body isn’t valid JSON, you should get the `{"error": "Request body must be JSON"}` message with 400 status. In Postman, also try not selecting the JSON type for raw body to see the error handling in action.

By completing Program 2, you’ve learned how to handle query parameters in GET requests and process JSON in POST requests, responding with JSON and proper HTTP status codes.

## Program 3: Working with Query Parameters and Response Status Codes

**Goal:** Dive a bit deeper into query parameters and returning custom HTTP status codes. In this program, we’ll reinforce the concept of reading query strings and explicitly setting various response statuses including success (200), bad request (400), and not found (404).

### Code

```python
# app3.py - Query parameters and custom status codes

from flask import Flask, request, jsonify, abort

app = Flask(__name__)

# A GET route that uses multiple query parameters to filter a result
@app.route('/divide', methods=['GET'])
def divide():
    # Expecting two query params: a and b
    a = request.args.get('a')
    b = request.args.get('b')
    if a is None or b is None:
        # Missing one of the parameters -> 400 Bad Request
        return jsonify({"error": "Please provide both 'a' and 'b' parameters"}), 400
    try:
        a = float(a)
        b = float(b)
    except ValueError:
        # Non-numeric query values -> 400
        return jsonify({"error": "Parameters 'a' and 'b' must be numbers"}), 400

    if b == 0:
        # Division by zero is not allowed -> 400
        return jsonify({"error": "Division by zero is not allowed"}), 400

    result = a / b
    return jsonify({"a": a, "b": b, "result": result}), 200

# A route to demonstrate 404 Not Found for an invalid path parameter
@app.route('/item/<int:item_id>', methods=['GET'])
def get_item(item_id):
    # Suppose we only have items 1-3 for demo
    if item_id not in [1, 2, 3]:
        # Use Flask's abort() to send a 404 error if item not found
        abort(404)
    # If valid, return a dummy item
    item = {"id": item_id, "name": f"Item {item_id}"}
    return jsonify(item), 200

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We import `abort` from Flask to help in sending HTTP errors easily.
* The `/divide` route demonstrates reading **multiple query parameters**:

  * We expect two numbers, `a` and `b`, provided as query parameters. For example: `/divide?a=10&b=2`. We retrieve them with `request.args.get('a')` and `request.args.get('b')`.
  * If either is missing, we return a 400 with an error JSON, similar to Program 2.
  * We attempt to convert both to floats (to allow decimal division). If conversion fails (inputs aren't numeric), return 400 with an error message.
  * If `b == 0`, we detect an attempt to divide by zero and return a 400 error as well (with an explanatory message). This is a **business logic validation** resulting in a bad request response.
  * Otherwise, we compute the division and return a JSON containing `a`, `b`, and the result of `a/b`. We explicitly include `, 200` in the return to emphasize the success status code.
* The `/item/<int:item_id>` route shows how to handle a case where a requested resource might not exist:

  * The route uses a dynamic path segment `<int:item_id>`. By specifying `<int:...>`, Flask will automatically convert that part of the URL to an integer and pass it to the function (or return 404 if it cannot convert). Here, `item_id` will be an `int` inside the function.
  * We simulate a scenario where only item IDs 1, 2, 3 exist. If the client requests an item outside this range, our code calls `abort(404)`. `abort()` is a Flask function that immediately stops the request and returns an HTTP error response with the given status code (404 Not Found in this case). Flask will return a default 404 HTML page if running in debug, but since we called it explicitly, it knows to send a 404 status.
  * If the item ID is valid (1–3), we return a dummy item dictionary (in real cases, you would fetch from a database or data structure). The response is JSON with a 200 status.
* **Why explicitly handle status codes?** In a Flask API, you’ll often need to return specific HTTP status codes based on conditions:

  * **200 OK** for successful requests (Flask does this by default if you return normally).
  * **400 Bad Request** for client-side errors like missing or invalid parameters.
  * **404 Not Found** for resources that cannot be located (Flask will also do this automatically if no route matches or if a path converter fails, but using `abort(404)` is useful for application-level missing resources).
  * You can also use `abort(401)` for unauthorized, `abort(403)` for forbidden, etc., when we handle authentication (coming up in later programs).

### Testing with Postman

Run `app3.py` and test the routes:

1. **Testing `/divide`**:

   * Try a request without parameters: GET `http://localhost:5000/divide`. Response should be 400 with JSON error about providing both parameters.
   * Try with non-numeric values: e.g. `?a=foo&b=bar`. Still 400 with error "must be numbers".
   * Try with `b=0`: e.g. `?a=5&b=0`. 400 with "division by zero not allowed".
   * Finally, try a valid one: e.g. `?a=9&b=3`. You should get `{"a": 9.0, "b": 3.0, "result": 3.0}` with a 200 OK. Note that we converted to float, so even if you passed integers, the JSON shows `9.0` etc.
   * Postman tip: You can add these query params in the Params section or manually append `?a=...&b=...` to the URL.
   * Each test verifies a different branch of our code (missing params, invalid type, invalid operation, success).
2. **Testing `/item/<item_id>`**:

   * Try `GET http://localhost:5000/item/5`. Since 5 is not in \[1,2,3], our code calls `abort(404)`. Postman will show a **404 Not Found** status. The body might be an HTML error page by default. (If you prefer JSON errors, you could catch this and return JSON, but by default Flask’s 404 is HTML.)
   * Try `GET http://localhost:5000/item/2`. You should get **200 OK** with JSON `{"id": 2, "name": "Item 2"}`.
   * If you try a non-integer like `GET /item/test`, Flask itself will return 404 because it couldn’t convert "test" to an int for `<int:item_id>`.
   * This demonstrates path parameter conversion and using `abort()` for returning errors.

At this point, you know how to validate inputs and return appropriate HTTP status codes in your Flask API. Next, we will move on to implementing authentication mechanisms to secure certain routes.

## Program 4: Basic Authentication Using Headers

**Goal:** Implement **HTTP Basic Authentication** in a Flask route by examining the **Authorization header**. In Basic Auth, clients send a header with a username and password encoded in Base64. We will simulate a protected route that only allows access if the correct credentials are provided via this header.

### Code

```python
# app4.py - Basic Authentication via Authorization header

import base64
from flask import Flask, request, jsonify, make_response

app = Flask(__name__)

# For demonstration, define a single valid username and password
VALID_USERNAME = "admin"
VALID_PASSWORD = "secret123"

@app.route('/protected-basic', methods=['GET'])
def protected_basic():
    auth_header = request.headers.get('Authorization')
    if not auth_header:
        # No credentials provided, request authentication
        # Send a 401 with WWW-Authenticate header as per Basic Auth spec
        response = make_response(jsonify({"error": "Authentication required"}), 401)
        response.headers['WWW-Authenticate'] = 'Basic realm="Login Required"'
        return response

    # Authorization header expected format: "Basic <base64_credentials>"
    parts = auth_header.split()
    if len(parts) != 2 or parts[0].lower() != 'basic':
        # Malformed header
        return jsonify({"error": "Invalid Authorization header format"}), 400

    # Decode the Base64 credentials part
    encoded_credentials = parts[1]
    try:
        decoded_bytes = base64.b64decode(encoded_credentials)
        credentials = decoded_bytes.decode('utf-8')
    except Exception as e:
        return jsonify({"error": "Invalid Base64 credentials"}), 400

    # Credentials format is "username:password"
    if ':' not in credentials:
        return jsonify({"error": "Invalid credential format"}), 400
    username, password = credentials.split(':', 1)

    # Check against our valid credentials
    if username == VALID_USERNAME and password == VALID_PASSWORD:
        # Successful authentication
        return jsonify({"message": f"Welcome, {username}! You have accessed a protected resource."}), 200
    else:
        # Wrong credentials -> 401 Unauthorized
        response = make_response(jsonify({"error": "Invalid username or password"}), 401)
        # Prompt again for correct credentials
        response.headers['WWW-Authenticate'] = 'Basic realm="Login Required"'
        return response

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We import `base64` to decode the credentials and also `make_response` to attach headers to our responses.
* We set `VALID_USERNAME` and `VALID_PASSWORD` as the only acceptable credentials for simplicity. In real cases, you would check against a user database.
* The route `/protected-basic` requires Basic Auth:

  * We read the `Authorization` header from the incoming request: `Authorization: Basic <credentials>`. If the header is missing, we return a **401 Unauthorized** with a `WWW-Authenticate` header. The `WWW-Authenticate` header instructs the client that Basic authentication is needed. We set it to `Basic realm="Login Required"` which is a standard way to prompt the user (the realm can be any description).
  * If the header is present, we split it on whitespace. The expected format is two parts: "Basic" and the Base64-encoded credentials. We check that the first part (scheme) is "Basic" (case-insensitive) and that we have two parts.
  * We take the second part which is the Base64 string. We attempt to decode it using `base64.b64decode`. This should give us a bytes string like `b'username:password'`. We decode that to UTF-8 to get the string `username:password`.
  * We verify the decoded format contains a colon. If not, it’s not in the expected "user\:pass" format.
  * We then split the credentials into `username` and `password`.
  * We compare these against our known valid credentials. If they match, we return a success message JSON with 200 OK.
  * If they do not match, we return 401 Unauthorized with an error message and again include `WWW-Authenticate` to allow the client to retry with correct credentials.
* This mimics HTTP Basic Auth flow: the first request typically has no auth and gets a 401 with `WWW-Authenticate`, then the client sends credentials. In Postman, we can send the header preemptively.
* **Security considerations:** Basic Auth sends credentials in Base64 (which is just an encoding, not encryption). This means it’s not secure on its own—typically you would use HTTPS to encrypt the entire connection if doing this. Also, storing plaintext passwords (like our `VALID_PASSWORD`) is not secure; later we’ll use hashing for stored passwords. But for a demo, this is fine.

### Testing with Postman

Run `app4.py`. In Postman:

1. **Without credentials**: Make a GET request to `http://localhost:5000/protected-basic` without any Authorization header.

   * You should receive a 401 Unauthorized. In Postman’s response, you’ll see the status **401**. Check the headers in the response (in Postman, switch to the Headers tab of the response): there should be `WWW-Authenticate: Basic realm="Login Required"`.
   * The body is a JSON: `{"error": "Authentication required"}`.
2. **With valid credentials**: In Postman, go to the **Authorization** tab for your request. Choose "Basic Auth" from the dropdown. Enter username `admin` and password `secret123` (our valid pair). Postman will automatically add the correct `Authorization: Basic ...` header to the request.

   * Send the GET request again. This time, you should get **200 OK** and a JSON message: `{"message": "Welcome, admin! You have accessed a protected resource."}`.
   * This shows that the server decoded and verified your credentials successfully.
3. **With invalid credentials**: Test by changing the password or username in Postman’s Basic Auth fields. For example, use `admin : wrongpass`. The response should be 401 Unauthorized with `{"error": "Invalid username or password"}`. The response will still include `WWW-Authenticate: Basic realm="Login Required"`, meaning the server is saying "that was not correct, please try again or provide valid credentials".
4. **Manual header**: Alternatively, you can manually set the `Authorization` header. For `admin:secret123`, the Base64 encoding is `YWRtaW46c2VjcmV0MTIz` (you can verify this by using an online Base64 encoder or Python). You would then set `Authorization` to `Basic YWRtaW46c2VjcmV0MTIz`. Postman’s Basic Auth does this for you, but it’s good to understand the underlying format.

This program demonstrated how to secure a route with Basic Auth. However, sending credentials with every request is not ideal for a modern API. Instead, **token-based authentication (JWT)** is preferred for stateless authentication. We will explore JWTs next.

## Program 5: Creating JWT Tokens for Authentication

**Goal:** Learn how to create a **JWT (JSON Web Token)** after a user logs in. JWTs are self-contained tokens that clients can send to prove their authentication, instead of sending username/password each time. We will use the **PyJWT** library to encode a token. This program focuses on generating a JWT – the next will focus on using it to protect routes.

### Code

```python
# app5.py - JWT token creation example

import jwt  # PyJWT library
from datetime import datetime, timedelta, timezone
from flask import Flask, request, jsonify

app = Flask(__name__)
app.config['SECRET_KEY'] = 'supersecretkey'  # secret key for signing JWT

# Dummy user data (in real life, you would query a database)
USER_DATA = {
    "alice": {"password": "alice123"},   # username: alice, password: alice123
    "bob":   {"password": "bobpassword"} # username: bob, password: bobpassword
}

@app.route('/login', methods=['POST'])
def login():
    # Expect JSON with username and password
    data = request.get_json()
    if not data or 'username' not in data or 'password' not in data:
        return jsonify({"error": "Username and password required"}), 400

    username = data['username']
    password = data['password']
    # Check if user exists and password matches
    user = USER_DATA.get(username)
    if user and user['password'] == password:
        # Create JWT payload
        payload = {
            "user": username,
            # Set token to expire in 1 hour for example
            "exp": datetime.now(timezone.utc) + timedelta(hours=1)
        }
        # Encode JWT using our secret key and HS256 algorithm
        token = jwt.encode(payload, app.config['SECRET_KEY'], algorithm="HS256")
        # PyJWT's jwt.encode returns a token (in PyJWT>=2 it returns a byte string or str depending on version)
        token_str = token if isinstance(token, str) else token.decode('utf-8')
        return jsonify({"token": token_str}), 200
    else:
        # Unauthorized if login fails
        return jsonify({"error": "Invalid username or password"}), 401

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We use the `jwt` module from PyJWT (install it via `pip install PyJWT`). JWT (JSON Web Token) is a standard for tokens that contain claims (payload data) that are signed (not encrypted) by the server’s secret so they cannot be forged.
* We set `app.config['SECRET_KEY']` to a secret value. This key is used to sign the JWT (and also generally used by Flask for sessions and security-related needs). In a real application, **never hardcode the secret key in code** – you’d load it from an environment variable or config file, but for our demonstration it’s here.
* We have a dummy `USER_DATA` dictionary simulating user accounts. In practice, you’d verify user credentials from a database. Here, we have two users: “alice” and “bob” with their passwords in plaintext for simplicity.
* The `/login` route accepts POST requests with JSON containing `"username"` and `"password"`.

  * We parse the JSON with `request.get_json()`. If JSON is missing or doesn’t have both fields, return 400.
  * We then check if the provided username exists in `USER_DATA` and if the password matches the stored password.
  * If the credentials are valid, we proceed to create a JWT **payload**. Typically, you’d include a user identifier and maybe some other claims:

    * We include `"user": username` as an identifier in the token payload.
    * We include an `"exp"` (expiration) claim set to current time + 1 hour. The `datetime.now(timezone.utc) + timedelta(hours=1)` gives an aware datetime one hour from now in UTC. The `exp` claim is standard in JWTs to indicate token expiration time.
  * We call `jwt.encode(payload, app.config['SECRET_KEY'], algorithm="HS256")` to encode the token.

    * HS256 means HMAC-SHA256 signing algorithm, which uses our secret key to sign the token so we can verify it later. This returns a token (in PyJWT v2, it returns a byte string; we ensure it’s a string with the `decode` logic).
    * The token is essentially three base64 parts (header, payload, signature) separated by dots. It might look like a long string of characters (e.g., `eyJ0eXAiOiJKV1QiLCJhbGci...`).
  * We return the token as JSON: `{"token": "<token_str>"}`.
  * If credentials are invalid, we return 401 Unauthorized with an error.
* **Important:** We included the `"exp"` claim, which PyJWT will interpret and enforce on decode (it will raise an exception if the token is expired when we verify it later). If we omitted `"exp"`, the token would never expire by itself. Always set an expiration for JWTs so they eventually become invalid.
* Also note: In a real scenario, you wouldn’t store plaintext passwords or even have them in a dictionary. We will handle password hashing in a later program. Here it’s plain for simplicity.

### Testing with Postman

1. **Get a JWT token**: Start `app5.py`. In Postman, create a POST request to `http://localhost:5000/login`. Set the body to JSON (raw, application/json) and provide a JSON object with a valid username and password. For example:

   ```json
   {
     "username": "alice",
     "password": "alice123"
   }
   ```

   Send the request. If the credentials are correct, you should get **200 OK** with a JSON response containing a `token` field. The token will be a long string of characters (JWTs typically have two dots in them, separating three parts). It will look something like:
   `{"token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWxpY2UiLCJleHAiOi...etc"}`.

   * Copy this token value (without the quotes) to use in the next step.
   * If you send wrong credentials (e.g. username exists but wrong password, or unknown username), you’ll get a **401** with `{"error": "Invalid username or password"}`.
   * If you omit username or password, you’ll get **400** with the appropriate error message.
2. **Examine the token (optional)**: JWTs are not encrypted, they are just encoded. If you paste the token into a tool like [jwt.io](https://jwt.io/) (or use a JWT library to decode without verifying), you can actually see the payload. You should see the `user` claim (e.g. "alice") and an `exp` timestamp. This is just to illustrate that JWT payload is visible to clients (so never put secret info in JWT payload). The important thing is the signature (generated using SECRET\_KEY) which clients cannot fake.
3. **Token expiration test (optional)**: Our token expires in 1 hour. You can test an expired token by manually setting a short expiration (for instance, change `timedelta(minutes=1)` for a quick test, or even a past time to simulate expiration). The actual usage of `exp` will be shown when we decode the token in the next program.

So far, we have a way to generate tokens for valid users. Next, we will create routes that require this token (JWT) to be provided, demonstrating route protection using JWT verification.

## Program 6: Protecting Routes with JWT (Bearer Token Authentication)

**Goal:** Use JWTs to secure certain API routes. We will implement a middleware-like check in protected routes that verifies the JWT from the **Authorization header**. This is commonly done with a "Bearer" token scheme where the header is `Authorization: Bearer <JWT>`.

### Code

```python
# app6.py - JWT-protected routes

import jwt
from functools import wraps
from flask import Flask, request, jsonify

app = Flask(__name__)
app.config['SECRET_KEY'] = 'supersecretkey'  # same secret used for token encoding

# Decorator for routes that need JWT authentication
def token_required(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        auth_header = request.headers.get('Authorization')
        if not auth_header:
            return jsonify({"error": "Authentication token is missing"}), 401
        # Expect header format: "Bearer <JWT>"
        parts = auth_header.split()
        if parts[0].lower() != 'bearer' or len(parts) != 2:
            return jsonify({"error": "Invalid token header. Use Bearer <Token>"}), 401
        token = parts[1]
        try:
            # Decode the token using the secret; raises exceptions if invalid or expired
            payload = jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])
        except jwt.ExpiredSignatureError:
            return jsonify({"error": "Token has expired"}), 401
        except jwt.InvalidTokenError:
            return jsonify({"error": "Token is invalid"}), 401

        # Token is valid; payload is available. You could attach user info to request here if needed.
        return f(*args, **kwargs, user_payload=payload)
    return decorated

# Unprotected route (for comparison)
@app.route('/public', methods=['GET'])
def public():
    return jsonify({"message": "Anyone can access this public route."}), 200

# Protected route - requires a valid JWT
@app.route('/protected', methods=['GET'])
@token_required
def protected(user_payload):
    # user_payload is injected by the decorator, contains decoded token data
    user = user_payload.get("user")
    return jsonify({"message": f"Hello, {user}. This is a protected route."}), 200

# Protected admin-only route
@app.route('/admin-area', methods=['GET'])
@token_required
def admin_area(user_payload):
    user = user_payload.get("user")
    # For demonstration, suppose 'alice' is an admin and 'bob' is not
    if user != 'alice':  
        return jsonify({"error": "Admin access required"}), 403
    return jsonify({"message": f"Welcome to the admin area, {user}!"}), 200

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We define a decorator `token_required` to avoid repeating token verification logic for each protected route. The `functools.wraps` decorator ensures the wrapped function’s metadata is preserved (optional but good practice).

  * The decorator function checks the `Authorization` header in the request. We expect it to contain a bearer token in the form "Bearer \<JWT>".
  * If the header is missing, we return 401 immediately.
  * If the header format is wrong (e.g., missing "Bearer" or token part), we also return 401 with an error. The client should send `Authorization: Bearer YOUR_TOKEN_HERE`.
  * If we have a token, we attempt to decode it using `jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])`. This will verify the signature and, if the token has an `"exp"` claim, also check expiration.

    * On success, we get the `payload` (which we set in Program 5 to include `"user"` and `"exp"`).
    * If the token is expired, `jwt.ExpiredSignatureError` is raised; we catch it and return 401 with a specific message.
    * If any other issue occurs (wrong signature, malformed token, etc.), `jwt.InvalidTokenError` is caught and we return 401.
  * If the token is valid, we call the actual route function `f`, passing through any original arguments and adding `user_payload=payload`. This allows the protected route to know the content of the token (like who the user is).
* We have a `/public` route that is accessible by anyone (no decorator).
* We have a `/protected` route with `@token_required`. The function signature now includes `user_payload` because our decorator will pass it. This route simply greets the user by name using the token’s data.
* We also add an `/admin-area` route to demonstrate **role-based access control**. In this simple scenario, we decide that user "alice" is an admin, others are not. (We don't have roles explicitly stored yet, but we're simulating.)

  * We use `@token_required` as well, so only a valid token gets this far.
  * We then check the `user` from the token payload. If it’s not "alice", we return 403 Forbidden. If it is "alice", we allow access.
  * In a real app, you might include a `"role"` claim in the JWT or look up the user’s role from the database. We’ll refine this when we integrate a database.
* Why **Bearer**? "Bearer" is just a convention indicating the type of auth token. The header `Authorization: Bearer <token>` is a common scheme for JWTs in REST APIs. It's not enforced by Flask, but by using it we follow standards.
* With this setup, any route we decorate with `@token_required` will require a valid JWT. We can easily extend the decorator to handle roles, but for clarity we did role check inside the route.

### Testing with Postman

Before testing, ensure you have a token from the previous login program (Program 5). Alternatively, we can integrate the login route into this app for a seamless test, but assuming you have `app5.py` running or can copy the token. For testing, let's use the token for "alice" to test admin route and "bob" to see the 403.

1. **Public route**: Send GET to `http://localhost:5000/public`. This should return 200 with `{"message": "Anyone can access this public route."}`. No token needed.
2. **Protected route (without token)**: Send GET to `http://localhost:5000/protected` with **no Authorization header**. You should get 401 Unauthorized, and the JSON `{"error": "Authentication token is missing"}`.
3. **Protected route (with token)**: Now add the token. In Postman, under Authorization, choose Bearer Token and paste your JWT (or manually add header `Authorization: Bearer <token>`).

   * Use the token for **alice** (from Program 5, username "alice"). Send GET to `/protected`. Expected result: 200 OK, `{"message": "Hello, alice. This is a protected route."}`.
   * Try with **bob**’s token (if you have one from login as bob): It should say "Hello, bob..." accordingly, as long as token is valid.
   * Try altering the token (e.g., change one character) and send: You should get 401 Invalid token.
   * If you wait until the token expires (1 hour) or manually alter the `"exp"` to a past time before encoding, you will get `{"error": "Token has expired"}` with 401.
4. **Admin-only route**:

   * Using **bob**’s token, send GET to `http://localhost:5000/admin-area`. Bob is not an admin in our logic, so even though the token is valid, the route should return **403 Forbidden** with `{"error": "Admin access required"}`.
   * Using **alice**’s token, send GET to `/admin-area`. Alice should get 200 OK with `{"message": "Welcome to the admin area, alice!"}`.
   * If you send no token or invalid token to `/admin-area`, you’ll get the same 401 responses as other protected routes because the token check happens first in the decorator.

Now we have a basic token-based auth system: a login route issues a JWT, and protected routes require the JWT. We have also implemented a simple role check. The next step is to integrate a database for storing users and roles, instead of our in-memory `USER_DATA`.

## Program 7: Flask SECRET\_KEY and Its Usage

**Goal:** Understand the significance of Flask’s `SECRET_KEY`. We’ve already been using `SECRET_KEY` for JWT signing. Here, we’ll briefly demonstrate its role in Flask (session signing) and reaffirm its importance in keeping tokens secure.

### Code

```python
# app7.py - Demonstrating SECRET_KEY usage and secure sessions

from flask import Flask, session, jsonify

app = Flask(__name__)

# Set a secret key for secure sessions and JWT signing
app.config['SECRET_KEY'] = 'myverystrongsecretkey'

@app.route('/set-session')
def set_session():
    # Example of using Flask session (which requires SECRET_KEY)
    session['framework'] = 'Flask'
    return jsonify({"message": "Session value set. (Check /get-session)"}), 200

@app.route('/get-session')
def get_session():
    framework = session.get('framework')
    return jsonify({"framework": framework}), 200

# (In a real app, JWT creation would also use this SECRET_KEY as shown in previous programs.)

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We configure `app.config['SECRET_KEY']` with a random-looking string. The **secret key** is used by Flask for securely signing the session cookie (among other things). If you do not set a secret key, Flask’s session functionality will not work (it will complain or not allow setting session data).
* In previous programs, we used this key for JWT. In fact, if using extensions like Flask-JWT-Extended, it would use Flask’s `SECRET_KEY` by default to sign tokens.
* In the code above, we show a simple usage of Flask’s session:

  * The `/set-session` route puts a value into the `session` object. The Flask session is a secure cookie stored on the client; data is cryptographically signed (not encrypted) using the `SECRET_KEY`. Setting `session['framework'] = 'Flask'` will send a cookie to the client.
  * The `/get-session` route reads `session.get('framework')` and returns it.
  * This is just to illustrate one use of `SECRET_KEY`. The actual output is trivial (just returning `"Flask"`), but what's important is that this wouldn't work at all if `SECRET_KEY` was not set. Flask would not set a session cookie without a secret to sign it (to prevent tampering).
* In the context of our API, the `SECRET_KEY` secures:

  * **Session Cookies**: If we were using session-based auth or storing anything in session, it’s signed with this key. If an attacker stole or guessed the `SECRET_KEY`, they could forge session cookies.
  * **JWT Signing**: We manually used it in `jwt.encode`. The strength of JWT’s security is directly tied to keeping this key secret. If leaked, someone could generate valid JWTs and impersonate users.
  * **Other extensions**: Some Flask extensions (e.g., CSRF protection in forms, Flask-Login cookies) also use `SECRET_KEY` to sign tokens or cookies.
* **Choosing a SECRET\_KEY**: It should be a long, random string of bytes. The documentation even suggests using `secrets.token_hex()` to generate one. For development, you might hardcode it, but in production, load it from an environment variable and keep it secret.
* We won't extensively test session behavior via Postman (since it’s more of a web/browser concept with cookies), but this program serves as a conceptual lecture about `SECRET_KEY`.

### Testing with Postman

You can still test the above routes in Postman, though it’s slightly artificial:

* GET `http://localhost:5000/set-session`. The response will be a JSON message. More importantly, check the response headers in Postman. You should see a header called **Set-Cookie**. It will set something like `session=<long_value>; HttpOnly; Path=/`. This is Flask sending the signed session cookie to the client.
* In Postman, by default, it will not automatically send that cookie on the next request unless you handle it. For a quick test, copy the Set-Cookie value.
* Now do GET `http://localhost:5000/get-session`. In Postman, go to the Headers tab of the request and add a header: `Cookie: session=<the value you copied>`. This simulates the browser sending the session cookie back.
* The response should be `{"framework": "Flask"}` confirming that the session data was stored and retrieved using the secret key to validate the cookie.
* If you modify the cookie value (simulate tampering), Flask will reject it and `session.get('framework')` would return `None` because the signature check fails.

This demonstrates the importance of `SECRET_KEY` in maintaining session integrity and any signed data. Always keep your secret key safe and never expose it. Next, we’ll integrate a MySQL database to store users and illustrate a more persistent authentication system.

## Program 8: MySQL Database Integration using Flask-MySQLdb

**Goal:** Connect our Flask app to a MySQL database using the **Flask-MySQLdb** extension, and perform basic operations. We will set up a MySQL connection, create a user table (if not exists), and demonstrate a simple query. This lays the groundwork for storing user credentials in a database.

### Code

```python
# app8.py - MySQL integration example with Flask-MySQLdb

from flask import Flask, jsonify
from flask_mysqldb import MySQL

app = Flask(__name__)
# MySQL configuration (adjust with your MySQL credentials and database name)
app.config['MYSQL_HOST'] = 'localhost'
app.config['MYSQL_USER'] = 'root'
app.config['MYSQL_PASSWORD'] = 'your_mysql_password'
app.config['MYSQL_DB'] = 'flaskapi'
app.config['MYSQL_CURSORCLASS'] = 'DictCursor'  # optional: to get results as dicts

mysql = MySQL(app)

# Initialize database table for users (if not exists)
with app.app_context():
    cur = mysql.connection.cursor()
    # Create users table with id, username, password, role
    cur.execute("""
        CREATE TABLE IF NOT EXISTS users (
            id INT AUTO_INCREMENT PRIMARY KEY,
            username VARCHAR(50) UNIQUE NOT NULL,
            password VARCHAR(100) NOT NULL,
            role VARCHAR(20) NOT NULL
        )
    """)
    # Insert a demo user if not exists
    cur.execute("SELECT * FROM users WHERE username=%s", ("alice",))
    result = cur.fetchone()
    if not result:
        # Insert a default user 'alice' with password 'alice123' and role 'admin'
        cur.execute("INSERT INTO users (username, password, role) VALUES (%s, %s, %s)", 
                    ("alice", "alice123", "admin"))
        mysql.connection.commit()
    cur.close()

@app.route('/users', methods=['GET'])
def get_users():
    cur = mysql.connection.cursor()
    cur.execute("SELECT id, username, role FROM users")
    rows = cur.fetchall()
    cur.close()
    # `rows` will be a list of dicts because we set cursorclass to DictCursor
    return jsonify(rows), 200

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We use `flask_mysqldb.MySQL` extension to integrate with a MySQL database. Make sure to install it: `pip install flask-mysqldb`. (Also ensure MySQL server is running and accessible.)
* We configure database connection details:

  * `MYSQL_HOST`, `MYSQL_USER`, `MYSQL_PASSWORD`, `MYSQL_DB` are set to connect to our MySQL. Adjust these to your environment (e.g., if you have a different user or password, and create a database named `flaskapi` for this exercise).
  * `MYSQL_CURSORCLASS = 'DictCursor'` is optional but convenient – it means fetch operations will return dictionaries (column name to value) instead of tuples.
* We create a `mysql = MySQL(app)` which sets up the connection. This extension will handle connections for us, letting us use `mysql.connection.cursor()` to get a cursor.
* Using an application context (`with app.app_context():`), we run some startup SQL to ensure a table and a default user:

  * We execute a SQL statement to create a `users` table if it doesn’t exist, with columns:

    * `id`: auto-increment primary key.
    * `username`: unique, up to 50 chars.
    * `password`: up to 100 chars (we'll later store hashed passwords which can be longer than plain).
    * `role`: e.g., "admin" or "user".
  * We then check if a user "alice" exists. If not, we insert a default user:

    * Username "alice", password "alice123", role "admin".
    * We commit the transaction to save changes.
  * This block ensures we have at least one user to work with for testing. In a real application, you'd manage migrations or have separate setup scripts.
* We define a GET route `/users` which will retrieve all users (id, username, role) from the database:

  * We get a cursor with `mysql.connection.cursor()`, execute a SELECT query, and fetch all results.
  * After fetching, we close the cursor.
  * We then `return jsonify(rows)`. If using `DictCursor`, each row is a dict like `{"id": ..., "username": ..., "role": ...}`. Flask’s jsonify can handle a list of dicts, converting it to a JSON array.
  * If not using DictCursor, `rows` would be a list of tuples; we’d have to manually format them or specify columns.
* This program doesn’t yet involve JWT or auth – it’s focusing on making sure our Flask app can talk to MySQL and that the users table is in place for the next steps.

### Setting up MySQL (guidance)

Before running this, ensure:

* MySQL server is installed and running.
* A database named `flaskapi` (as used in config) exists. You can create one via MySQL client: `CREATE DATABASE flaskapi;`.
* The user in config (here 'root' with `your_mysql_password`) has access to this database. Adjust if needed (for example, you might create a specific user for the app).
* The flask-mysqldb extension actually uses the MySQLdb (mysqlclient) driver under the hood. On some systems, you may need to install OS-level MySQL client libraries. If you encounter an error on installing, refer to Flask-MySQLdb docs for dependency instructions.

### Testing with Postman

1. **Start the application**: Run `app8.py`. Watch the console for any errors on connecting to the database. If everything is correct, the app will start and on first run create the table and insert the user.
2. **Test the `/users` endpoint**: In Postman, send a GET request to `http://localhost:5000/users`. You should get a JSON array of users. For example, after first run it might return:

   ```json
   [
     {
       "id": 1,
       "username": "alice",
       "role": "admin"
     }
   ]
   ```

   If you run it again (without resetting the DB), it will still show "alice" once because we only insert if not exists.
3. **Verify data in MySQL** (optional): Connect to your MySQL database (using CLI or a tool) and run `SELECT * FROM users;`. You should see the "alice" user. You can also add more users via SQL if you want to test (just ensure unique usernames).
4. If you see any errors related to MySQL connection, double-check your host/user/password, and that MySQL service is running. Also ensure the `flaskapi` database exists.

Now that we have database integration, we can modify our login and role checks to use real database data instead of the dummy dictionary. We will do that in the next program by creating a login endpoint that verifies user credentials from the database and generates a JWT.

## Program 9: Login Endpoint with Database and JWT Generation

**Goal:** Create a `/login` endpoint that authenticates a user against the MySQL database and returns a JWT token. This combines our previous JWT creation logic with the database of users. We’ll also update the token payload to include the user’s role for authorization purposes.

### Code

```python
# app9.py - Login with MySQL database and JWT token response

import jwt
from datetime import datetime, timedelta, timezone
from flask import Flask, request, jsonify
from flask_mysqldb import MySQL
from werkzeug.security import check_password_hash

app = Flask(__name__)
app.config['SECRET_KEY'] = 'myverystrongsecretkey'
app.config['MYSQL_HOST'] = 'localhost'
app.config['MYSQL_USER'] = 'root'
app.config['MYSQL_PASSWORD'] = 'your_mysql_password'
app.config['MYSQL_DB'] = 'flaskapi'
app.config['MYSQL_CURSORCLASS'] = 'DictCursor'

mysql = MySQL(app)

@app.route('/login', methods=['POST'])
def login():
    data = request.get_json()
    if not data or 'username' not in data or 'password' not in data:
        return jsonify({"error": "Username and password required"}), 400

    username = data['username']
    password = data['password']
    cur = mysql.connection.cursor()
    cur.execute("SELECT id, username, password, role FROM users WHERE username=%s", (username,))
    user = cur.fetchone()
    cur.close()
    if not user:
        # Username not found
        return jsonify({"error": "Invalid username or password"}), 401

    # user['password'] is the stored password (hashed or plain depending on earlier setup)
    stored_password = user['password']
    # We'll assume passwords are stored in plain for now or already hashed appropriately.
    # If hashed (which we will do in next program), use check_password_hash
    if stored_password == password or check_password_hash(stored_password, password):
        # Build token payload
        payload = {
            "user_id": user['id'],
            "username": user['username'],
            "role": user['role'],
            "exp": datetime.now(timezone.utc) + timedelta(hours=1)
        }
        token = jwt.encode(payload, app.config['SECRET_KEY'], algorithm="HS256")
        token_str = token if isinstance(token, str) else token.decode('utf-8')
        return jsonify({"token": token_str}), 200
    else:
        return jsonify({"error": "Invalid username or password"}), 401

# (We could include protected routes here as in Program 6, but focusing on login for this example.)

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We import `check_password_hash` from `werkzeug.security`. We will use this in anticipation of storing hashed passwords. For now, our database has plaintext `"alice123"`, so `check_password_hash` won’t be used (it will return False since the stored password isn’t a hash). We include it to show where it fits when we improve security.
* The app is configured with the same `SECRET_KEY` and MySQL connection as before (pointing to the `flaskapi` database with the `users` table).
* The `/login` route:

  * Expects JSON with username and password, similar to Program 5. We validate presence of both fields.
  * We query the database for a user with the given username: selecting `id, username, password, role` from `users`. We fetch one result (because username is unique, either one or none).
  * If `user` is None, that means the username doesn’t exist, so we return 401 (don’t reveal which part is wrong for security – just a generic invalid credentials message).
  * If a user is found, we get the stored password. In our current setup (from Program 8), we stored `"alice123"` in plain text. In future (Program 11) we will store hashed, at which point `stored_password` will be a hash string.
  * We then check the provided password:

    * If we have stored plaintext (like "alice123"), `stored_password == password` will be True for a correct password.
    * If we have a hashed password, `check_password_hash(stored_password, password)` will return True if the hash matches the given password.
    * We combine these conditions with OR, assuming that either the password is correct in plaintext or when hashed. (This is for smooth transition – in practice, once you hash passwords, you’d only use the hash check.)
  * If the password check passes, we prepare the JWT payload:

    * We include `user_id`, `username`, and `role` from the database. Now the token carries the user’s role too.
    * We include `exp` for 1 hour expiration.
  * We encode the token with `jwt.encode` and return it as before.
  * If password check fails, return 401.
* Essentially, we replaced the dummy user dictionary with a real database lookup. Also, the token now has `role` which we can use in protected endpoints to differentiate admin vs regular user (no role check here, but we will adjust in the next program).
* Notice: We did not create the table or default user here because we expect Program 8 already created them. If running this standalone, ensure the table and a user exist in the DB (from previous step). For integration, one could combine app8 and app9 logic or ensure to run app8 first. In a real app, you'd have a consistent single app with both table creation and routes.

### Testing with Postman

Make sure you have the MySQL database running with the `users` table and at least one user (e.g., "alice" as inserted previously).

1. **Test correct credentials**: Send a POST to `http://localhost:5000/login` with JSON body:

   ```json
   {
     "username": "alice",
     "password": "alice123"
   }
   ```

   You should get **200 OK** and a JSON response like `{"token": "<JWT_TOKEN_HERE>"}`. Copy the token for later. The token payload (if decoded) should have alice’s id, username, and role "admin".
2. **Test incorrect password**: Change the password in the JSON to something else. You should get **401 Unauthorized** with `{"error": "Invalid username or password"}`.
3. **Test non-existent user**: Try a username that’s not in the DB. Also should yield 401 with the same message.
4. **Omitted fields**: Send an empty JSON or missing username or password. You should get **400 Bad Request** with `{"error": "Username and password required"}`.
5. **Token usage**: Although this program doesn’t define protected routes, you can manually test the returned token by decoding it using a JWT tool or by writing a small decode snippet. It should contain the fields we included. We will use it in next program.

Now we have a robust login that checks the database. Next, we will enforce role-based access using the role stored in the token and also improve security by hashing passwords in the database.

## Program 10: Role-Based Access Control and Flask Blueprints

**Goal:** Use the user’s role to control access to certain endpoints (admin vs user), and introduce Flask **Blueprints** to organize our routes. We will create separate blueprints for authentication and for main API functionality, demonstrating modularity.

### Code

```python
# app10.py - Role-based access control and using Blueprints

import jwt
from datetime import datetime, timedelta, timezone
from functools import wraps
from flask import Flask, request, jsonify, Blueprint
from flask_mysqldb import MySQL

app = Flask(__name__)
app.config['SECRET_KEY'] = 'myverystrongsecretkey'
app.config['MYSQL_HOST'] = 'localhost'
app.config['MYSQL_USER'] = 'root'
app.config['MYSQL_PASSWORD'] = 'your_mysql_password'
app.config['MYSQL_DB'] = 'flaskapi'
app.config['MYSQL_CURSORCLASS'] = 'DictCursor'
mysql = MySQL(app)

# Blueprint for auth-related routes
auth_bp = Blueprint('auth', __name__, url_prefix='/auth')
# Blueprint for API routes
api_bp = Blueprint('api', __name__, url_prefix='/api')

# Decorator to require valid JWT for protected routes
def token_required(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        auth_header = request.headers.get('Authorization')
        if not auth_header:
            return jsonify({"error": "Authentication token is missing"}), 401
        parts = auth_header.split()
        if len(parts) != 2 or parts[0].lower() != 'bearer':
            return jsonify({"error": "Invalid token header. Use Bearer <token>"}), 401
        token = parts[1]
        try:
            payload = jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])
        except jwt.ExpiredSignatureError:
            return jsonify({"error": "Token has expired"}), 401
        except jwt.InvalidTokenError:
            return jsonify({"error": "Invalid token"}), 401

        # Attach payload to keyword arguments for use in the route
        return f(*args, **kwargs, token_payload=payload)
    return decorated

@auth_bp.route('/login', methods=['POST'])
def login():
    data = request.get_json()
    if not data or 'username' not in data or 'password' not in data:
        return jsonify({"error": "Username and password required"}), 400
    username = data['username']
    password = data['password']
    cur = mysql.connection.cursor()
    cur.execute("SELECT id, username, password, role FROM users WHERE username=%s", (username,))
    user = cur.fetchone()
    cur.close()
    if not user or user['password'] != password:
        return jsonify({"error": "Invalid username or password"}), 401

    # Create token payload with role
    payload = {
        "user_id": user['id'],
        "username": user['username'],
        "role": user['role'],
        "exp": datetime.now(timezone.utc) + timedelta(hours=1)
    }
    token = jwt.encode(payload, app.config['SECRET_KEY'], algorithm="HS256")
    token_str = token if isinstance(token, str) else token.decode('utf-8')
    return jsonify({"token": token_str}), 200

@api_bp.route('/data', methods=['GET'])
@token_required
def get_data(token_payload):
    # A protected route accessible to any logged-in user (regardless of role)
    user = token_payload['username']
    return jsonify({"message": f"Hello, {user}. Here is the confidential data."}), 200

@api_bp.route('/admin', methods=['GET'])
@token_required
def admin_area(token_payload):
    # A protected route accessible only to admins
    if token_payload.get('role') != 'admin':
        return jsonify({"error": "Admin access required"}), 403
    user = token_payload['username']
    return jsonify({"message": f"Welcome to the admin panel, {user}."}), 200

# Register blueprints with the app
app.register_blueprint(auth_bp)
app.register_blueprint(api_bp)

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We create two **Blueprints**:

  * `auth_bp` for authentication-related routes, with URL prefix `/auth`. This will group routes like login (and in the future maybe register, logout, etc.).
  * `api_bp` for our main API routes, with prefix `/api`. This could group various endpoints that the API provides.
* The `token_required` decorator is similar to Program 6, but we place it at the top-level of this file (outside of blueprint definitions, which is fine).
* We define the `/auth/login` route inside the `auth_bp` blueprint. It’s basically the same login logic as Program 9 (without hashing yet, assuming plaintext match for now). It returns a token containing the user’s role.

  * Note: The route is `@auth_bp.route('/login')` with prefix `/auth`, so full URL will be `/auth/login`.
* Under `api_bp`, we define two routes:

  * `/api/data` which is a generic protected resource accessible to any valid token (any logged-in user). It just returns a hello message with the user’s name.
  * `/api/admin` which is protected and also checks `token_payload['role']`. If role isn’t "admin", it returns 403 Forbidden. If role is admin, returns a welcome message.
* We register the blueprints: `app.register_blueprint(auth_bp)` and `app.register_blueprint(api_bp)`. The blueprint prefixes (`/auth` and `/api`) ensure these routes are mounted under those paths.
* **Why use Blueprints?** In a larger application, you might separate your routes into different files or logical groups. For example, an `auth.py` file with an `auth_bp` blueprint for auth routes, a `api.py` for main API, etc. This keeps the code organized. Here we show the structure in one file for clarity, but one can imagine splitting them.
* The logic inside is straightforward and similar to earlier programs, just organized differently. We still use the global `app.config` and `mysql` in the blueprint routes, which is fine because they have access to those (since we created `mysql = MySQL(app)` at the top in the app context).
* This program ties together login, JWT, role checking, and blueprint usage.

### Testing with Postman

Ensure the MySQL DB has users (especially an admin user like "alice" as we inserted). Run `app10.py`.

1. **Login (auth blueprint)**: Send POST to `http://localhost:5000/auth/login` with a valid user (e.g., alice). You should get a token as before.

   * If you use "alice" with "alice123", you get a token which encodes role "admin".
   * If you use a non-admin user (if you added one, say "bob"), you get a token with role "user".
   * Bad credentials should yield 401, missing fields 400.
2. **Access /api/data**: Using a token from either user, send GET to `http://localhost:5000/api/data` with `Authorization: Bearer <token>`.

   * For a valid token, you should get a message greeting that user. Admin or not doesn’t matter here, any logged user can see it. If token missing or invalid, you get 401.
3. **Access /api/admin**:

   * Using **admin’s token** (alice’s token): GET `http://localhost:5000/api/admin` with the token. Should get 200 and welcome message.
   * Using a non-admin token: GET `/api/admin` with that token. Should get 403 Forbidden with `{"error": "Admin access required"}`.
   * Without token or invalid token: will be caught by `token_required` first, resulting in 401.
4. **Blueprint route prefixes**: Notice that in Postman we had to include `/auth` or `/api`. If you try `http://localhost:5000/login` (without /auth), you’ll get 404 because the login route is under the blueprint prefix. Blueprints basically prepend that prefix to all its routes, organizing the URL space.

At this stage, our application is well-structured and secure for basic needs. The final improvement will be to hash user passwords in the database instead of storing plaintext, and update our login check accordingly.

## Program 11: Secure Password Storage with Werkzeug Security (Hashing Passwords)

**Goal:** Enhance our user authentication by storing **hashed passwords** instead of plaintext. We will use `werkzeug.security.generate_password_hash` to hash passwords when creating users, and `check_password_hash` to verify. We’ll add a user registration endpoint to demonstrate storing a hashed password, and modify login to use hash check.

### Code

```python
# app11.py - Password hashing and verification with Werkzeug

from flask import Flask, request, jsonify
from flask_mysqldb import MySQL
from werkzeug.security import generate_password_hash, check_password_hash
import jwt
from datetime import datetime, timedelta, timezone
from functools import wraps, partial

app = Flask(__name__)
app.config['SECRET_KEY'] = 'myverystrongsecretkey'
app.config['MYSQL_HOST'] = 'localhost'
app.config['MYSQL_USER'] = 'root'
app.config['MYSQL_PASSWORD'] = 'your_mysql_password'
app.config['MYSQL_DB'] = 'flaskapi'
app.config['MYSQL_CURSORCLASS'] = 'DictCursor'
mysql = MySQL(app)

# (Reusing token_required decorator from previous program)
def token_required(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        auth_header = request.headers.get('Authorization')
        if not auth_header:
            return jsonify({"error": "Authentication token is missing"}), 401
        parts = auth_header.split()
        if len(parts) != 2 or parts[0].lower() != 'bearer':
            return jsonify({"error": "Invalid token header. Use Bearer <token>"}), 401
        token = parts[1]
        try:
            payload = jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])
        except jwt.ExpiredSignatureError:
            return jsonify({"error": "Token has expired"}), 401
        except jwt.InvalidTokenError:
            return jsonify({"error": "Invalid token"}), 401
        return f(*args, **kwargs, token_payload=payload)
    return decorated

@app.route('/register', methods=['POST'])
def register():
    data = request.get_json()
    if not data or 'username' not in data or 'password' not in data or 'role' not in data:
        return jsonify({"error": "Username, password, and role are required"}), 400

    username = data['username']
    password = data['password']
    role = data['role']
    # Basic validation: ensure role is either 'admin' or 'user'
    if role not in ('admin', 'user'):
        return jsonify({"error": "Role must be 'admin' or 'user'"}), 400

    # Check if username already exists
    cur = mysql.connection.cursor()
    cur.execute("SELECT id FROM users WHERE username=%s", (username,))
    existing = cur.fetchone()
    if existing:
        cur.close()
        return jsonify({"error": "Username already exists"}), 409  # Conflict
    # Hash the password
    hashed_pw = generate_password_hash(password)  # default method=pbkdf2:sha256
    # Insert new user
    cur.execute("INSERT INTO users (username, password, role) VALUES (%s, %s, %s)",
                (username, hashed_pw, role))
    mysql.connection.commit()
    cur.close()
    return jsonify({"message": f"User {username} registered successfully"}), 201

@app.route('/login', methods=['POST'])
def login():
    data = request.get_json()
    if not data or 'username' not in data or 'password' not in data:
        return jsonify({"error": "Username and password required"}), 400
    username = data['username']
    password = data['password']
    cur = mysql.connection.cursor()
    cur.execute("SELECT id, username, password, role FROM users WHERE username=%s", (username,))
    user = cur.fetchone()
    cur.close()
    if not user:
        return jsonify({"error": "Invalid username or password"}), 401
    # user['password'] is now a hashed password
    if not check_password_hash(user['password'], password):
        return jsonify({"error": "Invalid username or password"}), 401

    # Create token payload
    payload = {
        "user_id": user['id'],
        "username": user['username'],
        "role": user['role'],
        "exp": datetime.now(timezone.utc) + timedelta(hours=1)
    }
    token = jwt.encode(payload, app.config['SECRET_KEY'], algorithm="HS256")
    token_str = token if isinstance(token, str) else token.decode('utf-8')
    return jsonify({"token": token_str}), 200

# Example protected route (as demonstration, requires any logged-in user)
@app.route('/profile', methods=['GET'])
@token_required
def profile(token_payload):
    return jsonify({
        "user_id": token_payload['user_id'],
        "username": token_payload['username'],
        "role": token_payload['role']
    }), 200

if __name__ == '__main__':
    app.run(debug=True)
```

### Explanation

* We added `generate_password_hash` and `check_password_hash` from Werkzeug. `generate_password_hash(password)` will create a secure hash (with salt) using a strong algorithm (default is PBKDF2-HMAC-SHA256 with many iterations, or even scrypt in latest Werkzeug). `check_password_hash(hashed, plain)` returns True if the plain password matches the given hash.
* The `/register` endpoint:

  * Expects JSON with `username`, `password`, and `role`.
  * It ensures none of these are missing and that role is either "admin" or "user" (for simplicity, we enforce only these two roles).
  * It checks if the username already exists in the DB. If yes, returns 409 Conflict error.
  * If new, it calls `generate_password_hash(password)` to hash the plaintext password. This returns a string like `"pbkdf2:sha256:260000$<salt>$<hash>"` (format may vary) which includes the method and salt and hashed value. Each call produces a different hash even for the same password due to random salt, but `check_password_hash` knows how to verify it.
  * It inserts the new user into the `users` table with the hashed password and given role, then commits and returns a 201 Created status with a success message.
* The `/login` endpoint:

  * Fetches the user by username as before.
  * If user not found, return 401.
  * If found, it uses `check_password_hash(user['password'], password)` to verify the provided password against the stored hash. If this returns False, credentials are wrong.
  * Only if the hash check passes do we generate the JWT token (with user\_id, username, role, exp) and return it.
* We included a sample protected route `/profile` that simply returns the info from `token_payload` to show that login+token works with hashed password too.
* Note: If you have existing users in the DB from previous steps with plaintext passwords, their `password` field is not hashed. The `check_password_hash` on a plaintext stored password will fail (since it expects a hash format). One approach is to re-register those users or update their passwords. Since we introduced a register route, you can add users properly. Or manually update the DB to replace plaintext with a generated hash for that password.
* For learning purposes, it’s okay to just register a new user via the new endpoint.

### Testing with Postman

If continuing from previous steps, consider clearing the `users` table or at least know that "alice" currently has a plaintext password. You can re-register her with the same username to update the password hash (our code would currently block duplicate usernames, so you might need to delete the old record or use a new username).

Let's test fresh:

1. **Register a new user**: POST `http://localhost:5000/register` with body:

   ```json
   {
     "username": "charlie",
     "password": "charlie123",
     "role": "user"
   }
   ```

   Expected: 201 Created, `{"message": "User charlie registered successfully"}`.

   * If you try the same username again, you should get 409 conflict.
   * Try with missing fields or an invalid role to test the 400 responses.
   * In the database, `users` table now has charlie with a hashed password (you can select to see it).
2. **Login with the new user**: POST `http://localhost:5000/login` with body:

   ```json
   { "username": "charlie", "password": "charlie123" }
   ```

   Expected: 200 OK with a token. This proves that our `check_password_hash` worked for the correct password. If you use a wrong password, you get 401.

   * If you still have "alice" in DB with plaintext "alice123", login will fail for her now because our code tries to treat that as a hash. You should update her entry. For now, use the users created properly via register.
3. **Use the token**: Copy the token from login. GET `http://localhost:5000/profile` with `Authorization: Bearer <token>`. You should get 200 and a JSON with your `user_id`, `username`, and `role`. This confirms the whole flow: registration with hashed password, login, token generation, and token verification on protected route.
4. **Security check**: If you inspect the database, the password is stored as a long hash string, not the original. Even if someone got read access to your DB, they can’t reverse these hashes (they are one-way and salted). This is critical for security best practices in real applications.

Finally, you can test an admin scenario: register an admin user and try using their token on an admin-only route (if you carry over the admin route logic from Program 10, or adapt a similar check in a route here). The principle remains the same.

