# Coder Unraid Application - Project Roadmap

## Version 1.0 - Current Release

### Features Implemented
- ✅ Unraid XML template for Coder v2.27.9-amd64
- ✅ Docker Compose configuration
- ✅ SQLite database support
- ✅ HTTPS-ready with reverse proxy support
- ✅ VS Code IDE provisioning
- ✅ Comprehensive documentation
- ✅ Setup and troubleshooting guides

### Current Specifications
- Image: `ghcr.io/coder/coder:v2.27.9-amd64`
- Database: SQLite (production-ready for single instance)
- TLS: Reverse proxy support (Nginx Proxy Manager)
- IDE: VS Code
- Min Unraid: 6.4.0

## Version 1.1 - Planned Improvements

### Environment Variable Enhancements
- [ ] OIDC/OAuth integration templates
- [ ] Pre-configured OIDC provider examples (Keycloak, Okta, etc.)
- [ ] LDAP integration documentation

### Database Options
- [ ] PostgreSQL integration guide with compose file
- [ ] MySQL support documentation
- [ ] Database backup/restore procedures

### Advanced Features
- [ ] GPU passthrough configuration examples
- [ ] Workspace template examples
- [ ] Custom workspace provisioning scripts
- [ ] Multi-language IDE configuration

## Version 1.2 - Community Features

### User Contributions
- [ ] Accept community workspace templates
- [ ] Community IDE configuration samples
- [ ] Integration examples with other Unraid apps

### Documentation
- [ ] Video setup tutorials
- [ ] Automated backup procedures
- [ ] Performance tuning guide
- [ ] Scaling guide for team deployments

## Version 2.0 - Major Enhancement

### Planned Major Features
- [ ] Support for multiple Coder versions (template variants)
- [ ] One-click HTTPS setup with auto-renewal
- [ ] Integrated backup system
- [ ] Automated health checks and recovery
- [ ] Web-based configuration interface
- [ ] Analytics and usage monitoring

### Platform Support
- [ ] ARM64 image support (Raspberry Pi compatibility)
- [ ] ARM32 image support (if Coder provides it)
- [ ] Multi-architecture template

## Maintenance Timeline

### Regular Updates
- Coder version tracking: Monitor new releases monthly
- Security updates: Apply immediately upon release
- Unraid compatibility: Test with major Unraid releases
- Dependencies: Keep documentation current

### Support Roadmap
- Unraid 6.4.0 - 6.12.x: Actively maintained
- Unraid 7.x: Support when available
- End-of-life Unraid versions: Community support

## Known Limitations

### Current Version (1.0)
- SQLite limited to ~100 concurrent connections (sufficient for small teams)
- No built-in backup system (data persists in volumes)
- TLS requires reverse proxy (not native)
- No auto-scaling (single instance only)

### Planned Solutions
- PostgreSQL option in 1.1 for higher concurrency
- Backup integration in 1.2
- Native TLS option in 2.0
- Kubernetes support in 2.0+

## Community Requests Backlog

Submit feature requests via:
- GitHub Issues: https://github.com/[username]/coder-unraid-app/issues
- Unraid Forums: https://forums.unraid.net/
- Discussions: https://github.com/[username]/coder-unraid-app/discussions

### Example Requests to Consider
- [ ] Network policies and VPN access control
- [ ] Workspace resource limits (CPU/RAM per user)
- [ ] Integration with Unraid VPN plugins
- [ ] Mobile app support improvements
- [ ] Workspace templates marketplace

## Release Schedule

- **v1.0:** Current (December 2024)
- **v1.1:** Q1 2025 (Database, OIDC)
- **v1.2:** Q2 2025 (Community, Documentation)
- **v2.0:** Q4 2025 (Major enhancements)

## Breaking Changes Notice

### Potential Future Breaking Changes
- Database migration path from SQLite → PostgreSQL planned for v1.1
- Configuration format may change for v2.0 (backwards compatible migration provided)
- Volume structure may be reorganized (migration script provided)

## Deprecation Notice

- Support for Unraid < 6.4.0 will be dropped in v2.0
- Coder versions < v2.0 support will be dropped in v2.0

## Contributing to Roadmap

Have ideas for future versions? 
1. Check existing feature requests
2. Create GitHub issue with details
3. Discuss in community forums
4. Submit PR with implementation

---

**Last Updated:** December 2024

For current progress, visit: [Project GitHub Repository]
