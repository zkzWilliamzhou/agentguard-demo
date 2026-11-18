# Large Instructions File

This file demonstrates the 32KiB truncate limit issue.

## Introduction

This file contains extensive documentation that exceeds the 32KiB limit that Codex and some other AI agents impose when reading instruction files. When files exceed this limit, these agents silently truncate the content, which can lead to important instructions being lost.

## Why This Matters

AI coding agents often read instruction files to understand project conventions, coding standards, and important guidelines. When these files are too large:

1. **Information Loss**: Only the first 32KiB is read, potentially cutting off critical instructions
2. **Inconsistent Behavior**: Different agents may have different truncate limits
3. **Silent Failures**: The agent doesn't alert you to truncation

## Best Practices

1. **Split Large Files**: Use AGENTS.md for core instructions and move detailed guides to a docs/ directory
2. **Prioritize Content**: Place the most important information at the beginning of files
3. **Use References**: Link to external documentation instead of embedding large content

## Detailed Instructions

### Coding Standards

Follow these coding standards when working on this project:

1. **Naming Conventions**
   - Files should use snake_case
   - Classes should use PascalCase
   - Constants should use UPPER_SNAKE_CASE

2. **Documentation**
   - All public functions must have docstrings
   - Complex logic should have comments
   - Update documentation when code changes

3. **Testing**
   - Write tests before implementing features
   - Aim for high code coverage
   - Run all tests before committing

4. **Security**
   - Never commit secrets or API keys
   - Validate all user inputs
   - Use environment variables for sensitive data

### Git Workflow

1. Create a feature branch for each new feature
2. Commit frequently with clear, descriptive messages
3. Push changes and create a pull request
4. Get review from at least one other person
5. Merge only after approval

### Code Review Process

1. **Automated Checks**
   - Linting must pass
   - All tests must pass
   - No security issues

2. **Manual Review**
   - Check code correctness
   - Verify test coverage
   - Review documentation
   - Spot potential improvements

### Performance Considerations

1. **Efficiency**
   - Avoid unnecessary computations
   - Use appropriate data structures
   - Profile code before optimizing

2. **Memory Usage**
   - Be mindful of memory allocations
   - Clean up resources properly
   - Use generators for large datasets

### Error Handling

1. **Exceptions**
   - Catch specific exceptions
   - Provide meaningful error messages
   - Log errors appropriately

2. **Validation**
   - Validate inputs early
   - Fail fast on invalid data
   - Provide error recovery options

### Security Guidelines

1. **Input Validation**
   - Sanitize all external inputs
   - Validate data types and ranges
   - Reject malformed requests

2. **Authentication & Authorization**
   - Use strong authentication
   - Implement proper authorization
   - Never trust user input

3. **Data Protection**
   - Encrypt sensitive data
   - Use secure communication
   - Implement proper access controls

## Example Code

```python
def example_function(param: str) -> str:
    """Example function with proper documentation.
    
    Args:
        param: Input parameter
        
    Returns:
        Processed result
    """
    if not param:
        raise ValueError("Parameter cannot be empty")
    
    # Process the input
    result = param.strip()
    
    return result
```

## Conclusion

Following these guidelines helps maintain code quality, security, and consistency across the project.