### YAML Syntax
{% if page %}
:::{tip}
:class: margin
We recommend [learn YAML in Y minutes](https://learnxinyminutes.com/docs/yaml/) for an extensive intro to YAML syntax.
:::

YAML syntax is designed to be **easy to read and write**.
Here are some key elements of YAML syntax:
{% endif %}
{% if slide %}::::{grid}{% endif %}
{% if slide %}:::{grid-item-card}{% else %}#### 1.{% endif %} Basic Structure

- **Key-Value Pairs**: {% if page %}YAML uses a simple key-value pair structure, where keys are followed by a colon and a space.{% endif %}
  ```yaml
  name: John Doe
  age: 30
  ```

- **Nested Structures**: {% if page %}Indentation (using spaces, not tabs [^sn1]) is used to represent nested data.
[^sn1]: Using spaces for indentation ensures consistency across different editors and environments, as tabs can be displayed differently depending on the settings of the text editor or IDE. For example, one editor might display a tab as four spaces wide, while another might display it as eight spaces wide. This inconsistency can lead to misaligned code, making it harder to read and maintain.
{% endif %}
  ```yaml
  person:
    name: John Doe
    age: 30
  ```
{% if slide %}:::{% endif %}
{% if slide %}:::{grid-item-card}{% else %}#### 3.{% endif %} Strings
- **String Formatting**:{% if page %} Strings can be written in plain format, or enclosed in quotes (single or double).{% endif %}
  ```yaml
  greeting: "Hello, World!"
  farewell: 'Goodbye!'
  ```
- **Multiline Strings**:{% if page %} Use the pipe (`|`) for multiline strings, preserving line breaks.{% endif %}
  ```yaml
  descr: |
    A multiline string.
    Retains line breaks.
  ```
{% if slide %}:::
::::
{% endif %}
:::{admonition} Abbreviated forms
:class: note, margin
Lists and Dictionaries can be condensed:
- `start = ["a", "b"]`
- `user = {name: John, job: Developer}`
:::
{% if slide %}::::{grid}
:::{grid-item-card}{% else %}#### 2.{% endif %} Lists
{% if page %}- **Lists**: Lists are created using a hyphen followed by a space.{% endif %}
  ```yaml
  fruits:
    - Apple
    - Banana
    - Cherry
  ```
{% if slide %}:::{% endif %}
{% if slide %}:::{grid-item-card}{% else %}#### 4.{% endif %} Comments
{% if page %}- **Comments**: Comments start with a `#` and continue to the end of the line.{% endif %}
  ```yaml
  # A comment
  name: John Doe  # Also a comment
  ```
{% if slide %}:::{% endif %}
{% if slide %}::::{% endif %}

