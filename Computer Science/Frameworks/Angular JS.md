Angular JS is a [[JavaScript]] framework that is used for web development. Angular is a framework written in [[TypeScript]] and as such is compiled from typescript into JS. Simply Angular can be thought of as a set of custom tags that interact with each other. An angular file is composed of:
- `index.html` is the main [[HTML]] file that includes the required libraries and bootstraps angular applications.
- `script.ts` which is the main file where code is located.
- `system.config.ts` which is a configuration file for System JS which handles module loading and compilation.
- `tsconfig.json` configures Typescript compilation, and compiles it into JS.
An angular project can be made with the command-line command `ng new projectname`

# Components
Angular JS works through breaking up code into **components**. A component is a **class** that can be used as a tag within a HTML file. Components can automatically be created through the command line with the command `ng generate component name`. This will create all the files for a component.

To create a component manually an **annotation** must be used. This is done with the keyword `@Component`, which has an optional field which takes an object. These mask boiler plate code, and function as fundamental building blocks.

# String Interpolation
String interpolation is done with the syntax `{{ }}` which is a type of Angular that runs a command to change the HTML.

# Directives
Structural directives provide conceptual information for how directives work. In general these directives give a tag a condition for their existence. Whether that be a simple if condition, or a for loop. The main structural directives include:
- `*ngFor` which creates a html element that can be repeated. This takes a string which follows `let x of xs`.
- `*ngIf` creates an element give n

# Property Binding
A property binding is used to allow the code to determine a tag's property. This is done through the syntax `[properies]="cond"`, this condition usually a variable found within an object. A property can be an **input** if within the class the variable has the decorator `@Input('...')`. This takes a value from the HTML and sets itself to be it..

# Events
An event can be done through the keyword `(click)="..."` found within a HTML tag's property. The keyword `toggle(...)` is another event which can be used as a result of a click.
