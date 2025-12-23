# Coder VSCode Cloud - Unraid Application

Deploy Coder, a cloud-based development environment platform, on your Unraid server. Run VS Code, JetBrains IDEs, and other development tools directly in your browser with persistent workspaces.

## Overview

**Coder** is an open-source platform for provisioning self-hosted cloud development environments. With Coder on Unraid, you can:

- ✅ **Code Anywhere:** Access full VS Code experience from any browser
- ✅ **Consistent Environments:** Reproducible development environments for all team members
- ✅ **Self-Hosted:** Complete control—data stays on your Unraid server
- ✅ **Multiple IDEs:** Support for VS Code, JetBrains IDEs, Jupyter notebooks, and more
- ✅ **Docker Integration:** Workspaces are Docker containers, leveraging Unraid's native Docker support
- ✅ **Team Collaboration:** Manage multiple developers and workspaces

## Features

- **VS Code in Browser:** Full Visual Studio Code experience without installation
- **Web Terminal Access:** SSH or web-based terminal within each workspace
- **Workspace Sharing:** Share individual apps with others via path-based routing
- **Dev URLs:** Localhost forwarding for testing web apps
- **SQLite Database:** Simple deployment (no external database needed)
- **HTTPS Ready:** Works with reverse proxy for secure access

## Quick Start

### Via Unraid Community Applications
1. Go to **Docker** → **Add Container**
2. Search for **Coder** in Community Applications
3. Configure ports and volumes as prompted
4. Start container
5. Access at `http://your-unraid-ip:7080`

### Manual Installation
1. Use the provided `coder.xml` template in Unraid's Docker interface
2. See [SETUP.md](SETUP.md) for detailed configuration steps

## Configuration

### Environment Variables
- `CODER_ADDRESS`: Bind address (default: `0.0.0.0:7080`)
- `CODER_POSTGRESQL_URL`: Database URL (default: SQLite)
- `CODER_TLS_ENABLE`: Enable TLS (use reverse proxy instead)
- `CODER_SECURE_AUTH_COOKIE`: Secure cookies (enable with HTTPS)

See [ENV.md](ENV.md) for complete environment variable documentation.

### Volumes
- `/home/coder` - Configuration and user settings
- `/var/lib/coder` - Database and workspace data

### Ports
- `7080` - Web UI (HTTP)

## System Requirements

| Requirement | Minimum | Recommended |
|------------|---------|-------------|
| Unraid | 6.4.0+ | Latest |
| RAM | 2GB | 4GB+ |
| CPU | 2 cores | 4+ cores |
| Disk Space | 5GB | 20GB+ |
| Network | Gigabit | Gigabit |

## Docker Compose

A `docker-compose.yml` file is included for local testing or standalone Docker deployments:

```bash
docker-compose up -d
```

## Deployment Options

### HTTP (Local Network)
```
http://192.168.1.100:7080
```

### HTTPS with Reverse Proxy (Recommended)
Use Unraid's **Nginx Proxy Manager** to provide HTTPS:
1. Create proxy host pointing to `coder:7080`
2. Enable SSL certificate (Let's Encrypt)
3. Set `CODER_SECURE_AUTH_COOKIE=true`

## Usage

### Creating Your First Workspace
1. Log in to Coder (`http://your-unraid-ip:7080`)
2. Click **Create workspace**
3. Select template (default or custom)
4. Wait for workspace provisioning
5. Click **VS Code** or **Terminal** to access

### Accessing Workspaces
- **Browser:** `http://your-unraid-ip:7080` → Select workspace → IDE
- **SSH:** Use connection details provided in workspace settings
- **VS Code Desktop:** Install Coder extension and remote-connect

## Specifications

- **Image:** `ghcr.io/coder/coder:v2.27.9-amd64`
- **Database:** SQLite (default) or PostgreSQL
- **Container Port:** 7080
- **Restart Policy:** Unless stopped
- **Network:** Bridge

## Database Options

### SQLite (Default - Recommended for Unraid)
- **Pros:** Simple, no extra container, suitable for single instance
- **Cons:** Limited concurrency
- **URL:** `file:///var/lib/coder/coder.db`

### PostgreSQL (Advanced)
- **Pros:** Better concurrency, suitable for teams
- **Cons:** Requires separate container or database
- **URL:** `postgres://user:password@host:5432/coder?sslmode=disable`

## Troubleshooting

### Container won't start
- Check Unraid Docker logs
- Ensure `/mnt/user/appdata/coder` is writable
- Verify sufficient disk space

### Can't access web interface
- Confirm container running: Status should show "Running"
- Check port binding: Should see port `7080`
- Verify firewall allows port 7080

### Workspace creation fails
- Check available disk space
- Monitor Docker container logs
- Increase `CODER_PROVISIONER_DAEMONS` if concurrent creations fail

See [SETUP.md](SETUP.md) for detailed troubleshooting guide.

## Upgrading

1. Stop container
2. Pull new image tag
3. Restart container
4. Data persists in volumes automatically

## Support

- **Official Docs:** https://coder.com/docs
- **GitHub Issues:** https://github.com/coder/coder/issues
- **Discussions:** https://github.com/coder/coder/discussions
- **Community:** https://forums.unraid.net/

## License

Coder is licensed under the AGPL-3.0 License. See https://github.com/coder/coder/blob/main/LICENSE for details.

## Project Links

- **Coder Website:** https://coder.com
- **GitHub Repository:** https://github.com/coder/coder
- **Docker Image:** https://ghcr.io/coder/coder
- **Documentation:** https://coder.com/docs

## Files Included

- `coder.xml` - Unraid Docker template
- `docker-compose.yml` - Docker Compose configuration
- `ENV.md` - Complete environment variables documentation
- `SETUP.md` - Detailed setup and configuration guide
- `README.md` - This file

## Installation via Unraid Community Applications

Once this template is submitted to Community Applications:

1. **Docker** → **Add Container**
2. Select **Community Applications**
3. Search for **Coder**
4. Click **Install**
5. Configure as needed
6. Start container

## Contributing

To contribute improvements, report issues, or suggest features:
- Fork this repository
- Make your changes
- Submit a pull request with detailed description

---

**Happy Coding!** 🚀

Deploy Coder on your Unraid server and enjoy cloud development environments with full control over your infrastructure.
