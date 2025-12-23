# 🚀 Quick Reference Card

## Coder Unraid Application v1.0

---

## ⚡ Quick Start

**Access:** `http://your-unraid-ip:7080`  
**Template:** [coder.xml](coder.xml)  
**Database:** SQLite (included)  
**Port:** 7080  

---

## 📋 Essential Files

| File | Purpose |
|------|---------|
| [coder.xml](coder.xml) | Unraid Docker template |
| [docker-compose.yml](docker-compose.yml) | Docker Compose config |
| [README.md](README.md) | Project overview |
| [SETUP.md](SETUP.md) | Setup guide |
| [ENV.md](ENV.md) | Environment variables |

---

## 🔧 Configuration

```xml
Port: 7080
Volume: /mnt/user/appdata/coder
Database: SQLite (file:///var/lib/coder/coder.db)
IDE: VS Code
TLS: Reverse proxy ready
```

---

## 📦 Installation

### Via Community Applications (After Listing)
```
Docker → Add Container → Search "Coder" → Install
```

### Manual
```
Docker → Add Container → coder.xml template → Configure → Start
```

---

## 🔗 Environment Variables

**Essential:**
- `CODER_ADDRESS` = `0.0.0.0:7080`
- `CODER_POSTGRESQL_URL` = `file:///var/lib/coder/coder.db`

**Security:**
- `CODER_TLS_ENABLE` = `false` (use reverse proxy)
- `CODER_SECURE_AUTH_COOKIE` = `false` (enable with HTTPS)

**Features:**
- `CODER_ALLOW_PATH_APP_SHARING` = `true`
- `CODER_ALLOW_DEV_URLS` = `true`

See [ENV.md](ENV.md) for complete list.

---

## 💾 Volumes

```
/home/coder     ← User settings & config
/var/lib/coder  ← Database & data
```

Map to: `/mnt/user/appdata/coder`

---

## 🔒 HTTPS Setup

1. Install **Nginx Proxy Manager** on Unraid
2. Create proxy host:
   - Domain: `coder.yourdomain.com`
   - Target: `coder:7080`
   - SSL: Let's Encrypt
3. Update Coder:
   - `CODER_SECURE_AUTH_COOKIE=true`
4. Restart container

---

## 🧪 Testing

**Docker Compose Test:**
```bash
cd workspace
docker-compose up -d
docker-compose logs coder
```

**Health Check:**
```bash
curl http://localhost:7080/api/v2/buildinfo
```

**Access:**
```
http://localhost:7080
```

---

## 📊 System Requirements

| Item | Minimum | Recommended |
|------|---------|-------------|
| Unraid | 6.4.0 | Latest |
| RAM | 2GB | 4GB+ |
| CPU | 2 cores | 4+ cores |
| Disk | 5GB | 20GB+ |

---

## 🆘 Troubleshooting

**Won't start?**
- Check logs: Docker → Container → Logs
- Verify `/mnt/user/appdata/coder` is writable

**Can't access?**
- Check port 7080 is open
- Verify container running
- Try: `http://192.168.x.x:7080`

**Workspace creation fails?**
- Check disk space
- Review container logs
- Increase `CODER_PROVISIONER_DAEMONS`

See [SETUP.md](SETUP.md) for detailed troubleshooting.

---

## 📚 Documentation

| Document | Content |
|----------|---------|
| [README.md](README.md) | Overview & features |
| [SETUP.md](SETUP.md) | Setup & troubleshooting |
| [ENV.md](ENV.md) | Configuration variables |
| [TESTING.md](TESTING.md) | Testing procedures |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Contribution guide |
| [ROADMAP.md](ROADMAP.md) | Future plans |

---

## 🌐 Publishing

1. **GitHub:** Push files to `coder-unraid-app` repository
2. **Community Apps:** Submit PR to `Unraid/Community-Applications-Submitters`
3. **Forum:** Create thread at `forums.unraid.net`

See [PUBLISH-GITHUB.md](PUBLISH-GITHUB.md) for detailed steps.

---

## 📝 Quick Commands

```bash
# Start container (after adding to Unraid)
# Docker → Container → Start

# View logs
# Docker → Container → Coder → Logs

# Stop container
# Docker → Container → Stop

# Access web UI
http://your-unraid-ip:7080

# SSH into workspace
ssh -i key.pem user@workspace-ip
```

---

## ✅ Checklist

Before deploying:
- [ ] Read [README.md](README.md)
- [ ] Review [SETUP.md](SETUP.md)
- [ ] Prepare `/mnt/user/appdata/coder` directory
- [ ] Allocate 2GB+ RAM
- [ ] Enable port 7080

Before publishing:
- [ ] Create GitHub account
- [ ] Create `coder-unraid-app` repository
- [ ] Push all files
- [ ] Follow [PUBLISH-GITHUB.md](PUBLISH-GITHUB.md)
- [ ] Submit to Community Applications
- [ ] Create forum thread

---

## 🔗 Links

- **Coder Official:** https://coder.com
- **Coder Docs:** https://coder.com/docs
- **GitHub:** https://github.com/coder/coder
- **Unraid Forums:** https://forums.unraid.net
- **Docker Hub:** https://ghcr.io/coder/coder

---

## 📦 Version Info

- **Coder:** v2.27.9-amd64
- **Template:** v1.0
- **Released:** December 2024
- **Status:** ✅ Production Ready

---

## 💡 Tips

1. **For HTTPS:** Use Nginx Proxy Manager (easier than native TLS)
2. **For teams:** Consider PostgreSQL over SQLite (see [ENV.md](ENV.md))
3. **For performance:** Allocate 4GB+ RAM for multiple concurrent users
4. **For backup:** Backup `/mnt/user/appdata/coder` regularly

---

## 🎯 Next Steps

**Option A - Deploy Now:**
1. Read [SETUP.md](SETUP.md)
2. Add container to Unraid
3. Access at http://your-unraid-ip:7080

**Option B - Publish First:**
1. Follow [PUBLISH-GITHUB.md](PUBLISH-GITHUB.md)
2. Submit to Community Applications
3. Users can then install easily

---

**Ready to deploy? Start with [SETUP.md](SETUP.md)!** 🚀

**Ready to publish? Start with [PUBLISH-GITHUB.md](PUBLISH-GITHUB.md)!** 📤
