# ts-jison-lex

This is a fork of Zach Carter <zach@carter.name>'s [jison module](https://www.npmjs.com/package/jison-lex) tweaked to use just enough templates to make typescript compilers tollerate the generated parser.

Original Jison README (modulo compilation examples):
====
A lexical analyzer generator used by [jison](http://jison.org). It takes a lexical grammar definition (either in JSON or Bison's lexical grammar format) and outputs a JavaScript lexer.

## install
npm install jison-lex -g

## usage
```
Usage: jison-lex [file] [options]

file     file containing a lexical grammar

Options:
   -o FILE, --outfile FILE       Filename and base module name of the generated parser
   -t TYPE, --module-type TYPE   The type of module to generate (commonjs, js)
   --version                     print version and exit
```

## programatic usage

```
var JisonLex = require('jison-lex');

var grammar = {
  rules: [
    ["x", "return 'X';" ],
    ["y", "return 'Y';" ],
    ["$", "return 'EOF';" ]
  ]
};

// or load from a file
// var grammar = fs.readFileSync('mylexer.l', 'utf8');

// generate source
var lexerSource = JisonLex.generate(grammar);

// or create a parser in memory
var lexer = new JisonLex(grammar);
lexer.setInput('xyxxy');
lexer.lex();
// => 'X'
lexer.lex();
// => 'Y'

## license
MIT
