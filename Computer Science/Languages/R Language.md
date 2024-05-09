R is a programming language used primarily for [[Data Science|data analytics]], and statistics. It takes a partially [[Functional Programming|functional]] approach but still has basic object support, [[Programming Paradigms#Imperative|imperative]] paradigms, and is [[Programming Paradigms#Static or Dynamic Typing|dynamically typed]].

# Syntax
R has a variety of minor syntactical changes, the most obvious being the assignment operator `<-`. Beyond this, Boolean operators follow the symbolic format, and statements use curly brackets to specify a new scope. It is also a 1-indexed language.

# Datatypes
It follows the basic Boolean, and character [[Datatypes|datatypes]] but modifies the integer types. Instead it has:
- **Integer** which functions as an integer.
- **Numeric** which functions as a floating point number.
- **Complex** which is a complex number.

Arrays are called vectors within R, and can most easily be created through list comprehensions or the concatenation function `c(…)`.

# Data Frames
A data frame is a set of vectors that contain any value. Values can be accessed by column name or index with `df[…]`. Columns can also be accessed with `df$…` which can also be extended to get certain indexes. For multidimensional arrays row and column

The `names(…)` operation gets the column's name and allows for changes. Amount of rows and columns can be accessed with `nrow(…)` and `ncol(…)`, or `dim(…)`. To display the column names and data types `str(…)`.

Sorting can be done through the `order(…)` command, with the optional `decreasing` field.

Merging of data frames can be done with `merge(…)` to merge by a common key, or `rbind(…)` which joins data frames vertically.

[[Data Science#Descriptive Statistics|Summary statistics]] can be found with `min(…)`, `mean(…)`, and `sd(…)`. For a full summary simply do `summary(…)`.
