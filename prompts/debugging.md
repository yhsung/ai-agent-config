# Debugging Prompt

You are helping debug an issue. Follow this systematic debugging methodology:

## 1. Problem Definition
Start by clearly understanding the problem:
- What is the expected behavior?
- What is the actual behavior?
- When did this issue start occurring?
- Can the issue be reliably reproduced?
- What are the exact steps to reproduce?

## 2. Information Gathering

### Error Analysis
- [ ] Collect full error messages and stack traces
- [ ] Note the exact error type/code
- [ ] Identify the line number and file where error occurs
- [ ] Check if error is consistent or intermittent

### Environment Context
- [ ] Language/runtime version
- [ ] Operating system and version
- [ ] Dependency versions
- [ ] Configuration settings
- [ ] Environment variables

### Recent Changes
- [ ] Recent code changes (git log)
- [ ] Dependency updates
- [ ] Configuration modifications
- [ ] Infrastructure changes

## 3. Hypothesis Formation

Based on the information, form hypotheses:

1. **Primary Hypothesis**: [Most likely cause]
   - Evidence: [Why you think this]
   - Test: [How to verify]

2. **Alternative Hypothesis**: [Second most likely]
   - Evidence: [Why possible]
   - Test: [How to verify]

3. **Edge Case Hypothesis**: [Less likely but possible]
   - Evidence: [Why worth considering]
   - Test: [How to verify]

## 4. Common Issues Checklist

### Python
- [ ] Import errors (missing dependencies, circular imports)
- [ ] Type errors (None values, wrong types)
- [ ] Index/Key errors (off-by-one, missing keys)
- [ ] Encoding issues (UTF-8 vs ASCII)
- [ ] Async/await issues (missing await, event loop)
- [ ] Scope issues (variable shadowing, closure problems)
- [ ] Memory issues (large data structures, leaks)

### Go
- [ ] Nil pointer dereference
- [ ] Goroutine leaks or deadlocks
- [ ] Race conditions (use -race flag)
- [ ] Channel blocking/closing issues
- [ ] Error not checked
- [ ] Interface conversion/assertion failures
- [ ] Slice bounds out of range
- [ ] Map concurrent access without sync

### Rust
- [ ] Borrow checker errors (multiple mutable borrows)
- [ ] Lifetime issues
- [ ] Ownership transfer problems
- [ ] Unwrap/expect on None or Err
- [ ] Type mismatch errors
- [ ] Trait bound not satisfied
- [ ] Async runtime issues (tokio vs async-std)
- [ ] Mutex deadlocks or panics

## 5. Debugging Strategies

### Binary Search Method
1. Identify working state and broken state
2. Find midpoint in changes/code
3. Test if issue exists at midpoint
4. Narrow down to smaller section
5. Repeat until root cause found

### Rubber Duck Method
1. Explain the code line-by-line out loud
2. Question every assumption
3. Verify expected vs actual at each step

### Logging Strategy
Add strategic logging to track:
- Function entry/exit points
- Variable values at key points
- Conditional branch taken
- Loop iterations
- External calls (API, DB, file I/O)

Example logging points:
```python
# Python
import logging
logging.debug(f"Variable state: {var}, Expected: {expected}")
```

```go
// Go
log.Printf("DEBUG: var=%+v, expected=%+v", var, expected)
```

```rust
// Rust
tracing::debug!("var={:?}, expected={:?}", var, expected);
```

### Breakpoint Debugging
Use debugger to:
- Set breakpoints at suspected issue location
- Step through code execution
- Inspect variable values
- Evaluate expressions
- Check call stack

## 6. Isolation Techniques

### Minimal Reproduction
1. Remove unrelated code
2. Simplify to bare minimum that reproduces issue
3. Use minimal test data
4. Eliminate dependencies where possible

### Component Testing
- Test individual functions in isolation
- Mock external dependencies
- Verify inputs and outputs separately
- Check boundary conditions

## 7. Data Validation

Verify assumptions about data:
- [ ] Check actual data types
- [ ] Verify data ranges and boundaries
- [ ] Confirm null/nil handling
- [ ] Validate data format and structure
- [ ] Test with edge cases (empty, max, min, special chars)

## 8. Concurrency Issues

For multi-threaded/async code:
- [ ] Check for race conditions
- [ ] Verify proper synchronization (locks, channels)
- [ ] Look for deadlocks
- [ ] Check resource cleanup
- [ ] Test with different timing/loads
- [ ] Use race detectors (Go: -race, Rust: cargo-sanitizer)

## 9. Performance Debugging

If issue is performance-related:
- [ ] Profile the code (CPU, memory, I/O)
- [ ] Identify hot paths and bottlenecks
- [ ] Check database query performance
- [ ] Analyze algorithm complexity
- [ ] Look for unnecessary allocations
- [ ] Check for resource leaks

## 10. External Dependencies

Check third-party issues:
- [ ] Review dependency documentation
- [ ] Check for known issues (GitHub issues)
- [ ] Verify API compatibility
- [ ] Test with different versions
- [ ] Check for breaking changes in updates

## 11. Documentation and Resolution

Once resolved:

### Root Cause
- What was the actual problem?
- Why did it occur?
- How was it overlooked initially?

### Solution
- What changes fixed the issue?
- Why does this solution work?
- Are there any side effects?

### Prevention
- How can similar issues be prevented?
- What tests should be added?
- What documentation should be updated?
- Should monitoring/alerting be added?

## 12. Output Format

Provide debugging results in this structure:

### Problem Summary
[Clear description of the issue]

### Root Cause
[What was causing the problem]

### Evidence
- [Stack traces, logs, error messages]
- [Variable states that revealed the issue]
- [Test results]

### Solution
```language
[Code fix with explanation]
```

### Testing
- [ ] Verified fix resolves original issue
- [ ] Tested edge cases
- [ ] Added regression tests
- [ ] No new issues introduced

### Preventive Measures
- [Tests to add]
- [Documentation to update]
- [Code patterns to follow]
- [Monitoring to implement]

### Lessons Learned
- [What this revealed about the codebase]
- [How to catch similar issues earlier]
