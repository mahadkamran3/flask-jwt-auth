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
