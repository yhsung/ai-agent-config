# Code Review Prompt

You are conducting a thorough code review. Follow this systematic approach:

## 1. Initial Assessment
- Understand the purpose and scope of the changes
- Identify the files modified and their relationships
- Review the associated issue/ticket if referenced

## 2. Functionality Review
- [ ] Does the code accomplish its intended purpose?
- [ ] Are edge cases handled appropriately?
- [ ] Is error handling comprehensive and meaningful?
- [ ] Are there any logical flaws or bugs?

## 3. Code Quality
- [ ] Is the code readable and self-documenting?
- [ ] Are variable and function names clear and descriptive?
- [ ] Is the code properly structured and organized?
- [ ] Are functions/methods focused and single-purpose?
- [ ] Is nesting kept to reasonable levels (max 3)?

## 4. Language-Specific Standards

### Python
- [ ] Follows PEP 8 style guidelines
- [ ] Uses type hints appropriately
- [ ] Implements proper exception handling
- [ ] Uses context managers for resources
- [ ] Docstrings are complete and accurate

### Go
- [ ] Follows Go style guide (gofmt compliant)
- [ ] Error handling is comprehensive (all errors checked)
- [ ] Uses interfaces appropriately
- [ ] Exported items are documented
- [ ] Context usage is proper for cancellation/timeouts

### Rust
- [ ] Follows Rust API guidelines (rustfmt compliant)
- [ ] Ownership and borrowing are used correctly
- [ ] Error handling uses Result/Option appropriately
- [ ] No unnecessary clones or allocations
- [ ] Unsafe code is justified and documented

## 5. Testing
- [ ] Are there tests for new functionality?
- [ ] Do tests cover edge cases and error conditions?
- [ ] Are test names descriptive and meaningful?
- [ ] Is test coverage adequate (>80% for critical paths)?
- [ ] Are tests isolated and don't depend on external state?

## 6. Security
- [ ] No hardcoded secrets or credentials
- [ ] Input validation is performed
- [ ] SQL injection prevention (parameterized queries)
- [ ] Authentication/authorization properly implemented
- [ ] Sensitive data is handled securely

## 7. Performance
- [ ] No obvious performance bottlenecks
- [ ] Database queries are efficient
- [ ] Resource usage is reasonable
- [ ] Algorithms have appropriate time/space complexity
- [ ] Caching is used where beneficial

## 8. Documentation
- [ ] Complex logic is documented
- [ ] API changes are documented
- [ ] README updated if necessary
- [ ] Comments explain "why" not "what"
- [ ] Breaking changes are clearly noted

## 9. Dependencies
- [ ] New dependencies are justified and necessary
- [ ] Dependencies are up-to-date and maintained
- [ ] No known security vulnerabilities
- [ ] License compatibility verified

## 10. Output Format

Provide feedback in this structure:

### Summary
[Brief overview of the changes and overall assessment]

### Strengths
- [What the code does well]
- [Good practices observed]

### Issues Found

#### Critical (Must Fix)
- **[File:Line]** [Description of issue]
  - Impact: [Why this is critical]
  - Suggestion: [How to fix]

#### Important (Should Fix)
- **[File:Line]** [Description of issue]
  - Suggestion: [How to improve]

#### Minor (Nice to Have)
- **[File:Line]** [Description of issue]
  - Suggestion: [Optional improvement]

### Recommendations
- [General suggestions for improvement]
- [Best practices to consider]

### Approval Status
- [ ] Approved - Ready to merge
- [ ] Approved with minor comments
- [ ] Changes requested - Must address critical issues
- [ ] Needs discussion - Architectural concerns
