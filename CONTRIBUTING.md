# Contributing to WhatsApp Automation Plugin

Thank you for your interest in contributing to the WhatsApp Automation plugin for Agent Zero!

## How to Contribute

### Reporting Bugs

Before reporting a bug, please:
1. Search the [existing issues](https://github.com/agent0ai/whatsapp-automation/issues)
2. Verify if the problem has already been reported
3. Include details such as:
   - Plugin version
   - Chrome version
   - Operating system
   - Steps to reproduce the error
   - Complete error messages

### Improvement Suggestions

For new feature suggestions:
1. First search for existing issues
2. Open an issue with the `enhancement` label
3. Describe the use case clearly
4. Explain why it would be useful

### Pull Requests

Pull requests are welcome!

#### Steps for a PR:
1. Fork the repository
2. Create a branch for your change:
   ```bash
   git checkout -b feature/your-improvement
   ```
3. Make your changes with clear commits
4. Ensure scripts are executable:
   ```bash
   chmod +x scripts/*.sh
   ```
5. Verify that plugin.yaml meets the specifications
6. Push to your fork
7. Open a Pull Request

#### Code Standards:
- Bash scripts: use `set -e` for error handling
- Include comments in English
- Follow existing style conventions
- Test your changes before submitting the PR

## Version Releases

Versions follow [Semantic Versioning](https://semver.org/):
- **MAJOR**: backward-incompatible changes
- **MINOR**: compatible new functionalities
- **PATCH**: compatible bug fixes

## License

All contributions will be under the project's MIT license.

## Contact

For questions or discussions:
- Open an issue on GitHub
- Contact the Agent Zero team

---

Thank you for contributing! 🎉
