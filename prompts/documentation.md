# Documentation Generation Prompt

You are creating comprehensive documentation. Follow these guidelines:

## 1. Documentation Type Selection

Identify what type of documentation is needed:
- [ ] API documentation
- [ ] User guide/tutorial
- [ ] Architecture documentation
- [ ] Code comments/docstrings
- [ ] README file
- [ ] Changelog
- [ ] Contributing guide

## 2. Audience Analysis

Understand your audience:
- **Developers**: Technical details, API references, code examples
- **Users**: How-to guides, tutorials, troubleshooting
- **Contributors**: Setup instructions, architecture, coding standards
- **Stakeholders**: High-level overview, benefits, roadmap

## 3. Documentation Structure

### README Template
```markdown
# Project Name

Brief description (1-2 sentences)

## Features
- Key feature 1
- Key feature 2
- Key feature 3

## Installation

### Prerequisites
- Requirement 1
- Requirement 2

### Setup
[Step-by-step installation instructions]

## Quick Start
[Minimal example to get started]

## Usage
[Common use cases and examples]

## Configuration
[Configuration options and settings]

## Documentation
[Link to full documentation]

## Contributing
[How to contribute]

## License
[License information]
```

### API Documentation Template
```markdown
# API Reference

## Module/Package Name

Brief description of the module's purpose.

### Function/Method Name

Description of what this function does.

**Parameters:**
- `param1` (type): Description
- `param2` (type, optional): Description. Default: value

**Returns:**
- type: Description of return value

**Raises/Errors:**
- ErrorType: When this error occurs

**Example:**
[Code example showing usage]

**Notes:**
[Any important notes or caveats]
```

## 4. Language-Specific Documentation

### Python Docstrings

Use Google or NumPy style:

```python
def function_name(param1: str, param2: int = 0) -> bool:
    """Brief description of function.

    Longer description if needed. Explain the purpose,
    behavior, and any important details.

    Args:
        param1: Description of param1
        param2: Description of param2. Defaults to 0.

    Returns:
        Description of return value

    Raises:
        ValueError: Description of when this is raised
        TypeError: Description of when this is raised

    Example:
        >>> function_name("test", 42)
        True

    Note:
        Any important notes or caveats
    """
    pass
```

### Go Documentation

Follow Go conventions:

```go
// Package packagename provides functionality for X.
//
// This package implements Y and is used for Z.
package packagename

// FunctionName performs X operation.
//
// It takes param1 which represents Y, and returns Z.
// If an error occurs during W, it returns an error.
//
// Example usage:
//   result, err := FunctionName("example")
//   if err != nil {
//       log.Fatal(err)
//   }
func FunctionName(param1 string) (string, error) {
    // Implementation
}
```

### Rust Documentation

Use doc comments:

```rust
/// Brief description of the function.
///
/// Longer description explaining the purpose and behavior.
/// Can span multiple lines.
///
/// # Arguments
///
/// * `param1` - Description of param1
/// * `param2` - Description of param2
///
/// # Returns
///
/// Description of return value
///
/// # Errors
///
/// This function will return an error if:
/// - Condition 1
/// - Condition 2
///
/// # Examples
///
/// ```
/// use crate::module::function_name;
///
/// let result = function_name("test", 42)?;
/// assert_eq!(result, expected);
/// ```
///
/// # Panics
///
/// This function panics if X condition occurs.
///
/// # Safety
///
/// (For unsafe functions) This function is unsafe because...
pub fn function_name(param1: &str, param2: i32) -> Result<String, Error> {
    // Implementation
}
```

## 5. Code Examples Best Practices

Good examples should:
- [ ] Be runnable and tested
- [ ] Show common use cases first
- [ ] Progress from simple to complex
- [ ] Include error handling
- [ ] Use realistic variable names
- [ ] Include expected output
- [ ] Be properly formatted

Example structure:
```language
// Brief comment explaining what this example does
// Setup/context if needed

// The actual example code
result = function_call(params)

// Show the output or result
// Output: expected_result
```

## 6. Architecture Documentation

When documenting architecture:

### System Overview
- High-level diagram showing components
- Brief description of each component
- How components interact

### Component Details
For each major component:
- Purpose and responsibilities
- Key interfaces/APIs
- Dependencies
- Data flow
- Design decisions and rationale

### Diagrams
Use appropriate diagram types:
- Architecture diagrams (component relationships)
- Sequence diagrams (interaction flow)
- Data flow diagrams
- State diagrams (for stateful systems)
- ER diagrams (for data models)

## 7. Tutorial Writing Guidelines

### Structure
1. **Introduction**: What will be built/learned
2. **Prerequisites**: Required knowledge and setup
3. **Steps**: Clear, sequential instructions
4. **Explanation**: Why each step is necessary
5. **Verification**: How to confirm it worked
6. **Next Steps**: Where to go from here

### Best Practices
- [ ] One concept at a time
- [ ] Clear, concise language
- [ ] Visual aids where helpful
- [ ] Working examples at each step
- [ ] Troubleshooting common issues
- [ ] Links to related documentation

## 8. Changelog Format

Follow Keep a Changelog format:

```markdown
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added
- New feature X
- New feature Y

### Changed
- Modified behavior of Z

### Deprecated
- Feature A will be removed in v2.0

### Removed
- Removed deprecated feature B

### Fixed
- Fixed bug in component C
- Resolved issue with D

### Security
- Fixed security vulnerability in E

## [1.0.0] - 2026-01-01

### Added
- Initial release
```

## 9. Contributing Guide Template

```markdown
# Contributing Guide

## Getting Started

### Prerequisites
[List required tools and versions]

### Development Setup
[Step-by-step setup instructions]

## Development Workflow

### Creating a Branch
[Branch naming conventions]

### Making Changes
[Coding standards and guidelines]

### Testing
[How to run tests and add new ones]

### Committing
[Commit message format and conventions]

### Submitting Pull Requests
[PR process and requirements]

## Code Standards
[Link to coding standards or include here]

## Review Process
[What to expect during code review]

## Getting Help
[Where to ask questions]
```

## 10. Documentation Quality Checklist

- [ ] **Accuracy**: Information is correct and up-to-date
- [ ] **Completeness**: All necessary information included
- [ ] **Clarity**: Easy to understand, no jargon without explanation
- [ ] **Consistency**: Terminology and style consistent throughout
- [ ] **Currency**: Reflects current codebase state
- [ ] **Examples**: Working, tested examples provided
- [ ] **Organization**: Logical structure, easy to navigate
- [ ] **Searchability**: Good headings, keywords, and index
- [ ] **Grammar**: No spelling or grammatical errors
- [ ] **Links**: All links work and point to correct resources

## 11. Maintenance Guidelines

### When to Update Documentation
- [ ] New features added
- [ ] API changes made
- [ ] Bugs fixed that affect usage
- [ ] Configuration options changed
- [ ] Dependencies updated
- [ ] Deprecations or removals

### Review Schedule
- Review README quarterly
- Update API docs with each release
- Review tutorials semi-annually
- Update architecture docs when design changes

## 12. Output Format

When generating documentation, provide:

### Proposed Documentation
```markdown
[The actual documentation content]
```

### Documentation Metadata
- **Type**: [API/Tutorial/Guide/etc.]
- **Audience**: [Target audience]
- **Maintenance**: [How often to update]
- **Related Docs**: [Links to related documentation]

### Improvements Made
- [What was added]
- [What was clarified]
- [What was reorganized]

### Recommendations
- [Suggestions for additional documentation]
- [Areas that need more examples]
- [Topics that need clarification]
