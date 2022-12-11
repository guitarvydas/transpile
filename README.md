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

# Warts
- historically, this used to be called fmt-js
	- clean up needed to rename fmt-js.* to transpile
- historically, this function has been split into two files
	- `fmt-js.js`
	- `transpile.js`
	- clean up needed to combine everything into one file
# See Also
- Ohm-JS documentation https://ohmjs.org
- a REPL for language/grammar development https://ohmjs.org/editor/
- example usage Parsing Explorer https://github.com/guitarvydas/parsingexplorer
- example usage Fab Explorer *