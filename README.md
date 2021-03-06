# Outline Format

The outline format is a text-only document format for simple lists.

These editor plugins provide support for outline documents:
- vim: https://github.com/RobotNerd/outline-vim

If your favorite editor does not have a plugin that supports .outline,
please write one and it will be linked here!

## File type

Outline documents are text-only with a file extension of `.outline`.

## Formatting rules

The formatting rules in this document are broken down into two groups:

Semantic
- Sections
- Unordered lists
- Indenting
- Comments
- Multi-line list items

Syntax highlighting (optional)
- Quoted Strings
- URIs and email addresses
- Tags: TODO, FIXME, etc.

### Sections

A section header must meet the following criteria:
- There must not be any leading whitespace on the line.
- The first character must be one of the following:
  - A-Z
  - a-z
  - `.`

A section header is not required, but it is considered a best
practice to have at least one section header per file.

### Unordered lists

Unordered list items begin with a single character representing a
bullet point. The characters listed below are recognized as a bullet
point if they are the first non-whitespace charater on the line.

The character chosen for a bullet point conveys meaning:
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

The recommendation is to use spaces instead of tabs and to use
2 spaces per indentation level.

### Comments

Comments begin with double hash `##` and terminate at the end of
the line. Commented out text is ignored when converting to other formats.

Comments cannot be embedded in quoted strings (including multi-line quotes).

### Brackets

Special notes are placed inside a pair from brackets `[]`.

- Begin with a `[`.
- End with a `]` or the end of the file, whichever comes first.

### Multi-line list items

List items can span multiple lines. Add a line break and indent the
second (and subsequent) line by two spaces from the column with the
bullet point. If any of these lines begin with a bullet point, then
they will be considered new child list items instead of a continuation
of the previous item.

Comments can be embedded in a multi-line list item. An entire line can be
commented out or just the end portion of the line. See the code block at the
end of this section for an example.

When converting to other formats that support line-wrapping:
- All contiguous whitespace should be converted to a single space
  (like rendering HTML).
- Comments are ignored.

```
My Section
- A list item can span multiple lines if you add a line break
  and indent two additional spaces. All subsequent lines should
  be left-aligned with the second line.
- This multi-line item can contain ## an embedded comment
  comments that will be ignored when converting to other formats.
- This multi-line item
## this entire line is commented out
  will continue onto this line and ignore fully commented out lines
```

### Quoted strings

Portions of a list item may be placed inside double quotes `"` so that
syntax highlighting can render that substring as visually distinct from
regular text. Quoted strings terminate either at an ending double quote
character or at a blank line. When converting multi-line quoted strings
to other formats, all contiguous whitespace should be collapsed into a single
space (like rendering HTML).

### URIs and email addresses

URIs and email addresses may be highlighted to make them visually distinct
from regular text. Formatting guidelines can be found here:
- Email: [RFC 3696](https://tools.ietf.org/html/rfc3696)
- URI: [RFC 3986](https://tools.ietf.org/html/rfc3986)

### Tags: TODO, FIXME, etc.

The items in the list below act as special metadata tags. Syntax
highlighting of outline documents can highlight these items to make
them stand out.

- BUG
- DEPRECATED
- FIXME
- IMPORTANT
- NOTE
- TODO

The following rules define when these items are recognized as valid
tags in an outline document:
- A space must both precede and follow the tag and any other alphanumeric
  character or underscore. For example, the `TODO` substring of `TODO,`
  will be recognized as a tag but in `TODO_stuff` it will not.
- Tags are not recognized when part of a section header or inside a
  quoted string.

## Best Practices

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
  should be preceded by a single space. There should also be a single
  space after the `##` that begins the comment.

  ```
  My list
  - list item
  - another list item ## with a comment at the end of the line
  ## - don't add the preceding space if commenting out the entire line
  ```
- Using comments:
  - Highlight parts of the outline that have become irrelevant. This may
    be useful a useful alternative to deleting content.
  - Add text to the document that may not fit the outline specification.
- Use brackets to add a note to a bullet point that will stand out from
  the surrounding text thanks to syntax highlight.

  ```
  My list
  - list item [TODO research and update this item]
  - another list item
  ```

- Try to keep bracketed blocks limited to a single line.
- Comments vs. brackets:
  - Use comments for temporary removal ("hiding") of parts of the document.
  - Use brackets to include special notes that will visually stand out from
    the surrounding text.
  - Brackets add information. Comments remove information.
- Spaces should be used for indentation instead of tabs.
- Indentation should be 2 spaces per tab stop.
- The recommended maximum line length is 80 characters.
  This does not apply to long text strings that cannot be split up (e.g. URLs).
- Quoted strings that span multiple lines should be left-aligned
  following the same rules as standard multi-line indenting.

## Examples and testing

The `test/` directory contains example outline files. Each file
contains examples for a specific formatting type. The focus is to provide
examples of edge cases that could cause problems for syntax highlighters.

## Acknowledgements

Inspired by https://fountain.io/.
