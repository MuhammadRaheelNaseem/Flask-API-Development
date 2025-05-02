### **Basic Level**

#### **Program 1: Setting up Flask and Basic API Route**

```python
import requests

url = 'http://127.0.0.1:5000/hello'

response = requests.get(url)
print(response.json())  # Output: {"message": "Hello, World!"}
```

#### **Program 2: Handling POST Requests and JSON Payload**

```python
import requests
import json

url = 'http://127.0.0.1:5000/data'
data = {'name': 'Alice', 'age': 25}

response = requests.post(url, json=data)
print(response.json())  # Output: {"received": {"name": "Alice", "age": 25}}
```

#### **Program 3: Using Query Parameters**

```python
import requests

url = 'http://127.0.0.1:5000/greet'
params = {'name': 'John'}

response = requests.get(url, params=params)
print(response.json())  # Output: {"message": "Hello, John!"}
```

#### **Program 4: Handling Responses and Status Codes**

```python
import requests

url = 'http://127.0.0.1:5000/error'

response = requests.get(url)
print(response.status_code)  # Output: 404
print(response.json())  # Output: {"error": "Resource not found"}
```

#### **Program 5: Basic Authentication**

```python
import requests
from requests.auth import HTTPBasicAuth

url = 'http://127.0.0.1:5000/secure'

# Sending the 'admin' credentials for authentication
response = requests.get(url, auth=HTTPBasicAuth('admin', 'password'))
print(response.json())  # Output: {"message": "This is a secure endpoint"}
```

#### **Program 6: Working with MySQL Database**

```python
import requests

url = 'http://127.0.0.1:5000/users'

response = requests.get(url)
print(response.json())  # Output: User data from MySQL
```

#### **Program 7: Token-based Authentication (JWT)**

```python
import requests

# Login to get the JWT token
login_url = 'http://127.0.0.1:5000/login'
login_data = {'username': 'admin', 'password': 'password'}
login_response = requests.post(login_url, json=login_data)
token = login_response.json()['token']

# Access protected route using the JWT token
protected_url = 'http://127.0.0.1:5000/protected'
headers = {'Authorization': f'Bearer {token}'}

response = requests.get(protected_url, headers=headers)
print(response.json())  # Output: {"message": "This is a protected endpoint"}
```

### **Intermediate Level**

#### **Program 8: Protecting Routes with JWT**

```python
import requests

# Login to get the JWT token
login_url = 'http://127.0.0.1:5000/login'
login_data = {'username': 'admin', 'password': 'password'}
login_response = requests.post(login_url, json=login_data)
token = login_response.json()['token']

# Access protected route using the JWT token
protected_url = 'http://127.0.0.1:5000/protected'
headers = {'Authorization': f'Bearer {token}'}

response = requests.get(protected_url, headers=headers)
print(response.json())  # Output: {"message": "This is a protected endpoint"}
```

---

### **JWT with Python (Testing Token Generation and Validation)**

#### **Login and Get Token**

```python
import requests

login_url = 'http://127.0.0.1:5000/login'
login_data = {'username': 'admin', 'password': 'adminpass'}

response = requests.post(login_url, json=login_data)
token = response.json()['token']
print("JWT Token:", token)
```

#### **Decode Token**

```python
import requests

token = '<paste_the_token_here>'

decode_url = 'http://127.0.0.1:5000/decode'
response = requests.post(decode_url, json={'token': token})
print(response.json())  # Output: {'decoded': {...}}
```

#### **Refresh Token**

```python
import requests

token = '<paste_the_token_here>'

refresh_url = 'http://127.0.0.1:5000/refresh'
response = requests.post(refresh_url, json={'token': token})
print(response.json())  # Output: {'new_token': 'new_jwt_token'}
```

---

### **Advanced Level**

#### **Program 9: Role-Based Authentication (RBAC)**

```python
import requests

# Login to get the JWT token (admin or user)
login_url = 'http://127.0.0.1:5000/login'
login_data = {'username': 'admin', 'password': 'adminpass'}
login_response = requests.post(login_url, json=login_data)
token = login_response.json()['token']

# Access protected admin route using the JWT token
admin_url = 'http://127.0.0.1:5000/admin'
headers = {'Authorization': f'Bearer {token}'}

response = requests.get(admin_url, headers=headers)
print(response.json())  # Output: {"message": "Welcome, Admin!"}
```

#### **Program 10: Proper `SECRET_KEY` Configuration**

```python
import requests

url = 'http://127.0.0.1:5000/secure'

response = requests.get(url)
print(response.json())  # Output: {"message": "This is a secure route!"}
```

#### **Program 11: Implementing Secure JWT Authentication (using Flask-Login)**

```python
import requests

# Login to get the JWT token (admin or user)
login_url = 'http://127.0.0.1:5000/login'
login_data = {'username': 'admin', 'password': 'adminpass'}
login_response = requests.post(login_url, json=login_data)
token = login_response.json()['token']

# Access secure route using the JWT token
secure_url = 'http://127.0.0.1:5000/secure'
headers = {'Authorization': f'Bearer {token}'}

response = requests.get(secure_url, headers=headers)
print(response.json())  # Output: {"message": "Hello admin, you have accessed a secure route!"}
```

#### **Program 12: Admin and User Roles with JWT (Advanced RBAC)**

```python
import requests

# Login to get the JWT token (admin or user)
login_url = 'http://127.0.0.1:5000/login'
login_data = {'username': 'admin', 'password': 'adminpass'}
login_response = requests.post(login_url, json=login_data)
token = login_response.json()['token']

# Access protected admin route using the JWT token
admin_url = 'http://127.0.0.1:5000/admin'
headers = {'Authorization': f'Bearer {token}'}

response = requests.get(admin_url, headers=headers)
print(response.json())  # Output: {"message": "Welcome, Admin!"}

# Access protected user route using the JWT token
user_url = 'http://127.0.0.1:5000/user'
response = requests.get(user_url, headers=headers)
print(response.json())  # Output: {"message": "Hello admin, you have accessed the user route!"}
```

#### **Program 13: Flask Blueprints for Modular API**

```python
import requests

# Access the /user route
user_url = 'http://127.0.0.1:5000/user'
response = requests.get(user_url)
print(response.json())  # Output: {"message": "User Home"}

# Access the /user/profile route
profile_url = 'http://127.0.0.1:5000/user/profile'
response = requests.get(profile_url)
print(response.json())  # Output: {"message": "User Profile"}
```
