Syntactically Awesome Style Sheets (SASS) or SCSS is a interpreted language which is used to create [[CSS]]. SCSS is a superset of CSS with an addition of features such as variables, functions, and nesting. A SASS file can be preprocessed with the command `sass input.scss output.css`. With arguments such as `--watch` automatically changing modifying the CSS file after saving. SASS has to types of syntax **SCSS** and **SASS**. These differences are curly braces vs indentation. **SCSS** the more popular variant appears like:
```scss
.selector {
	color: red;
}
```
While **SASS** the less popular due to it not being backwards compatible with CSS can be display like:
```sass
.selector
	color: red
```

# Variables
Variables provide an ability to keep consistent values across files. They are consistently used in conjunction with relative values as to allow for values to be changed easily depending of the conditions. This is done with the syntax:
```scss
$main-color: red
div {
	color: red;
}
```

# Nesting
Nesting provides an easier method of organising CSS. This allows for selectors to be easily visually represented with a nested syntax. This follows:
```scss
body {
	div {
		color: red;
	}
	a { color: blue; }
}
```

# Modules
Modules/Partials allow for subfiles to be created that when interpreted interpret into its main file. This allows for files name with a preceding underscore such as `_partials.scss` to be interpreted into the main file where it is called with the `use` syntax. The difference between **module** and **partial** is that partials have greater compatibility while modules allow for variables to be called.

# Mixins
Mixins allow for reusable groups of CSS code. This code can even take arguments to allow for greater flexibility. This follows the syntax:
```scss
@mixin theme($theme:red) {
	color: $theme;
	display: flex;
}
div {
	@include theme($theme: blue)
}
```

# Extensions
Extensions function similar to [[SCSS#Mixins|Mixins]] however interpret to more concise CSS. This means they should be used when less dynamic styles are required. Extensions can be done with:
```scss
%theme {
	color: red;
}
div {
	@extend %theme;
}
```

# Operators
Mathematical operations can be done within SCSS code given `sass:math` is being used. This leads to mathematical operations to be interpreted upon runtime.
