
Challenge 1
-----------
Pick an open source implementation of a language you like. Download the source
code and poke around in it. Try to find the code that implements the scanner
and parser. Are they hand-written, or generated using tools like Lex and Yacc?
(.l or .y files usually imply the latter.)

Looking at the CPython implementation on github, I believe that the scanner and
parser are both handwritten. I was kind of suprised how difficult it was to
follow what was happening without reading accompanying documentation.

Challenge 2
-----------
Just-in-time compilation tends to be the fastest way to implement a
dynamically-typed language, but not all of them use it. What reasons are there
to not JIT?

Adds complexity to your language implementation.

Using JIT introduces unpredictability because the runtime can make decisions
on the fly as to when and how to compile or optimize code. This may not be
desirable in certain safety critical applications.

Memory overhead may be impractical for low level devices.

Challenge 3
-----------
Most Lisp implementations that compile to C also contain an interpreter that
lets them execute Lisp code on the fly as well. Why?

Reading a little bit into Lisps in the past, it sounds like the line between
compiling and interpreting is fuzzy, and that this allows for a very powerful
language feature called macros. Macros in Lisp are not like macros in other
languages which typically just entails string preprocessors. In Lisp, macros
will actually manipulate code on the fly. I'll leave it at that for this
answer, but in the future I plan to learn a lot more about Lisp languages.
