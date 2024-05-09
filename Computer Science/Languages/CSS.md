Cascading Styling Sheets, is a language used to format [[HTML]], separating design elements into a new file or section of a file. This file follows the `.css` format, and enables the HTML to pull from the file. Similarly the `<style>` tag can be used to declare a CSS section within a HTML file.

# Syntax
CSS follows the format of:
```
selector {
	property : value;
}
```
A **selector** finds the HTML element that is going to be styled. There are 5 main selector categories:
- **Simple** where an entire tag is selected.
- **Combinator** which selects based on a specific relation.
- **Pseudo-Class** which selects elements based on a certain state.
- **Pseudo-Element** that select and style a part of an element.
- **Attribute** which selects based on attribute or value.

The **simple selectors** include:
- Tags are selected by specifying the tag's name.
- ID selection is done with the `#` before the ID.
- Class selection is done with the `.` syntax. This can be used in conjunction to select tags based on a certain class.
- Group selection can be done with a comma, `,`.

The **combinator selectors** include:
- **Element Element Selector** which selects all elements inside an element.
- **Child Selector** which uses `>` to select all children of an element.
- **Adjacent Selector** which uses `+` to select the next adjacent tags.
- **General Sibling** which use `~` to select all sibling tags.
