# FMT-JS
A DSL to help in building programming languages.

Meant to specify semantics for Ohm-JS grammars.

# Usage
This is a JavaScript library function.  Call the API.

# API
## Transpile ()
`function transpile (src, grammarName, grammars, fmt, ohmlang, compfmt, supportfname)`

returns
`[Boolean, transpiled, errorMessage]`



# Demo
To test the transpile function...
5. Load `tester.html` into a browser.
6. Click "Test small" button to see that everything has loaded and is working.
7. Reload, click "Test Game Language (Ghost Stars)" button to convert a piece of a game script to JSON.


# Beautiful Assembler

> ~31:50 "In a 'real' Computer Science, the best languages of an era should serve as 'assembly code' for the next generation of expression.

[https://www.youtube.com/watch?v=fhOHn9TClXY&t=859s](https://www.youtube.com/watch?v=fhOHn9TClXY&t=859s)

# Sample Files Written in FMT-JS
See source code strings in fmt-js.html `smallsrc`, `smallsrc2`, `smallsrc3` and `bigtest`.

Note that the samples can be loaded by clicking on the appropriate "Use ..." buttons (see above).

# Documentation
Documentation from langjam0003 is https://publish.obsidian.md/programmingsimplicity/2022-07-24-FMT-JS+Documentation

## Philosophy
Treat SCNs like bowls of candy.

Bolt Ohm-JS + Fmt-JS together --> transpile SCN-source-code to executable code.

(SCN == mini-DSL ; Solution Centric Notation).

# N.B.

The output is Javascript, meant to be bolted into an Ohm-JS project.

The output Javascript is not neatly formatted.  I emphasize machine-readability-writability over human-readability.

Human readability can be achieved by grinding the output through a pretty-printer (I currently use emacs' "indent-region" command).

# Other Languages, C++, Python, Rust, JSON, Etc
Ohm-JS and Fmt-JS happen to be written in Javascript, but, they implement an new DSL (an SCN for parsing).

It should be possible to generate code for any other textual language using Ohm-JS and Fmt-JS.

(In fact, I have generated Python and JSON and Common Lisp code using Ohm-JS).

# Contrib
I would enjoy handing this off to anyone who wants to understand it and clean it up.

# Ohm-JS and Ohm-Editor
I strongly recommend using Ohm-Editor and Ohm-JS for grammar development.
[ohm-js](https://ohmjs.org/)
[ohm-editor](https://ohmjs.org/editor/)

# Acknowledgements
The grammar for the "big test" is based on parsing a snippet of code in WrittenScript](https://github.com/KinectTheUnknown/WrittenScript) discussed in the Discord [ohmland](https://discord.com/channels/779282197152661525/779286160597319680/992714506033692692)

The source code for the Ghost Stars test is a snippet from [Ghost Stars](https://oofoe.itch.io/ghost-stars).

# Revision
test from parallels
