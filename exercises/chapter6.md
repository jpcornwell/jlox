
Challenge 1
-----------

In C, a block is a statement form that allows you to pack a series of
statements where a single one is expected. The comma operator is an analogous
syntax for expressions. A comma-separated series of expressions can be given
where a single expression is expected (except inside a function call’s argument
list). At runtime, the comma operator evaluates the left operand and discards
the result. Then it evaluates and returns the right operand.

Add support for comma expressions. Give them the same precedence and
associativity as in C. Write the grammar, and then implement the necessary
parsing code.

Answer
------

Implemented.

Grammar would look like this:
expression -> comma;
comma -> equality ("," equality)\*;
equality -> comparison (("!=" | "==") comparison)\*;
...

Challenge 2
-----------

Likewise, add support for the C-style conditional or “ternary” operator ?:.
What precedence level is allowed between the ? and :? Is the whole operator
left-associative or right-associative?

Answer
------

Implemented.

I don't totally understand the precedence level question. I have written the
parser so that it evaluates the "ternary conditional rule" again.

I made the operator right associative so that the user can easily chain these
together and make a sort of switch construct.

Challenge 3
-----------

Add error productions to handle each binary operator appearing without a
left-hand operand. In other words, detect a binary operator appearing at the
beginning of an expression. Report that as an error, but also parse and discard
a right-hand operand with the appropriate precedence.

Answer
------

Implemented. 

But I cheated and looked at the answers. I wasn't sure how to handle an error
without immediately bailing out of the parsing. I forgot that the error
function only returns an exception and it's up to the caller to decide if that
gets thrown or not, which in turn lets you decide whether to keep parsing or to
enter panic mode.
