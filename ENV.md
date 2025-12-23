# Coder Environment Variables Documentation

## Core Configuration

### CODER_ADDRESS
- **Type:** string
- **Default:** `0.0.0.0:7080`
- **Description:** Address (host:port) Coder binds to for HTTP connections
- **Example:** `0.0.0.0:7080`

### CODER_POSTGRESQL_URL
- **Type:** string
- **Default:** `file:///var/lib/coder/coder.db` (SQLite)
- **Description:** PostgreSQL connection URL for database. Uses SQLite by default for simpler deployment.
- **SQLite Example:** `file:///var/lib/coder/coder.db`
- **PostgreSQL Example:** `postgres://user:password@host:5432/coder?sslmode=disable`

## Security Configuration

### CODER_TLS_ENABLE
- **Type:** boolean
- **Default:** `false`
- **Description:** Enable TLS/HTTPS. Recommended to use with a reverse proxy (Nginx Proxy Manager) instead.

### CODER_SECURE_AUTH_COOKIE
- **Type:** boolean
- **Default:** `false`
- **Description:** Set secure flag on auth cookies. Enable when using HTTPS through reverse proxy.
- **Note:** Set to `true` when using with reverse proxy for HTTPS

### CODER_TLS_CERTFILE
- **Type:** string
- **Description:** Path to TLS certificate file (if CODER_TLS_ENABLE=true)

### CODER_TLS_KEYFILE
- **Type:** string
- **Description:** Path to TLS key file (if CODER_TLS_ENABLE=true)

## Provisioner Configuration

### CODER_PROVISIONER_DAEMONS
- **Type:** integer
- **Default:** `1`
- **Description:** Number of provisioner daemon processes. Increase for better concurrency with multiple workspaces.

## Feature Flags

### CODER_ALLOW_PATH_APP_SHARING
- **Type:** boolean
- **Default:** `true`
- **Description:** Allow sharing individual apps with path-based routing (e.g., `coder.example.com/app/myapp`)

### CODER_ALLOW_DEV_URLS
- **Type:** boolean
- **Default:** `true`
- **Description:** Allow dev URLs for localhost development access within workspaces

### CODER_DISABLE_SESSION_EXPIRY
- **Type:** boolean
- **Default:** `false`
- **Description:** Disable session expiration (sessions expire after 24 hours by default)

## Optional Advanced Configuration

### CODER_ALLOW_WORKSPACE_RENAMES
- **Type:** boolean
- **Default:** `true`
- **Description:** Allow users to rename their workspaces

### CODER_MAX_TOKEN_LIFETIME
- **Type:** duration
- **Default:** `8760h` (1 year)
- **Description:** Maximum lifetime for API tokens

### CODER_DISABLE_PASSWORD_AUTH
- **Type:** boolean
- **Default:** `false`
- **Description:** Disable password authentication (force OAuth/external auth only)

### CODER_OIDC_CLIENT_ID
- **Type:** string
- **Description:** OpenID Connect client ID (for external authentication)

### CODER_OIDC_CLIENT_SECRET
- **Type:** string
- **Description:** OpenID Connect client secret (for external authentication)

## Notes for Unraid Deployment

- **SQLite Database:** Sufficient for single Unraid instance deployments. No additional container needed.
- **Reverse Proxy:** For HTTPS, use Unraid's Nginx Proxy Manager instead of enabling TLS in Coder.
- **Storage:** Ensure `/mnt/user/appdata/coder` has sufficient space for workspace configurations and data.
- **Memory:** Allocate at least 2GB RAM for smooth operation.
- **CPU:** 2+ CPU cores recommended for multiple concurrent users.
