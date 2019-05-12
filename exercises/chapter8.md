
Challenge 1
-----------

The REPL no longer supports entering a single expression and automatically
printing its result value. That’s a drag. Add support to the REPL to let users
type in both statements and expressions. If they enter a statement, execute it.
If they enter an expression, evaluate it and display the result value.

Answer
------

Implemented.

The approach I took was to modify the parser and interpreter to have two main
entry points each. You can pick from parseProgram, parseExpr, interpretProgram,
and interpretExpr. This keeps the overall logic simple. In order to decide
which entry points I then use, I simply look at the tokens returned by the
scanner. If there is no semicolon token, I assume I am dealing with a single
expression. If there is a semicolon, I handle it like a regular program.

Challenge 2
-----------

Maybe you want Lox to be a little more explicit about variable initialization.
Instead of implicitly initializing variables to nil, make it a runtime error to
access a variable that has not been initialized or assigned to, as in:

```
// No initializers.
var a;
var b;

a = "assigned";
print a; // OK, was assigned first.

print b; // Error!
```

Answer
------

Implemented.


Challenge 3
-----------

What does the following program do?

```
var a = 1;
{
  var a = a + 2;
  print a;
}
```

What did you expect it to do? Is it what you think it should do? What does
analogous code in other languages you are familiar with do? What do you think
users will expect this to do?

Answer
------

The code prints the value 3.

This actually is what I expected it to do. It is odd code, but it makes sense
that it evaluates the right hand side, which at that point is using the outer
variable, and computes 3, which it then assigns to a new inner variable.

I think it is perfectly valid for this behavior to exist. Though it may be
confusing to the unitiated.

Perl 6 will actually throw an error and tell you that it's not possible for a
variable's initialization to refer to itself.

I believe that novice programmers will get a shock from this, but veterans
should be able to realize pretty quickly what is going on.

