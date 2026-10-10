# Expense Tracker API

FastAPI backend for the Expense Tracker application with JWT authentication.

## Features

- JWT-based authentication with access and refresh tokens
- HttpOnly cookies for secure refresh token storage
- Password hashing with bcrypt
- SQLite database (easily configurable to PostgreSQL)
- CORS configured for frontend integration

## Setup

1. Create virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Create `.env` file from example:
```bash
cp .env.example .env
# Edit .env with your settings
```

4. Run the server:
```bash
uvicorn app.main:app --reload --port 8000
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login (returns access token, sets refresh token cookie)
- `POST /api/auth/refresh` - Refresh access token
- `POST /api/auth/logout` - Logout (clears refresh token cookie)
- `GET /api/auth/me` - Get current user info (protected)

## Development

The API runs on `http://localhost:8000` by default.
API documentation available at `http://localhost:8000/docs` (Swagger UI).

## Environment Variables

See `.env.example` for all configuration options.

## Security Notes

- Access tokens expire in 15 minutes (configurable)
- Refresh tokens expire in 7 days (configurable), stored in HttpOnly cookies
- Passwords hashed with bcrypt (cost factor 12)
- CORS restricted to configured origins
- In production: set `COOKIE_SECURE=true` and use HTTPS