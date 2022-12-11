![[transpile.png]]
A DSL for writing DSLs.

Transpile() is a library function for transpilation.

See examples of use in `pe` (parsing explorer) and `fabx` (Fabrication explorer).

# Usage - API
## Transpile (...)
`function transpile (src, grammarName, grammars, fmt, ohmlang, compfmt, supportfname)`

returns
`[Boolean, transpiled, errorMessage]`

- `src` is a string, containing the source text-to-be-transpiled
- `grammarName` is a string containing the name of the grammar (a single string - `grammars` see below - can contain multiple grammars)
- `grammars` is a string containing one or more grammars in Ohm-JS format
- `fmt` is a string containing a fabrication specification (formerly known as ForMaT)
- `ohmlang` is a JavaScript function - the Ohm engine, often installed in the enclosing HTML using `<script src="https://unpkg.com/ohm-js@16/dist/ohm.min.js"></script>` and referred to by the name `ohm`
- `compfmt` is a JavaScript function installed in the enclosing HTML using ```
    <script src="fmt-js/fmt-js.js"></script>
    <script src="fmt-js/transpile.js"></script>``` and referred to by the name `compilefmt`
- `supportfname` is a string containing the pathname for a JavaScript file containing support functions referred to by the fabrication (`fmt`) specification

On return:
- `Boolean` is either JavaScript `true` or JavaScript `false`, if the transpilation succeed or failed, respectively
- `transpiled` is a string containing the newly-transpiled text, or the empty string if errors occurred
- `errorMessage` is a string, empty if the transpilation fully succeeded, else containing the text of an error message.

# Usage - HTML
```
<script src="https://unpkg.com/ohm-js@16/dist/ohm.min.js"></script>
...
<script src="transpile/fmt-js.js"></script>
<script src="transpile/transpile.js"></script>
```
## Multigit
Include this repository using `multigit`.

Use `multigit -r` to fetch the library into your project after ensuring that `.gitignore` and `subrepos` are correctly configured (see below).

### .gitignore
Add `transpile/` to your project's `.gitignore` file.

### subrepos
Create a file `subrepos` that contains the lines
```
subrepos:
- path: 'transpile'
  repo: 'git@github.com:guitarvydas/transpile.git'
  branch: 'main'
```

## Node.js
To load the required functions in a node.js program, use the following code:

```
const ohm = require ('ohm-js');
const fmt = require ('transpile/fmt-js.js');
const transpiler = require ('transpile/transpile.js')
...
	  [success, transpiled, errormessage] = transpile (src, grammarName, grammar, fabspec, ohm, fmt.compilefmt, supportFileName);
...
```

# Warts
- historically, this used to be called `fmt-js`
	- clean up needed to rename `fmt-js.*` to `transpile`
- historically, this function has been split into two files
	- `fmt-js.js`
	- `transpile.js`
	- clean up needed to combine everything into one file
# See Also
- Ohm-JS documentation https://ohmjs.org
- a REPL for language/grammar development https://ohmjs.org/editor/
- example usage Parsing Explorer https://github.com/guitarvydas/parsingexplorer
- example usage Fab Explorer https://github.com/guitarvydas/fabx
- `multigit` https://pypi.org/project/multigit/ (sane use of `git` for using sub-repositories)