# Contributing to Flutter Firebase Template

Thank you for your interest in contributing to this Flutter Firebase template! We appreciate your help in making this template better for everyone.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion for improvement:

1. **Search existing issues** to see if it's already been reported
2. If not, **create a new issue** with:
   - A clear, descriptive title
   - Detailed description of the problem or suggestion
   - Steps to reproduce (for bugs)
   - Expected behavior
   - Actual behavior
   - Screenshots (if applicable)
   - Your environment (Flutter version, OS, device)

### Submitting Changes

1. **Fork the repository**
   ```bash
   # Click the "Fork" button on GitHub
   ```

2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR-USERNAME/flutter-template.git
   cd flutter-template
   ```

3. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

   Branch naming conventions:
   - `feature/` - New features
   - `fix/` - Bug fixes
   - `docs/` - Documentation updates
   - `refactor/` - Code refactoring

4. **Make your changes**
   - Write clean, readable code
   - Follow the existing code style
   - Add comments where necessary
   - Update documentation if needed

5. **Test thoroughly**
   ```bash
   flutter analyze
   flutter test
   flutter run
   ```

   Ensure:
   - No analysis errors or warnings
   - All tests pass
   - The app runs without errors
   - Your changes work as expected

6. **Commit your changes**
   ```bash
   git add .
   git commit -m "Add amazing feature"
   ```

   Commit message guidelines:
   - Use present tense ("Add feature" not "Added feature")
   - Use imperative mood ("Move cursor to..." not "Moves cursor to...")
   - Be clear and concise
   - Reference issues if applicable (#123)

7. **Push to your fork**
   ```bash
   git push origin feature/amazing-feature
   ```

8. **Open a Pull Request**
   - Go to the original repository on GitHub
   - Click "New Pull Request"
   - Select your feature branch
   - Fill in the PR template with:
     - Description of changes
     - Related issue numbers
     - Testing performed
     - Screenshots (if UI changes)

## Contribution Guidelines

### Code Style

- Follow [Dart Style Guide](https://dart.dev/guides/language/effective-dart/style)
- Use `flutter analyze` to check for issues
- Format code with `dart format .`
- Keep code modular and reusable

### Template Requirements

This is a template project, so contributions should:

- **Remain generic** - Don't include project-specific code
- **No hardcoded values** - Use environment variables or configuration
- **No credentials** - Never commit API keys, secrets, or credentials
- **Be well-documented** - Add comments and update docs
- **Be tested** - Ensure changes work across different setups

### What We're Looking For

Great contributions include:

- **Bug fixes** - Fix issues without breaking existing functionality
- **Documentation improvements** - Clarify setup steps, add examples
- **Code quality** - Refactor for better readability and performance
- **New features** - Add useful functionality that benefits all users
- **Test coverage** - Add or improve tests
- **Error handling** - Better error messages and recovery

### What to Avoid

Please don't:

- Add project-specific features that won't benefit other users
- Include personal branding or company names
- Commit environment files (`.env`, `GoogleService-Info.plist`)
- Make breaking changes without discussion
- Add unnecessary dependencies
- Submit incomplete or untested code

## Development Setup

1. **Install Flutter**
   - Follow [Flutter installation guide](https://docs.flutter.dev/get-started/install)
   - Verify: `flutter doctor`

2. **Clone and setup**
   ```bash
   git clone https://github.com/YOUR-USERNAME/flutter-template.git
   cd flutter-template
   flutter pub get
   ```

3. **Create test Firebase project**
   - Set up a Firebase project for testing
   - Don't use production credentials
   - Configure `.env` for local testing

4. **Run tests**
   ```bash
   flutter analyze
   flutter test
   flutter run
   ```

## Pull Request Process

1. **Before submitting**, ensure:
   - [ ] Code follows Dart style guidelines
   - [ ] No analyzer warnings or errors
   - [ ] All tests pass
   - [ ] Documentation updated
   - [ ] No credentials or secrets included
   - [ ] Changes are generic and reusable

2. **PR will be reviewed** for:
   - Code quality and style
   - Functionality and testing
   - Documentation completeness
   - Template appropriateness

3. **After approval**, your PR will be merged

4. **If changes requested**, address them and update the PR

## Code of Conduct

### Our Standards

- Be respectful and inclusive
- Welcome newcomers and help them learn
- Focus on constructive feedback
- Accept criticism gracefully
- Prioritize community wellbeing

### Unacceptable Behavior

- Harassment or discriminatory language
- Personal attacks or trolling
- Publishing others' private information
- Other unprofessional conduct

## Questions?

- Open an issue for questions about contributing
- Reach out before starting major changes
- Ask for help if you're stuck

## Recognition

Contributors will be recognized in:
- GitHub contributors list
- Release notes (for significant contributions)

Thank you for contributing to this Flutter Firebase template!
