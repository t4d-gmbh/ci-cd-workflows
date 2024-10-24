### YAML Syntax

YAML syntax is designed to be easy to read and write. Here are some key elements of YAML syntax:

#### 1. Basic Structure

- **Key-Value Pairs**: YAML uses a simple key-value pair structure, where keys are followed by a colon and a space.
  ```yaml
  name: John Doe
  age: 30
  ```

- **Nested Structures**: Indentation (using spaces, not tabs) is used to represent nested data.
  ```yaml
  person:
    name: John Doe
    age: 30
  ```

#### 2. Lists

- **Lists**: Lists are created using a hyphen followed by a space.
  ```yaml
  fruits:
    - Apple
    - Banana
    - Cherry
  ```

#### 3. Strings

- **String Formatting**: Strings can be written in plain format, or enclosed in quotes (single or double).
  ```yaml
  greeting: "Hello, World!"
  farewell: 'Goodbye!'
  ```

- **Multiline Strings**: Use the pipe (`|`) for multiline strings, preserving line breaks.
  ```yaml
  description: |
    This is a multiline string.
    It retains line breaks.
  ```

#### 4. Comments

- **Comments**: Comments start with a `#` and continue to the end of the line.
  ```yaml
  # This is a comment
  name: John Doe  # This is also a comment
  ```

