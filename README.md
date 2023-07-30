# Keycloak OIDC Python Production App
Simple Python app behind Nginx Reverse Proxy with Keycloak OIDC in Docker, orchestrated with Docker-Compose that runs in a production environment.

## Development
Start the environment: run `docker-compose up -d` in the root directory.

### Endpoints
1. http://localhost/: "Hello world!" index page
2. http://localhost/login: redirects to `keycloak` auth
3. http://localhost/auth/callback: `keycloak` callback after login
4. http://localhost/keycloak/admin: `keycloak` admin page
5. http://localhost/keycloak: `keycloak` login page

### Keycloak
Create a new user in the keycloak admin: http://localhost/keycloak/admin
Credentials: `admin:admin` (defined in `docker-compose.yml` and `.env`)
