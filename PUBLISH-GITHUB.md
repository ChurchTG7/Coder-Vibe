# GitHub Publication Guide

Follow these steps to publish the Coder Unraid Application to GitHub and Unraid Community Applications.

## Step 1: Create GitHub Repository

### Option A: Command Line
```bash
cd C:\Users\btspo\Documents\DockerCoderWorkspace
git init
git add .
git commit -m "Initial commit: Coder Unraid Application v1.0"
git remote add origin https://github.com/YOUR_USERNAME/coder-unraid-app.git
git branch -M main
git push -u origin main
```

### Option B: Web UI
1. Go to https://github.com/new
2. Repository name: `coder-unraid-app`
3. Description: `Unraid application template for Coder VSCode Cloud development environment`
4. Choose: Public (for community access)
5. Initialize with: Add .gitignore (already included)
6. Create repository

## Step 2: Push Files to GitHub

After creating the repository:

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/coder-unraid-app.git
cd coder-unraid-app

# Copy files from DockerCoderWorkspace
# Then commit and push:
git add .
git commit -m "Add Coder Unraid application template v1.0"
git push origin main
```

## Step 3: Submit to Unraid Community Applications

### File Hosting
The template needs to be accessible via a raw URL:
- GitHub raw URL: `https://raw.githubusercontent.com/YOUR_USERNAME/coder-unraid-app/main/coder.xml`

### Submission Process

1. **Fork Community Applications Repository:**
   - Go to: https://github.com/Unraid/Community-Applications-Submitters
   - Click "Fork"
   - This creates a copy in your account

2. **Add Your Application:**
   - Clone your forked repository
   - Edit the submission database (instructions in the repo)
   - Add Coder entry with:
     - Name: "Coder"
     - Repository URL: `https://raw.githubusercontent.com/YOUR_USERNAME/coder-unraid-app/main/coder.xml`
     - Description: "Cloud-based development environment with VS Code"
     - Icon: Include icon URL or path
     - Category: "Development"

3. **Submit Pull Request:**
   - Commit your changes
   - Push to your fork
   - Create Pull Request to Unraid/Community-Applications-Submitters
   - Include details about the application

4. **Wait for Review:**
   - Unraid maintainers review submissions
   - May request modifications
   - Once approved, appears in Community Applications

## Step 4: Create Support Forum Thread

### Forum Setup
1. Go to: https://forums.unraid.net/
2. Navigate to: "Community Applications" forum
3. Create new thread with:

**Thread Title:** `[APP] Coder - VSCode Cloud Development Environment`

**Thread Content:**
```
Coder is a cloud-based development environment platform for Unraid.

## Overview
Deploy Coder to provide VS Code (and other IDEs) as web-accessible development 
environments on your Unraid server. Perfect for team development or remote coding.

## Key Features
- VS Code in the browser
- Self-hosted on your Unraid server
- Multiple concurrent workspaces
- Web terminal access
- HTTPS ready with reverse proxy

## Quick Start
1. Docker → Add Container
2. Search for "Coder" in Community Applications
3. Click Install
4. Access at http://your-unraid-ip:7080

## Documentation
- [GitHub Repository](https://github.com/YOUR_USERNAME/coder-unraid-app)
- [README](https://github.com/YOUR_USERNAME/coder-unraid-app/blob/main/README.md)
- [Setup Guide](https://github.com/YOUR_USERNAME/coder-unraid-app/blob/main/SETUP.md)
- [Contributing](https://github.com/YOUR_USERNAME/coder-unraid-app/blob/main/CONTRIBUTING.md)

## Support
Please open issues on GitHub for bugs or feature requests.

## Version
v1.0 - Initial Release
```

## Step 5: Optional - Create GitHub Release

Create a release for version 1.0:

```bash
git tag -a v1.0 -m "Coder Unraid Application v1.0"
git push origin v1.0
```

Then create release on GitHub:
1. Go to: https://github.com/YOUR_USERNAME/coder-unraid-app/releases
2. Click "Create a new release"
3. Tag: v1.0
4. Title: "Coder Unraid Application v1.0"
5. Description: Copy from README.md
6. Publish release

## Step 6: Update README.md (Optional)

Add GitHub badge to README.md:

```markdown
[![GitHub Release](https://img.shields.io/github/v/release/YOUR_USERNAME/coder-unraid-app)](https://github.com/YOUR_USERNAME/coder-unraid-app/releases)
[![GitHub License](https://img.shields.io/github/license/YOUR_USERNAME/coder-unraid-app)](LICENSE)
```

## Checklist Before Publishing

- [x] All files created and tested
- [x] XML template validated
- [x] Documentation complete
- [x] ENV.md complete
- [x] SETUP.md complete
- [x] TESTING.md complete
- [x] CONTRIBUTING.md complete
- [x] ROADMAP.md complete
- [ ] GitHub repository created
- [ ] Files pushed to GitHub
- [ ] Community Applications PR submitted
- [ ] Forum thread created
- [ ] Release tagged (optional)

## Quick Links

- **Unraid Community Applications:** https://github.com/Unraid/Community-Applications-Submitters
- **Unraid Forums:** https://forums.unraid.net/
- **GitHub:** https://github.com/
- **Coder Official:** https://coder.com
- **Coder Documentation:** https://coder.com/docs

## Maintenance After Publishing

### Regular Updates
1. Monitor Coder releases: https://github.com/coder/coder/releases
2. Update image version in `coder.xml` when new versions available
3. Test with new Unraid releases
4. Update documentation as needed
5. Tag releases on GitHub

### Community Support
1. Monitor GitHub issues
2. Respond to forum questions
3. Accept pull requests for improvements
4. Update ROADMAP.md with progress

## Tips for Success

- **Keep Documentation Updated:** As Coder or Unraid updates, keep docs current
- **Monitor Issues:** Respond quickly to reported problems
- **Community First:** Accept contributions and feedback positively
- **Version Management:** Follow semantic versioning (v1.0, v1.1, v2.0)
- **Changelog:** Maintain CHANGELOG.md for version history

---

**You're all set to publish!** 🚀

Follow the steps above to share Coder with the Unraid community.
