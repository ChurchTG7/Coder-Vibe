# Contributing to Coder Unraid Application

Thank you for your interest in improving the Coder Unraid Application template!

## How to Contribute

### Reporting Issues
- Check existing issues first to avoid duplicates
- Include Unraid version, Docker version, and specific error messages
- Describe steps to reproduce the issue
- Include relevant logs from Unraid Docker section

### Suggesting Enhancements
- Describe the enhancement and its benefits
- Explain the use case
- Discuss potential implementation approaches

### Submitting Changes
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Test thoroughly on Unraid
5. Commit with clear message: `git commit -m "Add feature: description"`
6. Push to your fork
7. Submit a Pull Request with detailed description

## Testing Checklist

Before submitting a PR, ensure:
- [ ] XML template is valid and proper formatting
- [ ] Docker Compose file works: `docker-compose up -d`
- [ ] All environment variables are documented
- [ ] Configuration tested on Unraid system
- [ ] Setup guide steps verified
- [ ] README is clear and accurate
- [ ] No hardcoded credentials or sensitive data
- [ ] Compatible with stated Unraid version (6.4.0+)

## Code Guidelines

- Use clear, descriptive names for variables and sections
- Add comments for complex configurations
- Keep XML properly formatted and indented
- Document new environment variables in ENV.md
- Update README.md if adding features

## Documentation Standards

- Keep setup instructions clear and step-by-step
- Include troubleshooting for common issues
- Link to official Coder documentation
- Specify Unraid version requirements
- Document system requirements clearly

## Questions?

- Open a GitHub Discussion
- Ask in Unraid Forums (coder tag)
- Reference official Coder documentation

---

We appreciate all contributions to make this Unraid Application better!
