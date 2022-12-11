# FMT-JS
A library to help in building textual programming languages.

Matches input source and fabricates a new string from it.

# Usage
This is a JavaScript library function.  Call the API.

# API
## Transpile
`[success, transpiled, errormessage] = transpile (src, grammarName, grammar, fmt, ohm, compilefmt)`

Match *src* and fabricate a new source string from it.  AKA "transpilation".

Transpile *src* using the grammar and the *fmt* fabrication specification.  
1. First, it compiles *fmt* to an internal form[^int] for use with Ohm-JS.
2. Second, *src* is pattern-matched ("parsed") against the given *grammar* with name *grammarName*.  *GrammarName* is a simple string. The *grammar* is a string containing Ohm-JS DSL rules.
3. Third, the fabrication rules are applied to the pattern match ("CST" - Concrete Syntax Tree)
4. Fabrication produces a single string.  That string is returned in the variable *transpiled*.
Note tht

[^int]: The internal form is JavaScript code.  See Ohm-JS documentation for the full glory of what can be specified here.  *Fmt* is a restricted syntax that is meant only for creating strings.  Ohm-JS semantics, expressed as JavaScript can do much more than this.

- success - return value - boolean true if no errors

- *ohm* is a function - it must be the function supplied by Ohm-JS 
- *compilefmt* is a function - it must be the function supplied by *fmt-js.js*

The two functions - *ohm* and *compilefmt* - must be passed into the *transpile* function because of the differences between JavaScript and node.js (`src` element vs `require`) that make it impossible to write *transpile* in a generic manner.

## HTML
To load the required functions in a .HTML file, use the following code:
```
<!-- Ohm-JS -->
<script src="https://unpkg.com/ohm-js@16/dist/ohm.min.js"></script>


<!-- Transpiler -->
<script src="fmt-js/fmt-js.js"></script>
<script src="fmt-js/transpile.js"></script>

...
	  [success, transpiled, errormessage] = transpile (src, grammarName, grammar, fmt, ohm, compilefmt);
...
```

Where *src*, *grammarName*, *grammar*, and, *fmt* depend on the application.

Where *ohm*, and, *compilefmt* are used literally as-is.

## Node.js
To load the required functions in a node.js program, use the following code:

```
const ohm = require ('ohm-js');
const fmt = require ('fmt-js/fmt-js.js');
const transpiler = require ('fmt-js/transpile.js')
...
	  [success, transpiled, errormessage] = transpile (src, grammarName, grammar, fmt, ohm, fmt.compilefmt);
...
```
