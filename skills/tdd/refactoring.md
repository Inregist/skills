# Refactor Candidates

After TDD cycle, look for:

- **Duplication** -> Extract function/class
- **Long methods** -> Extract only when the helper names a real responsibility
- **Shallow modules** -> Combine or deepen
- **Feature envy** -> Move logic to where data lives
- **Primitive obsession** -> Add a value object only when rules repeat or invariants need a boundary
- **Existing code** the new code reveals as problematic
