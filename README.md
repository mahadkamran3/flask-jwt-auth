# Flask JWT Authentication API

A simple token-based authentication system built with Flask, JWT, and SQLite. This project demonstrates how to implement secure user registration, login, and protected routes using JSON Web Tokens (JWT).

---

## 🚀 Features

- User Registration with hashed passwords (bcrypt)
- User Login and JWT Token Generation
- Token-protected routes (via middleware)
- Organized project structure (`app/` folder)
- SQLite for database
- REST API tested using Postman

---

## 🗂️ Project Structure

flask-jwt-auth/
│
├── app/
│ ├── init.py # App factory and DB init
│ ├── models.py # User model
│ ├── routes.py # Auth and protected routes
│ └── utils.py # Token verification decorator
│
├── run.py # Run the Flask server
├── requirements.txt # Python dependencies
├── .gitignore # Ignored files
└── README.md # Project info


---

## 📦 Installation

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd flask-jwt-auth
python -m venv venv
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate
pip install -r requirements.txt
python run.py
```

---

## 🚦 Usage

1. Start the server:
   ```bash
   python run.py
   ```
2. The API will be available at `http://127.0.0.1:5000/`

---

## 🛠️ API Endpoints

### Register a new user
`POST /register`

**Request JSON:**
```json
{
  "username": "your_username",
  "password": "your_password"
}
```

### Login
`POST /login`

**Request JSON:**
```json
{
  "username": "your_username",
  "password": "your_password"
}
```
**Response:**
```json
{
  "token": "<JWT_TOKEN>"
}
```

### Protected Route Example
`GET /protected`

**Headers:**
```
Authorization: Bearer <JWT_TOKEN>
```

---

## 🧪 Testing with Postman

1. Register a user via `POST /register`.
2. Login via `POST /login` to get a JWT token.
3. Access protected routes by adding the token to the `Authorization` header as `Bearer <token>`.

---

## 🔧 Testing with curl

### 1. Register a new user
```bash
curl -X POST http://127.0.0.1:5000/register \
  -H "Content-Type: application/json" \
  -d '{
    "username": "testuser",
    "password": "testpassword123"
  }'
```

**Expected Response:**
```json
{
  "message": "User registered successfully"
}
```

### 2. Login to get JWT token
```bash
curl -X POST http://127.0.0.1:5000/login \
  -H "Content-Type: application/json" \
  -d '{
    "username": "testuser",
    "password": "testpassword123"
  }'
```

**Expected Response:**
```json
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
}
```

### 3. Access protected route with token
```bash
# Replace YOUR_JWT_TOKEN with the actual token from login response
curl -X GET http://127.0.0.1:5000/protected \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

**Expected Response:**
```json
{
  "message": "Access granted to protected route",
  "user": "testuser"
}
```

### 4. Test invalid token (should fail)
```bash
curl -X GET http://127.0.0.1:5000/protected \
  -H "Authorization: Bearer invalid_token_here"
```

**Expected Response:**
```json
{
  "message": "Token is invalid"
}
```

### 5. Test without token (should fail)
```bash
curl -X GET http://127.0.0.1:5000/protected
```

**Expected Response:**
```json
{
  "message": "Token is missing"
}
```

### 💡 curl Tips

**For Windows Command Prompt, use double quotes:**
```cmd
curl -X POST http://127.0.0.1:5000/register ^
  -H "Content-Type: application/json" ^
  -d "{\"username\": \"testuser\", \"password\": \"testpassword123\"}"
```

**For PowerShell, escape quotes or use single quotes:**
```powershell
curl -X POST http://127.0.0.1:5000/register `
  -H "Content-Type: application/json" `
  -d '{"username": "testuser", "password": "testpassword123"}'
```

**Save token to variable (Bash/Linux/macOS):**
```bash
# Get token and save to variable
TOKEN=$(curl -s -X POST http://127.0.0.1:5000/login \
  -H "Content-Type: application/json" \
  -d '{"username": "testuser", "password": "testpassword123"}' \
  | grep -o '"token":"[^"]*"' | cut -d'"' -f4)

# Use the token
curl -X GET http://127.0.0.1:5000/protected \
  -H "Authorization: Bearer $TOKEN"
```

---

## 📝 License

MIT License. See [LICENSE](LICENSE) for details.

---

## 🙏 Credits

- [Flask](https://flask.palletsprojects.com/)
- [PyJWT](https://pyjwt.readthedocs.io/)
- [bcrypt](https://pypi.org/project/bcrypt/)

---

## 📚 Further Reading

- [JWT.io Introduction](https://jwt.io/introduction/)
- [Flask Documentation](https://flask.palletsprojects.com/)
