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


