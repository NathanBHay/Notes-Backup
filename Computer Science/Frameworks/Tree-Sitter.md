Tree-Sitter is a library for parsing programming languages and creating [[Parsing|parser]] generators and incremental parsers. It's goals are to be a fast generalised approach for creating a parser for any language. Tree-sitter is made within [[C Language|C]] and has many top binding libraries in popular programming languages. 

Tree-sitter functions through 4 basic objects. These are the **language** (`TSLanguage`) which defines how to parse a particular programming language. The **Parser** (`TSParser`) which is a stateful object that is assigned a language to produce a **tree** (`TSTree`), consisting of **nodes** (`TSNode`).

Creating grammars with tree-sitter is handled through the use of the tree-sitter CLI tool which uses either node or cargo to manage the tree-sitter package. For node this process simply follows
```bash
>> npm init
>> npm install --save nan
>> npm install --save-dev tree-sitter-cli
>> tree-sitter generate
```
This creates an environment for development to take place, given the existence of a `grammar.js` file. Tree-sitter's CLI commands include:
- `generate` which generates the conversion.
- `test` which tests the parser for correctness.
- `parse` which parses a given file.

The grammar following is a basic example of the `grammar.js` file. This creates a grammar based upon a series of declared rules. 
```js
module.exports = grammar({
    name: 'lambda-calculus',
    rules: {
      source_file: $ => ...
    }
});
```
All grammar rules take a identifier `$.identifier` as an argument. For the input file simply use `$`. The following commands are used to create a complex grammar:
- **String & Regex literals** which are defined with strings or regex patterns.
- **Sequences** `seq(rule,...)` which matches multiple rules together, similar to a union operation.
- **Alternatives** `choice(rule,...)` which matches any of the rules.
- **Repetitions** `repeat(rule)` which matches based upon zero-or-more occurrences of a given rule, or `repeat1(rule)` which is one-or-more.
- **Options** `optional(rule)` which matches based on zero-or-more.
- **Precedence** `prec(number,rule)` which assigns a rule a given numerical precedence as to avoid conflicts. With the higher ones being evaluated first.
- **Right & Left Associative** `prec.left([number],rule)` which forces left or right associativity.
- **Tokens** `token(rule)` marks a rule to produce a single token.
- **Immediate tokens** `token.immediate(rule)` matches only if their is no white-space.
- **Aliases** `alias(rule,name)` which gives a rule an alternative name.
- **Field** `field(name,rule)` which assigns a field name to the child.
