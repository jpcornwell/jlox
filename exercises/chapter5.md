
Challenge 1
-----------

Earlier, I said that the |, \*, and + forms we added to our grammar metasyntax
were just syntactic sugar. Given this grammar:

```
expr → expr ( "(" ( expr ( "," expr )* )? ")" | "." IDENTIFIER )*
     | IDENTIFIER
     | NUMBER
```

Produce a grammar that matches the same language but does not use any of that
notational sugar.

Bonus: What kind of expression does this bit of grammar encode?

Answer
------

```
expr → expr "()"
expr → expr "(" arg ")"
expr → expr "." IDENTIFIER
expr → IDENTIFIER
expr → NUMBER

arg → arg ", " arg
arg → expr
```

This grammar represents number literals and identifiers optionally followed
by a field access or method invocation.

Challenge 2
-----------

The Visitor pattern lets you emulate the functional style in an object-oriented
language. Devise a corresponding pattern in a functional language. It should
let you bundle all of the operations on one type together and let you define
new types easily.

(SML or Haskell would be ideal for this exercise, but Scheme or another Lisp
works as well.)

Answer
------

I'm skipping this one. I definitely want to learn a Lisp language and Haskell
eventually, but one project at a time. Also as a side note, the visitor pattern
is kind of weird. This book claims that using this pattern is faster than a big
if else sequence of instanceof, but I would be curious to see some metrics as
to how much faster that is. I googled to see the advantages of visitor pattern,
and the answers I saw were not very convincing. All I got were People claiming
that it is more object oriented or more elegant. The former is irrelevant and
the latter is debatable.  I suppose in this instance it would give you compile
time checks that you handled every subclass in a given Visitor implementation,
but even that is partly due to the fact that Expr is auto-generated code.
Without that, you'd still have to manually update the Visitor interface with a
new method each time you create a new subclass. It seems like the best solution
would be to use a programming language that allows for both an object oriented
approach (for say the scanner here which has some internal state) and the
ability to define simple data structures (like Expr and its subtypes) that can
then be pattern matched in a single function. I don't know enough about how
these mechanisms work to know if that is possible or practical though. It looks
like Perl 6 does this, but I need to play around with it some more.


Challenge 3
-----------

In Reverse Polish Notation (RPN), the operands to an arithmetic operator are
both placed before the operator, so 1 + 2 becomes 1 2 +. Evaluation proceeds
from left to right. Numbers are pushed onto an implicit stack. An arithmetic
operator pops the top two numbers, performs the operation, and pushes the
result. Thus, this:

```
(1 + 2) * (4 - 3)
```

in RPN becomes:

```
1 2 + 4 3 - *
```

Define a visitor class for our syntax tree classes that takes an expression,
converts it to RPN, and returns the resulting string.

Answer
------

Implemented in RpnPrinter.java

