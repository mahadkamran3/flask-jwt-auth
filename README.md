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
