# Testing Guide for Coder Unraid Application

## Pre-Deployment Testing

### 1. XML Template Validation

Validate the XML syntax:

```bash
xmllint --noout coder.xml
```

Expected output: `coder.xml validates`

### 2. Docker Image Testing

Pull and test the image locally:

```bash
docker pull ghcr.io/coder/coder:v2.27.9-amd64
docker run --rm ghcr.io/coder/coder:v2.27.9-amd64 version
```

Expected: Shows Coder version information

### 3. Docker Compose Testing

Test the Docker Compose configuration:

```bash
docker-compose config
```

Expected: Shows valid YAML configuration without errors

Start the stack:

```bash
docker-compose up -d
```

Verify container running:

```bash
docker-compose ps
```

Expected: `coder` container status shows `Up`

Check health:

```bash
docker-compose logs coder
```

Expected: No critical errors, should show startup messages

## On Unraid Testing

### 1. Container Creation

- [ ] Add container via Unraid Docker interface
- [ ] Verify all port mappings correct (7080 → 7080)
- [ ] Confirm volume mounts exist and are writable
- [ ] Environment variables properly set
- [ ] Start container successfully

### 2. Container Operation

- [ ] Container appears in Docker tab with "Running" status
- [ ] Check container logs for errors
- [ ] Verify ports bound correctly: `netstat -an | grep 7080`
- [ ] Confirm volumes mounted: Check `/mnt/user/appdata/coder/` directory

### 3. Web Interface Access

- [ ] Access `http://<unraid-ip>:7080` from browser
- [ ] Login page displays correctly
- [ ] Create first user account (becomes admin)
- [ ] User account creation successful

### 4. Workspace Creation

- [ ] Create new workspace via web UI
- [ ] Select template successfully
- [ ] Workspace provisioning completes
- [ ] Workspace appears in list

### 5. IDE Access

- [ ] Open VS Code from workspace
- [ ] VS Code loads completely in browser
- [ ] Code editing works (create test file)
- [ ] Terminal access available
- [ ] Extensions can be installed

### 6. Persistence Testing

- [ ] Stop container via Unraid
- [ ] Verify data in `/mnt/user/appdata/coder/` persists
- [ ] Restart container
- [ ] Verify previous workspace still exists
- [ ] Confirm workspace data intact

### 7. HTTPS/Reverse Proxy Testing (Optional)

If using reverse proxy (Nginx Proxy Manager):

- [ ] Configure Nginx Proxy Manager for Coder
- [ ] Enable SSL certificate (Let's Encrypt)
- [ ] Access via HTTPS domain: `https://coder.yourdomain.com`
- [ ] Set `CODER_SECURE_AUTH_COOKIE=true`
- [ ] Restart container
- [ ] Verify HTTPS access works
- [ ] Confirm no auth cookie warnings

### 8. Resource Monitoring

- [ ] Monitor RAM usage during operation
- [ ] Check CPU usage while creating workspaces
- [ ] Verify disk I/O performance
- [ ] Monitor container restart behavior

## Multi-User Testing

### Workspace Isolation

- [ ] Create multiple user accounts
- [ ] Each user creates own workspace
- [ ] Verify users can't access other workspaces
- [ ] Test workspace permissions

### Concurrent Operations

- [ ] Create multiple workspaces simultaneously
- [ ] Verify all provision successfully
- [ ] Access multiple workspaces in different tabs
- [ ] Test switching between workspaces

## Performance Testing

### Baseline Performance

- [ ] Measure web UI load time: < 5 seconds
- [ ] Measure workspace creation time: < 2 minutes
- [ ] Measure IDE load time: < 3 seconds
- [ ] Monitor CPU/RAM during peak usage

### Load Testing

- [ ] Create 3-5 concurrent workspaces
- [ ] Run CPU/memory intensive operations
- [ ] Monitor for errors or timeouts
- [ ] Check system stability

## Upgrade Testing

### Version Migration

- [ ] Note current Coder version
- [ ] Stop container
- [ ] Remove container (keep volumes)
- [ ] Update image to new version
- [ ] Restart container
- [ ] Verify workspace data migrated
- [ ] Test all features still work

## Regression Testing

### Basic Features

- [ ] Login/logout works
- [ ] Workspace creation/deletion works
- [ ] VS Code access works
- [ ] Terminal access works
- [ ] File editing works
- [ ] Workspace settings accessible
- [ ] Admin panel accessible

### Configuration Changes

- [ ] Modify `CODER_PROVISIONER_DAEMONS`
- [ ] Change session expiry settings
- [ ] Enable/disable features
- [ ] Verify changes take effect

## Known Issues & Edge Cases

### Database Issues

- [ ] SQLite database file creation
- [ ] Database initialization on first start
- [ ] Database compatibility across Unraid versions

### Container Issues

- [ ] Container restart behavior
- [ ] Docker network connectivity
- [ ] Volume mount permissions
- [ ] Disk space constraints

### Browser Compatibility

- [ ] Test in Chrome/Chromium
- [ ] Test in Firefox
- [ ] Test in Safari
- [ ] Test in Edge
- [ ] Test on mobile devices (iPad/tablet)

## Troubleshooting Test Scenarios

### "Port already in use"

- [ ] Verify no other container using 7080
- [ ] Stop conflicting container
- [ ] Restart Coder

### "Permission denied" on volumes

- [ ] Check `/mnt/user/appdata/coder` permissions
- [ ] Verify docker user has write access
- [ ] Correct permissions if needed

### "Database locked" errors

- [ ] Check multiple instances not running
- [ ] Verify database file permissions
- [ ] Restart container to reset

### "Cannot connect to workspace"

- [ ] Verify workspace provisioned successfully
- [ ] Check workspace container is running
- [ ] Verify network connectivity
- [ ] Check firewall rules

## Test Results Reporting

Document test results:

```
Test Date: YYYY-MM-DD
Unraid Version: 6.X.X
Coder Version: v2.27.9
Test Environment: [Hardware specs]
Overall Result: [PASS/FAIL]

Tests Passed: X/X
Tests Failed: X/X

Failed Tests:
- [Test Name]: [Error description]

Notes: [Any additional observations]
```

## Automated Testing

Future testing can include:

- Script to validate XML syntax
- Script to test Docker image availability
- Script to verify port mappings
- Integration tests with Unraid API (if available)
- Performance benchmarking scripts

---

**Testing Schedule:** Run full test suite before each release and major Unraid version updates.
