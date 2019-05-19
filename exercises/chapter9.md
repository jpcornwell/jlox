
Challenge 1
-----------

A few chapters from now, when Lox supports first-class functions and dynamic
dispatch, then we technically won’t need branching statements built into the
language. Show how conditional execution can be implemented in terms of those.
Name a language that uses this technique for its control flow.

Answer
------

Smalltalk uses dynamic dispatch to accomplish conditional branching. That being
said, in that language everything is an object including the booleans. I don't
know if that is the case for Lox. If it were then you would have your true and
false objects do something like this.

```
class True {
  fun ifTrue(codeBlock) {
    codeBlock();
    return this;
  }
  fun ifFalse(codeBlock) {
    return this;
  }
}

class False {
  fun ifTrue(codeBlock) {
    return this;
  }
  fun ifFalse(codeBlock) {
    codeBlock();
    return this;
  }
}
```

And then to use it you could do

```
fun doFoo() { ... }
fun doBar() { ... }

(a < 5).ifTrue(doFoo).ifFalse(doBar);
```

Challenge 2
-----------

Likewise, looping can be implemented using those same tools, provided our
interpreter supports an important optimization. What is it, and why is it
necessary? Name a language that uses this technique for iteration.

Answer
------

The optimization is handling tail-end recursion. Tail-end recursion is when a
recursive function calls itself at the very end of the function's body. This
means that since the function isn't doing anything else with the return value
of the recursive call, the language implementation can reuse that function's
call stack frame. Reusing this prevents stack overflows, and allows for
arbitrarily long loops. Scheme's iteration capability is provided by taking
advantage of this technique.

Challenge 3
-----------

Unlike Lox, most other C-style languages also support break and continue
statements inside loops. Add support for break statements.

The syntax is a break keyword followed by a semicolon. It should be a syntax
error to have a break statement appear outside of any enclosing loop. At
runtime, a break statement causes execution to jump to the end of the nearest
enclosing loop and proceeds from there. Note that the break may be nested
inside other blocks and if statements that also need to be exited.

Answer
------

Implemented.

