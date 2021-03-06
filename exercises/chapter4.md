
Challenge 1
-----------
The lexical grammars of Python and Haskell are not regular. What does that
mean, and why aren’t they?

I'm skipping this question. To really understand it I'm going to have to delve
into my old textbooks. I plan on reading up and doing more compiler type
projects, so I feel comfortable kicking this one down the road.

Challenge 2
-----------
Aside from separating tokens — distinguishing print foo from printfoo  — spaces
aren’t used for much in most languages. However, in a couple of dark corners, a
space does affect how code is parsed in CoffeeScript, Ruby, and the C
preprocessor. Where and what effect does it have in each of those languages?

For pre-ANSI versions of the C preprocessor, the code was not allowed to have a
space before the '#' character.

Challenge 3
-----------
Our scanner here, like most, discards comments and whitespace since those
aren’t needed by the parser. Why might you want to write a scanner that does
not discard those? What would it be useful for?

An example of why it could be useful to parse comments would be how C# handles
XML comments. You can place comments in a specific XML format before your
functions, and then the compiled IL code will keep them so that it can be used
for intellisense.

An example of a parser keeping whitespace would be Python, which uses
whitespace instead of curly braces as a means of defining a code block.

Challenge 4
-----------
Add support to Lox’s scanner for C-style /* ... */ block comments. Make sure to
handle newlines in them. Consider allowing them to nest. Is adding support for
nesting more work than you expected? Why?

Okay, I added support for multiline comments and even allowed for them to be
nested. Overall it really wasn't too difficult. My function that consumes
multiline comments just calls itself if it gets to the beginning of another
multiline comment. This makes it easy to tell if the comment end markers are
not balanced.
