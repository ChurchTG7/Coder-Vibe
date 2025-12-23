# Coder Unraid Application Setup Guide

## Prerequisites
- Unraid 6.4.0 or later
- Docker installed and running on Unraid
- Nginx Proxy Manager (optional, for HTTPS access)
- Minimum 2GB RAM available
- Sufficient storage in `/mnt/user/appdata/` for Coder data

## Installation Steps

### Step 1: Add Coder to Unraid

1. Go to **Unraid Dashboard** → **Docker** tab
2. Click **Add Container**
3. Fill in the following:
   - **Name:** `coder`
   - **Repository:** `ghcr.io/coder/coder:v2.27.9-amd64`
   - **Port Mappings:**
     - Host Port: `7080` → Container Port: `7080`
   - **Volume Mappings:**
     - Host Path: `/mnt/user/appdata/coder` → Container Path: `/home/coder`
     - Host Path: `/mnt/user/appdata/coder/data` → Container Path: `/var/lib/coder`

### Step 2: Configure Environment Variables

In the Docker container configuration, add the following environment variables:

```
CODER_ADDRESS=0.0.0.0:7080
CODER_POSTGRESQL_URL=file:///var/lib/coder/coder.db
CODER_TLS_ENABLE=false
CODER_SECURE_AUTH_COOKIE=false
CODER_PROVISIONER_DAEMONS=1
CODER_ALLOW_PATH_APP_SHARING=true
CODER_ALLOW_DEV_URLS=true
CODER_DISABLE_SESSION_EXPIRY=false
```

### Step 3: Apply and Start Container

1. Click **Apply** to save the container configuration
2. Coder will download the image and start automatically
3. Monitor the logs to ensure no errors during startup

### Step 4: Access Coder Web Interface

1. Open your browser and navigate to:
   ```
   http://<YOUR_UNRAID_IP>:7080
   ```
   Replace `<YOUR_UNRAID_IP>` with your Unraid server's IP address

2. You should see the Coder login page
3. Create your first user account (first user becomes admin)

### Step 5: Initial Setup

1. **Login:** Use the credentials you just created
2. **Workspace Creation:** Click "Create workspace" to provision your first development environment
3. **IDE Selection:** Choose VS Code as your IDE
4. **Template Selection:** Select default template or create custom workspace

### Step 6: Configure HTTPS (Optional but Recommended)

If you want HTTPS access instead of HTTP:

#### Option A: Using Nginx Proxy Manager

1. In Unraid, install **Nginx Proxy Manager** from Community Applications
2. Configure a new proxy host:
   - **Domain Name:** `coder.yourdomain.com`
   - **Scheme:** `http`
   - **Forward Hostname:** `coder` (Docker container name)
   - **Forward Port:** `7080`
   - **Enable SSL Certificate:** Yes (use Let's Encrypt)

3. Update Coder environment variables:
   - Set `CODER_SECURE_AUTH_COOKIE=true`

#### Option B: Manual Reverse Proxy

1. Use any reverse proxy (Traefik, Apache, Nginx) configured for HTTPS
2. Proxy to `http://coder:7080` internally
3. Set `CODER_SECURE_AUTH_COOKIE=true` in environment variables

## Accessing Your Coder Workspaces

### VS Code Browser Access
- Navigate to `http://<YOUR_UNRAID_IP>:7080` → Your workspace → **VS Code**
- Full VS Code experience in browser with all extensions

### VS Code Desktop Access
1. Install [Coder VS Code Extension](https://marketplace.visualstudio.com/items?itemName=coder.coder-vscode)
2. Add remote connection to your Coder instance
3. Select workspace to open in desktop VS Code

### Terminal Access
- SSH into workspaces directly using provided connection details
- Or use web terminal within Coder UI

## Common Configuration Changes

### Increase Provisioner Daemons (for multiple concurrent workspaces)
```
CODER_PROVISIONER_DAEMONS=4
```
Restart the container for changes to take effect.

### Use PostgreSQL Instead of SQLite (for production)
```
CODER_POSTGRESQL_URL=postgres://user:password@postgres-host:5432/coder?sslmode=disable
```
Note: Requires separate PostgreSQL container or external database.

### Disable Password Authentication (OIDC only)
```
CODER_DISABLE_PASSWORD_AUTH=true
CODER_OIDC_CLIENT_ID=your-client-id
CODER_OIDC_CLIENT_SECRET=your-client-secret
CODER_OIDC_ISSUER_URL=https://your-oidc-provider.com
```

## Troubleshooting

### Container won't start
- Check Unraid logs: **Logs** → **Docker** tab
- Ensure `/mnt/user/appdata/coder` directory has proper permissions
- Verify sufficient free disk space

### Can't access Coder web interface
- Confirm container is running: **Docker** → check Coder status
- Check firewall: port 7080 should be accessible
- Try direct IP: `http://192.168.x.x:7080` (replace with your Unraid IP)

### Workspace creation fails
- Check available disk space on Unraid
- Increase `CODER_PROVISIONER_DAEMONS` if creating multiple workspaces
- Review container logs for specific error messages

### Database errors
- For SQLite: Ensure `/mnt/user/appdata/coder/data` is writable
- For PostgreSQL: Verify database connection string and database accessibility

## Upgrading Coder

1. Go to **Docker** → **Containers**
2. Stop the Coder container
3. Remove the container (keep volumes)
4. Update the repository to new version tag: `ghcr.io/coder/coder:v2.X.X-amd64`
5. Create new container with same configuration
6. Start the container
7. Your data persists in the volumes

## Performance Tuning

### Memory Allocation
- Minimum: 2GB
- Recommended: 4GB+ for multiple users
- Edit container settings to increase memory limit

### CPU Allocation
- Minimum: 2 cores
- Recommended: 4+ cores for better workspace performance

### Disk I/O
- Place appdata on fast storage (SSD if available)
- Monitor disk usage: Large workspace data can consume significant space

## Support & Documentation

- **Coder Documentation:** https://coder.com/docs
- **Coder GitHub:** https://github.com/coder/coder
- **Unraid Forums:** https://forums.unraid.net/
- **Community Applications:** https://github.com/coder/coder/discussions

## Next Steps

1. Create your first workspace
2. Install preferred development tools and extensions in VS Code
3. Configure additional IDEs if needed (JetBrains, etc.)
4. Set up team members and manage workspaces
5. Customize workspace templates for your use case
