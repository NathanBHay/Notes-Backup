Bash is a Unix shell and command language written to allow commands to be done to call actions. Some common bash commands are:
- **Man** gets the manual for a given function.
- **Echo** which prints a message.
- **PWD** which returns your current directory.
- **CD** which navigates to a new directory.
- **MV**/**CP** to move or copy a file to a new directory.
- **LS** lists the content, use the **-lh** to check the size.
- **Head** to check the first few lines of a file, with **-number** to check a certain amount of lines.
- **Less** displays the contents of a file or output one page at a time.
- **WC** counts the amount of lines, words, and letters. Use **-l** to get lines, **-w** to get words, and **-m** counts characters.
- **Cut** is used to process and filter text files. Use **-f** to get data by a set of fields, **-b** to get specifying set of bytes, **-c** to select by set of characters. For example *-f 3,5* is used to get the third and fifth column.
- **Awk** which is used to select something, and then do an action.
- **Grep** is used to find a line that contains the given word, and returns the entire line that the word appeared on. Use **-i** to search case-insensitive search, **-R** to search all directories for the line, **-c** displays the total number of appearances of the input.
- **Uniq** gets a list of the unique data in a space. Use **-c** to count the number of unique values.
- **|** pipe is used to take the output of the left operation and feed it as the input into the right operation.
- **>** redirect is used to create a new file from the given data.

File reading is done through the following commands:
- **Gunzip** which read and interprets *.gz* files.
- **tar** which read and interprets *.tar* files

Bash has two shell modes for command execution, those are batch and concurrent.
- **Batch** is done with the delimiter `;` or a new line, which signifies the next instruction.
- **Concurrent** is done with the `&` keyword which runs the first command in the background, and the second in the foreground.
