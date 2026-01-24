# Environment Variable Templates

## .env.local / .env.dev
```ini
NODE_ENV=development
LOG_LEVEL=debug

# Database
DB_USER=app
DB_PASSWORD=app
DB_NAME=app_dev
DB_HOST=localhost
INTERNAL_DB_PORT=5432
EXTERNAL_DB_PORT=5432
DATABASE_URL=postgresql://app:app@localhost:5432/app_dev?schema=public

# API
HOST=0.0.0.0
PORT=3001
INTERNAL_PORT=3001
API_PORT=3001

# Web
WEB_PORT=8080
```

## .env.test
```ini
NODE_ENV=test
LOG_LEVEL=error

# Database (Use a different port to avoid conflict)
DB_USER=app
DB_PASSWORD=app
DB_NAME=app_test
DB_HOST=localhost
INTERNAL_DB_PORT=5432
EXTERNAL_DB_PORT=5433 
DATABASE_URL=postgresql://app:app@localhost:5433/app_test?schema=public

# API
HOST=0.0.0.0
PORT=3001
INTERNAL_PORT=3001
API_PORT=3002

# Web
WEB_PORT=4173
```

## .env.prod.secrets (Do not commit real values)
```ini
# Secrets
DB_PASSWORD=production_password_here
COOKIE_SECRET=long_random_string_here
API_KEY=external_service_key_here
```
