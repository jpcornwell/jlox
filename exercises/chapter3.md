
Challenge 1
-----------
Write some sample Lox programs and run them (you can use the implementations of
Lox in my repository). Try to come up with edge case behavior I didn’t specify
here. Does it do what you expect? Why or why not?

I tried creating a class method named 'this', but the interpreter said that it
wasn't a valid method name, which certainly makes sense.

One thing that surprised me though, was I had a method that was declared with
one parameter. I tried calling it without any arguments and I got an error. I
was expecting it to be more like javascript and simply fill in the parameter
with nil.

Challenge 2
-----------
This informal introduction leaves a lot unspecified. List several open
questions you have about the language’s syntax and semantics. What do you think
the answers should be?

What happens if you declare the same function name twice, but with different
definitions. For this language, I would let subsequent declarations overwrite
the previous ones.

Challenge 3
-----------
Lox is a pretty tiny language. What features do you think it is missing that
would make it annoying to use for real programs? (Aside from the standard
library, of course.)

The lack of a modulo operator makes the first few Project Euler problems more
difficult then they need to be.

Having list like functionality of some sort would be nice.

It would also be nice to have the ability to cast values to other types.

The language could also do with some more string type features. Currently, you
cannot use '\n' to indicate a new line.

No break statement for exiting loops.
