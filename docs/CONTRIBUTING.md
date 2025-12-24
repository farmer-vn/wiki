# Contributing to HPC Lab Wiki

Thank you for your interest in contributing to the HPC Lab Wiki! This document provides guidelines for contributing content.

## How to Contribute

### Reporting Issues

If you find errors, outdated information, or have suggestions:

1. Check the [existing issues](https://github.com/farmer-vn/wiki/issues)
2. Create a new issue with:
   - Clear title and description
   - Steps to reproduce (if applicable)
   - Expected vs actual behavior
   - Screenshots (if helpful)

### Suggesting New Content

1. Open an issue describing the proposed content
2. Explain why it would be useful
3. Wait for discussion/approval before starting work

### Making Changes

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/your-feature-name`
3. **Make your changes** following the guidelines below
4. **Test locally**: Run `bundle exec jekyll serve` and review changes
5. **Commit**: Use clear, descriptive commit messages
6. **Push**: Push your branch to your fork
7. **Open a Pull Request**: Describe your changes

## Content Guidelines

### Markdown Style

- Use ATX-style headers (`#` not underlines)
- Include a table of contents for long pages
- Use code fences with language identifiers:
  ````markdown
  ```bash
  your command here
  ```
  ````

### Page Structure

Every page should have front matter:

```yaml
---
layout: default
title: Page Title
nav_order: 2
description: "Brief description"
permalink: /page-url
---
```

### Writing Style

- **Be clear and concise**
- **Use active voice**
- **Provide examples** for complex concepts
- **Link to official docs** for authoritative sources
- **Keep information current** - verify against official documentation
- **Use lists** for sequential steps or multiple items
- **Bold important terms** or warnings

### Code Examples

- Provide working, tested examples
- Include comments for clarity
- Show expected output when relevant
- Use placeholders like `<your_name>` for user-specific values

### File Naming

- Use lowercase with hyphens: `my-new-guide.md`
- Be descriptive but concise
- Avoid spaces and special characters

## Adding New Pages

1. Create a new `.md` file in the repository root
2. Add front matter with appropriate `nav_order`
3. Write content following the style guide
4. Update `index.md` if adding a major section
5. Test navigation works correctly

## Local Development

### Setup

```bash
# Install dependencies
bundle install

# Start development server
bundle exec jekyll serve

# Site will be available at http://localhost:4000/wiki
```

### Before Submitting

- [ ] Test all links work
- [ ] Verify code examples are correct
- [ ] Check spelling and grammar
- [ ] Ensure formatting is consistent
- [ ] Test on local server
- [ ] Verify mobile responsiveness

## Pull Request Process

1. **Update documentation** if you change functionality
2. **Test thoroughly** before submitting
3. **Write a clear PR description**:
   - What changes were made
   - Why they were necessary
   - Any related issues
4. **Respond to feedback** from reviewers
5. **Keep PRs focused** - one feature/fix per PR

## Review Criteria

Pull requests will be reviewed for:

- **Accuracy** - Information must be correct and current
- **Clarity** - Content should be easy to understand
- **Consistency** - Follow existing style and structure
- **Completeness** - Include all necessary information
- **Links** - All links must work correctly
- **Testing** - Changes must be tested locally

## Verification Process

Always verify technical information against:

1. [Official SIGMA2 Documentation](https://documentation.sigma2.no/)
2. Official tool documentation
3. Testing on actual systems when possible

## Questions?

- Open an issue for questions about contributing
- Tag with `question` label
- Be patient while waiting for response

## Code of Conduct

- Be respectful and professional
- Provide constructive feedback
- Welcome newcomers
- Focus on content, not contributors

## License

By contributing, you agree that your contributions will be licensed under the same MIT License that covers the project.

---

Thank you for helping improve the HPC Lab Wiki! 🎉
