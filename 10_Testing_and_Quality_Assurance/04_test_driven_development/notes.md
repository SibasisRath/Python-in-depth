# Test-Driven Development (TDD)

## Explanation

TDD is a development methodology where tests are written before the code that makes them pass. The cycle is often described as **Red‑Green‑Refactor**:

1. **Red**: write a failing test.
2. **Green**: write just enough code to make the test pass.
3. **Refactor**: clean up the code while ensuring tests still pass.

Benefits include better design, regression protection, and clarity of requirements.

## Examples

1. Write a test for a `Stack` class’s `push` method.
2. Run the test to see it fail.
3. Implement `Stack.push` and rerun until the test passes.
4. Refactor the `Stack` implementation and ensure the test still succeeds.

## Tasks

### Beginner
1. Follow the Red‑Green‑Refactor cycle to implement a small utility function (e.g., palindrome checker).
2. Use a test runner to automatically re-run tests on file changes.

### Intermediate
1. Apply TDD while building a small module with multiple functions or classes.
2. Pair-program with another developer using TDD to solve a problem.

### Advanced
1. Integrate TDD into a larger project and use coverage reports to identify untested code.
2. Evaluate when TDD might not be appropriate and how to adapt.

## Quick Review
- What are the three stages of the TDD cycle?
- Why does TDD often lead to simpler interfaces?

---