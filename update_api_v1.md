### **Basic Level**

#### **Program 1: Setting up Flask and Basic API Route**
- **Objective:** Understand how to set up a basic Flask application and create a simple API route.
- **Python Code:**
  ```python
  from flask import Flask, jsonify
  
  app = Flask(__name__)

  @app.route('/hello', methods=['GET'])
  def hello_world():
      return jsonify({"message": "Hello, World!"})

  if __name__ == '__main__':
      app.run(debug=True)
  ```
- **Explanation:** This code creates a simple Flask app with one route (`/hello`). It responds with a JSON message.
- **Testing with Postman:** 
  1. Open Postman, select **GET** method.
  2. Enter the URL `http://127.0.0.1:5000/hello`.
  3. Click **Send** to see the JSON response.
  4. **Output:** ` {"message": "Hello, World!"} `

#### **Program 2: Handling POST Requests and JSON Payload**
- **Objective:** Handle JSON payload in a POST request.
- **Python Code:**
  ```python
  from flask import Flask, request, jsonify

  app = Flask(__name__)

  @app.route('/data', methods=['POST'])
  def receive_data():
      data = request.get_json()  # Get JSON data from the request
      return jsonify({"received": data})

  if __name__ == '__main__':
      app.run(debug=True)
  ```
- **Explanation:** We use `request.get_json()` to extract JSON data from a POST request.
- **Testing with Postman:** 
  1. Choose **POST** method.
  2. Enter `http://127.0.0.1:5000/data`.
  3. In the **Body** tab, select **raw** and **JSON**.
  4. Send a JSON like `{"name": "Alice", "age": 25}` and see the response.
  5. **Output:** `{"name": "Alice", "age": 25}`
#### **Program 3: Using Query Parameters**
- **Objective:** Use query parameters in a GET request.
- **Python Code:**
  ```python
  from flask import Flask, request, jsonify

  app = Flask(__name__)

  @app.route('/greet', methods=['GET'])
  def greet_user():
      name = request.args.get('name', 'Guest')  # Get query parameter 'name'
      return jsonify({"message": f"Hello, {name}!"})

  if __name__ == '__main__':
      app.run(debug=True)
  ```
- **Explanation:** `request.args.get()` extracts query parameters.
- **Testing with Postman:** 
  1. Choose **GET** method.
  2. Enter `http://127.0.0.1:5000/greet?name=John`.
  3. Observe the returned message `Hello, John!`.
  4. **Output:** `{"message": "Hello John!"}`

#### **Program 4: Handling Responses and Status Codes**
- **Objective:** Send custom status codes and structured JSON responses.
- **Python Code:**
  ```python
  from flask import Flask, jsonify

  app = Flask(__name__)

  @app.route('/error', methods=['GET'])
  def error_example():
      return jsonify({"error": "Resource not found"}), 404

  if __name__ == '__main__':
      app.run(debug=True)
  ```
- **Explanation:** Returning a tuple allows us to specify both a response and a status code.
- **Testing with Postman:** 
  1. Choose **GET** method.
  2. Enter `http://127.0.0.1:5000/error`.
  3. See the error message and `404` status code.
    4. **Output:** `{"error": "Resource not found"}`

#### **Program 5: Basic Authentication**
- **Objective:** Set up basic HTTP authentication.
- **Python Code:**
  ```python
  from flask import Flask, request, jsonify
  from functools import wraps

  app = Flask(__name__)

  def check_auth(username, password):
      return username == 'admin' and password == 'password'

  def requires_auth(f):
      @wraps(f)
      # @wraps(f) decorator preserves the metadata (js name, docstring) of the original function f, 
      # so that the decorated function behaves the same as the original function.
      def decorated(*args, **kwargs):
          auth = request.authorization
          if not auth or not check_auth(auth.username, auth.password):
              return jsonify({"message": "Unauthorized"}), 401
          return f(*args, **kwargs)
      return decorated

  @app.route('/secure', methods=['GET'])
  @requires_auth
  def secure():
      return jsonify({"message": "This is a secure endpoint"})

  if __name__ == '__main__':
      app.run(debug=True)
  ```
- **Explanation:** The `requires_auth` decorator checks the credentials.
- **Testing with Postman:** 
  1. Choose **GET** method.
  2. Enter `http://127.0.0.1:5000/secure`.
  3. In Postman, go to the **Authorization** tab, choose **Basic Auth**, and enter `admin` and `password`.

#### **Program 6: Working with MySQL Database**
- **Objective:** Integrate MySQL database for storing and fetching data.
- **Python Code:**
  ```python
  from flask import Flask, jsonify
  from flask_mysqldb import MySQL

  app = Flask(__name__)
  app.config['MYSQL_HOST'] = 'localhost'
  app.config['MYSQL_USER'] = 'root'
  app.config['MYSQL_PASSWORD'] = 'admin'
  app.config['MYSQL_DB'] = 'api_test'

  mysql = MySQL(app)

  @app.route('/users', methods=['GET'])
  def get_users():
      cur = mysql.connection.cursor()
      cur.execute("SELECT * FROM api")
      data = cur.fetchall()
      return jsonify(data)

  if __name__ == '__main__':
      app.run(debug=True)
  ```
  `or`
    ```python
  from flask import Flask, jsonify
  from flask_mysqldb import MySQL
  import mysql.connector
  
  app = Flask(__name__)
  # app.config['MYSQL_HOST'] = 'localhost'
  # app.config['MYSQL_USER'] = 'root'
  # app.config['MYSQL_PASSWORD'] = 'admin'
  # app.config['MYSQL_DB'] = 'api_test'
  # mysql = MySQL(app)

  # @app.route('/users', methods=['GET'])
  # def get_users():
  #     cur = mysql.connection.cursor()
  #     cur.execute("SELECT * FROM api")
  #     data = cur.fetchall()
  #     return jsonify(data)
  
  db = mysql.connector.connect(
      host='localhost',
      user='root',
      password='admin',
      port=3306,
      database='api_test'
  )
    
  @app.route('/users', methods=["GET"])
  def get_users():
      cur = db.cursor()
      cur.execute("select * from api")
      data = cur.fetchall()
      return jsonify(data)

  if __name__ == '__main__':
      app.run(debug=True)
  ```
- **Explanation:** Using `Flask-MySQLdb` for connecting to MySQL and executing queries.
- **Testing with Postman:** 
  1. Ensure your MySQL server is running.
  2. Choose **GET** method, enter `http://127.0.0.1:5000/users`.
  3. The response will contain the user data from your `users` table.
  4. ![image](https://github.com/user-attachments/assets/7c8ff83f-e6a0-4e48-9d86-92770b755ff1)


#### **Program 7: Token-based Authentication (JWT)**
- **Objective:** Implement JWT authentication.
- **Python Code:**
  ```python
  from flask import Flask, request, jsonify
  import jwt
  import datetime

  app = Flask(__name__)
  app.config['SECRET_KEY'] = 'your_secret_key'

  @app.route('/login', methods=['POST'])
  def login():
      data = request.get_json()
      if data['username'] == 'admin' and data['password'] == 'password':
          token = jwt.encode({'user': 'admin', 'exp': datetime.datetime.utcnow() + datetime.timedelta(minutes=30)}, app.config['SECRET_KEY'], algorithm='HS256')
          return jsonify({'token': token})
      return jsonify({'message': 'Invalid credentials'}), 401

  if __name__ == '__main__':
      app.run(debug=True)
  ```
- **Explanation:** This generates a JWT token for valid users. The `exp` field adds an expiration time.
- **Testing with Postman:** 
  1. Choose **POST** method.
  2. Enter `http://127.0.0.1:5000/login`.
  3. Provide JSON body: `{"username": "admin", "password": "password"}`.
  4. Copy the JWT token from the response.
 
`or`
```python
from flask import Flask, request, jsonify
import jwt
import datetime
from functools import wraps

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'

# Token verification decorator
def token_required(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        token = None
        if 'Authorization' in request.headers:
            try:
                token = request.headers['Authorization'].split(" ")[1]
            except IndexError:
                return jsonify({'message': 'Token format invalid'}), 401
        if not token:
            return jsonify({'message': 'Token is missing!'}), 401
        try:
            data = jwt.decode(token, app.config['SECRET_KEY'], algorithms=['HS256'])
            current_user = data['user']
        except jwt.ExpiredSignatureError:
            return jsonify({'message': 'Token has expired'}), 401
        except jwt.InvalidTokenError:
            return jsonify({'message': 'Invalid token'}), 401
        return f(current_user, *args, **kwargs)
    return decorated

# Login Route - returns token
@app.route('/login', methods=['POST'])
def login():
    data = request.get_json()
    if data['username'] == 'mraheel' and data['password'] == '123456':
        token = jwt.encode({
            'user': 'admin',
            'exp': datetime.datetime.utcnow() + datetime.timedelta(minutes=30)
        }, app.config['SECRET_KEY'], algorithm='HS256')
        return jsonify({'token': token})
    return jsonify({'message': 'Invalid credentials'}), 401

# Protected route
@app.route('/protected', methods=['GET'])
@token_required
def protected(current_user):
    return jsonify({'message': f'Hello {current_user}, this is a protected route!'})

# Decode token route
@app.route('/decode', methods=['POST'])
def decode_token():
    token = request.json.get('token')
    try:
        data = jwt.decode(token, app.config['SECRET_KEY'], algorithms=['HS256'])
        return jsonify({'decoded': data})
    except jwt.ExpiredSignatureError:
        return jsonify({'error': 'Token expired'}), 401
    except jwt.InvalidTokenError:
        return jsonify({'error': 'Invalid token'}), 401

# Refresh token route
@app.route('/refresh', methods=['POST'])
def refresh_token():
    token = request.json.get('token')
    try:
        data = jwt.decode(token, app.config['SECRET_KEY'], algorithms=['HS256'], options={"verify_exp": False})
        new_token = jwt.encode({
            'user': data['user'],
            'exp': datetime.datetime.utcnow() + datetime.timedelta(minutes=30)
        }, app.config['SECRET_KEY'], algorithm='HS256')
        return jsonify({'new_token': new_token})
    except jwt.InvalidTokenError:
        return jsonify({'error': 'Invalid token'}), 401

if __name__ == '__main__':
    app.run(debug=True)
```

### 1. **Login to Get Token**
- **Method**: POST  
- **URL**: `http://127.0.0.1:5000/login`
- **Body (raw / JSON):**
```json
{
    "username": "mraheel",
    "password": "123456"
}
```

**Response Example:** 
```json
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGci..."
}
```

---

### 2. **Access Protected Route** 
- **Method**: GET  
- **URL**: `http://127.0.0.1:5000/protected`
- **Headers**:
```
Authorization: Bearer <paste_token_here>
```

**Expected Response:** 
```json
{
    "message": "Hello admin, this is a protected route!"
}
```

---

### 3. **Decode Token** 
- **Method**: POST  
- **URL**: `http://127.0.0.1:5000/decode`
- **Body (raw / JSON):**
```json
{
    "token": "<paste_token_here>"
}
```

**Expected Response:** 
```json
{
    "decoded": {
        "user": "admin",
        "exp": 1714712345
    }
}
```

---

### 4. **Refresh Token** 
- **Method**: POST  
- **URL**: `http://127.0.0.1:5000/refresh`
- **Body (raw / JSON):**
```json
{
    "token": "<paste_token_here>"
}
```

**Response:** 
```json
{
    "new_token": "eyJ0eXAiOiJKV1QiLCJhbGci..."
}
```





### **Intermediate Level**

---

#### **Program 9: Role-Based Authentication (RBAC)**

* **Objective:** Implement Role-Based Authentication for different types of users (admin, user).

* **Python Code:**

  ```python
  from flask import Flask, request, jsonify
  import jwt
  from functools import wraps
  from datetime import datetime, timedelta

  app = Flask(__name__)
  app.config['SECRET_KEY'] = 'super_secret_key'

  def token_required(f):
      @wraps(f)
      def decorated(*args, **kwargs):
          token = request.headers.get('Authorization')
          if not token:
              return jsonify({'message': 'Token is missing!'}), 403
          try:
              data = jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])
          except:
              return jsonify({'message': 'Token is invalid!'}), 403
          return f(*args, **kwargs, data=data)
      return decorated

  @app.route('/admin', methods=['GET'])
  @token_required
  def admin(data):
      if data['role'] != 'admin':
          return jsonify({'message': 'Admin access required!'}), 403
      return jsonify({"message": "Welcome, Admin!"}), 200

  @app.route('/user', methods=['GET'])
  @token_required
  def user(data):
      return jsonify({"message": f"Hello, {data['username']}!"}), 200

  @app.route('/login', methods=['POST'])
  def login():
      auth = request.get_json()
      if auth and auth['username'] == 'admin' and auth['password'] == 'adminpass':
          token = jwt.encode({'username': 'admin', 'role': 'admin', 'exp': datetime.utcnow() + timedelta(hours=1)}, app.config['SECRET_KEY'], algorithm='HS256')
          return jsonify({'token': token}), 200
      elif auth and auth['username'] == 'user' and auth['password'] == 'userpass':
          token = jwt.encode({'username': 'user', 'role': 'user', 'exp': datetime.utcnow() + timedelta(hours=1)}, app.config['SECRET_KEY'], algorithm='HS256')
          return jsonify({'token': token}), 200
      return jsonify({'message': 'Unauthorized'}), 401

  if __name__ == '__main__':
      app.run(debug=True)
  ```

* **Explanation:**

  * **`token_required` decorator:** This ensures that any protected route verifies the JWT sent in the `Authorization` header.
  * **Roles (admin/user):** We verify the role in the decoded JWT and enforce access control by checking the role in the `/admin` route.
  * **Login:** We simulate a login where the credentials are checked. If valid, a JWT is generated containing a `role` claim, which determines access.

* **Testing with Postman:**

  1. **Login as admin/user:**

     * Use **POST** to `/login` with JSON payload:

       ```json
       {
         "username": "admin",
         "password": "adminpass"
       }
       ```
     * You will get a token in the response.
  2. **Access protected admin route:**

     * In Postman, choose **GET** for `/admin`.
     * In the **Authorization** tab, choose **Bearer Token**, and paste the token you got from the `/login` route.
     * You should get a 200 response with "Welcome, Admin!" if the role is valid.
  3. **Access protected user route:**

     * Similar to the admin route, use a user token and check if access is granted.
  4. **Test invalid token:**

     * Use a manipulated or expired token and verify the 403 Unauthorized message.

---

#### **Program 10: Proper `SECRET_KEY` Configuration**

* **Objective:** Securely configure Flask’s `SECRET_KEY` for session signing, JWT encoding, and more.

* **Python Code:**

  ```python
  import os
  from flask import Flask, jsonify
  from werkzeug.security import generate_password_hash, check_password_hash

  app = Flask(__name__)

  # Loading SECRET_KEY securely from environment variable (do not hardcode in production)
  app.config['SECRET_KEY'] = os.environ.get('FLASK_SECRET_KEY', 'default_secret_key')

  @app.route('/secure', methods=['GET'])
  def secure_route():
      return jsonify({"message": "This is a secure route!"})

  if __name__ == '__main__':
      app.run(debug=True)
  ```

* **Explanation:**

  * **Environment Variable Usage:** We load the `SECRET_KEY` from the environment, which is the secure practice for production apps. If not set, it defaults to `'default_secret_key'`, but for security purposes, always set this in your deployment environment (for example, in `.env` or as an environment variable in your server).
  * **Security:** Never hardcode the secret key in production. Always use environment variables or a secure vault service to inject it at runtime. You can also use `python-dotenv` to load `.env` variables easily.

* **Setting Environment Variable (Linux/macOS):**

  ```bash
  export FLASK_SECRET_KEY="your_super_secret_key"
  ```

* **Testing:**

  1. In your terminal, run the Flask app.
  2. Make sure the secret is set in the environment and that you can access the `/secure` route.
  3. This route simply returns a secure message to verify the configuration.

---

#### **Program 11: Implementing Secure JWT Authentication (using Flask-Login)**

* **Objective:** Properly implement JWT authentication for secure routes using Flask-Login for session management.

* **Python Code:**

  ```python
  from flask import Flask, request, jsonify
  import jwt
  from datetime import datetime, timedelta
  from functools import wraps
  from flask_login import LoginManager, UserMixin, login_user, login_required, current_user

  app = Flask(__name__)
  app.config['SECRET_KEY'] = 'your_super_secret_key'

  # Setup Flask-Login
  login_manager = LoginManager()
  login_manager.init_app(app)

  class User(UserMixin):
      def __init__(self, id, username, role):
          self.id = id
          self.username = username
          self.role = role

  users = [
      User(1, 'admin', 'admin'),
      User(2, 'user', 'user')
  ]

  @login_manager.user_loader
  def load_user(user_id):
      return users[int(user_id) - 1] if user_id.isdigit() else None

  def token_required(f):
      @wraps(f)
      def decorated(*args, **kwargs):
          token = request.headers.get('Authorization')
          if not token:
              return jsonify({'message': 'Token is missing!'}), 403
          try:
              data = jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])
          except jwt.ExpiredSignatureError:
              return jsonify({'message': 'Token has expired!'}), 403
          except:
              return jsonify({'message': 'Token is invalid!'}), 403
          return f(*args, **kwargs)
      return decorated

  @app.route('/login', methods=['POST'])
  def login():
      auth = request.get_json()
      if auth and auth['username'] == 'admin' and auth['password'] == 'adminpass':
          token = jwt.encode({'username': 'admin', 'role': 'admin', 'exp': datetime.utcnow() + timedelta(hours=1)}, app.config['SECRET_KEY'], algorithm='HS256')
          return jsonify({'token': token}), 200
      elif auth and auth['username'] == 'user' and auth['password'] == 'userpass':
          token = jwt.encode({'username': 'user', 'role': 'user', 'exp': datetime.utcnow() + timedelta(hours=1)}, app.config['SECRET_KEY'], algorithm='HS256')
          return jsonify({'token': token}), 200
      return jsonify({'message': 'Unauthorized'}), 401

  @app.route('/secure', methods=['GET'])
  @token_required
  def secure():
      token = request.headers.get('Authorization')
      try:
          data = jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])
          return jsonify({"message": f"Hello {data['username']}, you have accessed a secure route!"}), 200
      except jwt.ExpiredSignatureError:
          return jsonify({'message': 'Token expired'}), 403
      except:
          return jsonify({'message': 'Invalid token'}), 403

  if __name__ == '__main__':
      app.run(debug=True)
  ```

* **Explanation:**

  * **Flask-Login:** We integrate Flask-Login to manage user sessions. It simplifies user authentication management, tracking users, and accessing the current session.
  * **JWT Authentication:** The `/login` route generates a JWT token for a valid username and password.
  * **Secure Route:** The `/secure` route is protected by Flask-Login. The user must be logged in to access this route. We verify the session with `login_required` and display a personalized message using `current_user`.

* **Testing with Postman:**

  1. **Login as admin/user**: Send **POST** request to `http://127.0.0.1:5000/login` with JSON:

     ```json
     {
       "username": "admin",
       "password": "adminpass"
     }
     ```
  2. **Access Secure Route**: Use **GET** to `/secure` with **Authorization** header containing `Bearer <token>` from the login response.
  3. The response should be `"Hello admin, you have accessed a secure route!"`.

---

### **Advanced Level**

---

#### **Program 12: Admin and User Roles with JWT (Advanced RBAC)**

* **Objective:** Extend role-based authentication for access control.

* **Python Code:**

  ```python
  from flask import Flask, request, jsonify
  import jwt
  from datetime import datetime, timedelta
  from functools import wraps

  app = Flask(__name__)
  app.config['SECRET_KEY'] = 'your_super_secret_key'

  def token_required(f):
      @wraps(f)
      def decorated(*args, **kwargs):
          token = request.headers.get('Authorization')
          if not token:
              return jsonify({'message': 'Token is missing!'}), 403
          try:
              data = jwt.decode(token, app.config['SECRET_KEY'], algorithms=["HS256"])
          except:
              return jsonify({'message': 'Token is invalid!'}), 403
          return f(*args, **kwargs, data=data)
      return decorated

  @app.route('/admin', methods=['GET'])
  @token_required
  def admin(data):
      if data['role'] != 'admin':
          return jsonify({'message': 'Admin access required!'}), 403
      return jsonify({"message": "Welcome, Admin!"}), 200

  @app.route('/user', methods=['GET'])
  @token_required
  def user(data):
      return jsonify({"message": f"Hello, {data['username']}!"}), 200

  @app.route('/login', methods=['POST'])
  def login():
      auth = request.get_json()
      if auth and auth['username'] == 'admin' and auth['password'] == 'adminpass':
          token = jwt.encode({'username': 'admin', 'role': 'admin', 'exp': datetime.utcnow() + timedelta(hours=1)}, app.config['SECRET_KEY'], algorithm='HS256')
          return jsonify({'token': token}), 200
      elif auth and auth['username'] == 'user' and auth['password'] == 'userpass':
          token = jwt.encode({'username': 'user', 'role': 'user', 'exp': datetime.utcnow() + timedelta(hours=1)}, app.config['SECRET_KEY'], algorithm='HS256')
          return jsonify({'token': token}), 200
      return jsonify({'message': 'Unauthorized'}), 401

  if __name__ == '__main__':
      app.run(debug=True)
  ```

* **Explanation:**

  * **Roles:** We enforce role-based access control (RBAC) for `/admin` and `/user` routes. Only users with the role `admin` can access `/admin`, and any valid user can access `/user`.
  * **JWT Token:** We generate JWT tokens for different users based on their role.

* **Testing with Postman:**

  1. **Login and get token**: POST to `/login` with username `admin` or `user`.
  2. **Access `/admin` route**: Send GET to `/admin` with the **Authorization** header containing the token. Admin access should return "Welcome, Admin!", while non-admin tokens should return 403.
  3. **Access `/user` route**: Any valid token should give access to the `/user` route.

---

#### **Program 13: Flask Blueprints for Modular API**

* **Objective:** Organize Flask routes into modular sections using **Blueprints**.

* **Python Code:**

  ```python
  from flask import Flask, Blueprint, jsonify

  app = Flask(__name__)

  # Create a blueprint for user-related routes
  user_bp = Blueprint('user', __name__, url_prefix='/user')

  @user_bp.route('/')
  def user_home():
      return jsonify({"message": "User Home"})

  @user_bp.route('/profile')
  def user_profile():
      return jsonify({"message": "User Profile"})

  app.register_blueprint(user_bp)

  if __name__ == '__main__':
      app.run(debug=True)
  ```

* **Explanation:**

  * **Blueprints:** We define a `user_bp` Blueprint to group all user-related routes (`/user` and `/user/profile`).
  * **Register Blueprints:** We register the blueprint with the Flask app using `app.register_blueprint(user_bp)`.

* **Testing with Postman:**

  1. **Access the `/user` route**: Send a **GET** request to `http://127.0.0.1:5000/user`.
  2. **Access `/user/profile` route**: Send a **GET** request to `http://127.0.0.1:5000/user/profile`.



