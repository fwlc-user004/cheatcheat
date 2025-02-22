# Unit Testing Cheat Sheet

## Overview
Unit testing is a software testing method that focuses on verifying individual components or "units" of code in isolation.  

## Benefits
- **Early Bug Detection:** Identify and fix issues at the component level.
- **Refactoring Safety:** Ensure that changes don’t break existing functionality.
- **Documentation:** Tests serve as examples of how functions or classes are intended to be used.

## Best Practices
- **Isolate Tests:** Ensure each test runs independently.
- **Descriptive Names:** Use clear, descriptive names for test functions/methods.
- **One Behavior per Test:** Test a single behavior or scenario.
- **Arrange, Act, Assert (AAA):**
  - **Arrange:** Set up necessary objects and prerequisites.
  - **Act:** Execute the function or method under test.
  - **Assert:** Verify the result matches expectations.
- **Mock External Dependencies:** Use stubs or mocks to isolate unit behavior.
- **Keep Tests Fast:** Fast tests encourage frequent execution.

## Popular Frameworks

### Python
- **unittest:** Built-in framework.
- **pytest:** More powerful and flexible, with easy syntax.

### Java
- **JUnit:** Widely used testing framework.
- **TestNG:** Provides additional features like parameterized testing.

### JavaScript
- **Jest:** Comprehensive testing framework with built-in mocking.
- **Mocha:** Flexible testing framework often used with assertion libraries like Chai.

### Other Languages
- **C#:** NUnit, xUnit
- **Ruby:** RSpec
- **C/C++:** Google Test (gTest)

## Example Code

### Python (pytest)
```python
# Function to test
def add(a, b):
    return a + b

# Unit Test
def test_add():
    assert add(2, 3) == 5
