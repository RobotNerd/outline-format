# Outline Standard

The outline format is a text-only document format for simple
outline-style lists.

> TODO include links to plugins for syntax highlighting + extra functionality

### File type

Outline documents are text-only with a file extension of `.outline`.

### Sections

A section header must meet the following criteria:
- No leading spaces.
- Begin with a capitalized alphabetic character, i.e. [A-Z].

A section header is not required, but it is considered a best
practice to have at least one section header per file.

### Unordered lists

Unordered list items begin with a single character representing a
bullet point. The character chosen for a bullet point conveys meaning:
- `-`: A normal list item. The default case.
- `*`: Alternative to `-`.
- `?`: A question that needs to be resolved.
- `!`: An important/critical item.
- `x`: An invalid or deprecated item.

A single space must separate the bullet point and the text of
the list item.

### Indenting

List items at the same indentation level are considered to be in the
same logical group. This is important when converting to other formats
where bullet points are represented by different icons depending on
their indentation level.

Recommended indentation is done with spaces with 2 spaces per tab stop.

### Multi-line list items

List items can span multiple lines. Add a line break and indent the
second (and subseqent) line by two space from the column with the
bullet point. If any of these lines begin with a bullet point, then
they will be considered new child list items instead of a continuation
of the previous item.

When converting to other formats that support line-wrapping, the
line breaks and spacing will be converted to a single space (like
when rendering HTML).

```
My Section
- A list item can span multipe lines if you add a line break
  and indent two additional spaces. All subsequent lines should
  be left-aligned with the second line.
```

> TODO

### Quoted strings

> TODO

### URIs

> TODO

### Brackets

> TODO

### Tags: TODO, FIXME, etc.

The items in the list below act as special metadata tags. Syntax
highlighting of outline documents can highlight these items to make 
them stand out.

- BUG
- DEPRECATED
- FIXME
- IMPORTANT
- TODO

The following rules define when these items are recognized as valid
tags in an outline document:
- A space must both precede and follow the tag and any other alphanumeric
  character. For example, the `TODO` substring of `[TODO]` will be
  recognized as a tag but in `TODOstuff` it will not.
- Tags are not recognized when part of a section header.

### Comments

Comments begin with double hashtags `##` and terminate at the end of
the line.

### Examples

Here are some examples if valid and invalid outline-formatted documents.

> TODO

### Best Practices

- The first line of the file should be a section header, even
  if the file will only have one section.

  ```
  My Section
  - list item
  - another list item
  ```

- A single blank line should occur before all section headers
  except the one on the first line.

  ```
  My first section
  - list item

  My second section
  - list item
  - another list item
  ```

- Don't mix and match `-` and `*` bullet points at the same indentation
  level under the same section heading. Choose one and stick with it.
- There should be no blank lines between any two consecutive list items.
- Comments at the end of a line (placed after uncommented text)
  should be preceeded by a single space. There should also be a single
  space after the `##` that begins the comment.

  ```
  My list
  - list item
  - another list item ## with a comment at the end of the line
  ## - don't add the preceeding space if commenting out the entire line
  ```

- Spaces should be used for indentation instead of tabs.
- Indentation should be 2 spaces per tab stop.

### Acknowledgements

Inspired by https://fountain.io/.

