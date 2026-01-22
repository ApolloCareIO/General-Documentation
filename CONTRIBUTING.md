# Contributing to Apollo Care Documentation

Thank you for your interest in contributing to Apollo Care's documentation! This guide will help you get started.

## Table of Contents

- [Ways to Contribute](#ways-to-contribute)
- [Documentation Standards](#documentation-standards)
- [Submission Process](#submission-process)
- [Style Guide](#style-guide)

---

## Ways to Contribute

### Report Issues

Found an error, outdated information, or confusing content? Open an issue:

1. Check existing issues to avoid duplicates
2. Use a clear, descriptive title
3. Describe the problem and its location
4. Suggest a fix if possible

### Suggest Improvements

Have ideas for new documentation or better explanations?

1. Open an issue with the `enhancement` label
2. Describe the improvement
3. Explain why it would benefit readers

### Submit Changes

Ready to contribute directly?

1. Fork the repository
2. Create a feature branch (`git checkout -b docs/improve-tokenomics`)
3. Make your changes
4. Submit a pull request

---

## Documentation Standards

### Accuracy

- All claims must be verifiable
- Technical details must match the codebase
- Financial/actuarial information must be reviewed

### Clarity

- Write for a general audience
- Define technical terms on first use
- Use examples to illustrate concepts

### Consistency

- Follow the established document structure
- Use consistent terminology (see Glossary)
- Match the tone of existing documents

---

## Submission Process

### For Minor Changes

1. Fork the repository
2. Make changes directly on your fork
3. Submit a pull request with a clear description

### For Major Changes

1. Open an issue first to discuss
2. Get feedback from maintainers
3. Fork and create a feature branch
4. Submit a pull request referencing the issue

### Pull Request Requirements

- [ ] Clear description of changes
- [ ] No broken links
- [ ] Consistent formatting
- [ ] Spell-checked content
- [ ] Technical accuracy verified

---

## Style Guide

### Formatting

#### Headings

```markdown
# Document Title (H1) - One per document
## Major Section (H2)
### Subsection (H3)
#### Minor Section (H4)
```

#### Tables

```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data | Data | Data |
```

#### Code Blocks

```markdown
\`\`\`rust
// Use language identifier for syntax highlighting
pub fn example() {}
\`\`\`
```

#### Lists

- Use bullet points for unordered lists
- Use numbered lists for sequential steps
- Keep list items parallel in structure

### Terminology

| Use | Don't Use |
|-----|-----------|
| APH token | $APH, APH coin |
| Premium | Contribution (in Phase 2+) |
| Member | User, customer |
| DAO | The DAO, Apollo DAO |
| Claims | Bills, expenses |

### Tone

- Professional but accessible
- Confident but not arrogant
- Educational, not promotional
- Honest about limitations

### Numbers

- Spell out one through nine
- Use numerals for 10 and above
- Always use numerals with units ($5,000, 90%)
- Use thousands separators (1,000,000 not 1000000)

---

## Document Templates

### New Feature Document

```markdown
# Feature Name

<p align="center">
  <strong>Brief Description</strong><br/>
  <em>Version X.X | Month Year</em>
</p>

---

## Overview

Brief introduction to the feature.

## How It Works

Detailed explanation.

## Technical Details

Implementation specifics.

## FAQ

Common questions.

---

*Document Version: X.X*  
*Last Updated: Month Year*  
*Status: DRAFT/PUBLISHED*
```

---

## Questions?

- Open an issue for documentation questions
- Join community channels for general discussion
- Email support@apollocare.io for sensitive matters

---

Thank you for helping improve Apollo Care documentation!
