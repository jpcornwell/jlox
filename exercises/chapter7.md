
Challenge 1
-----------

Allowing comparisons on types other than numbers could be useful. The syntax is
shorter than named function calls and might have a reasonable interpretation
for some types like strings. Even comparisons among mixed types, like 3 <
"pancake" could be handy to enable things like heterogenous ordered
collections. Or it could lead to bugs and confused users.

Would you extend Lox to support comparing other types? If so, which pairs of
types do you allow and how do you define their ordering? Justify your choices
and compare them to other languages.

Answer
------

I would probably extend Lox so that the comparison operators also worked on
strings. This could simply return a value based on the lexicographic ordering
of the two strings. It hasn't been mentioned yet whether the strings in Lox
will be Unicode strings, but if so, I would keep things as simple as possible
and compare the Unicode code points.

If the types are mixed (one operand is a number and the other is a string) then
I would go ahead and throw an error. If we were using other symbols as possible
comparison operators (like Perl does with le and ge) it wouldn't be as bad, but
only using less than and greater makes it harder to infer what the user is
trying to accomplish.

Then to be consistent I guess I would go ahead and allow the booleans to be
compared also. I would have false come before true.

Finally, you could return nil if a comparison is used with one or two nil
values.

It appears that Python and Ruby both allow comparisons of strings. Python
allows comparison of booleans. It doesn't allow mixed types and doesn't allow
None to be compared to anything including itself. Ruby doesn't allow
comparisons between booleans. It also doesn't allow mixed types and doesn't
allow nil to be compared to anything including itself.

Challenge 2
-----------

Many languages define + such that if either operand is a string, the other is
converted to a string and the results are then concatenated. For example,
"scone" + 4 would yield scone4. Extend the code in visitBinaryExpr() to support
that.

Answer
------

Implemented.

Challenge 3
-----------

What happens right now if you divide a number by zero? What do you think should
happen? Justify your choice. How do other languages you know handle division by
zero and why do they make the choices they do?

Change the implementation in visitBinaryExpr() to detect and report a runtime
error for this case.

Answer
------

Currently if I divide zero by zero I get NaN and if I divide a non-zero number
by zero I get Infinity (or -Infinity depending on the sign of the dividend).
Not knowing as much about this as I probably should, I would probably prefer a
runtime error just because so many other languages do this. If I knew more
about the mathematics at play, then maybe I could push for a solution that
didn't involve a runtime error.

Interestingly, Java only gives Infinity when you are dividing floating point
numbers. Integer division will throw an exception.

I assume the reason languages throw errors when dividing by zero is because
this is not a typical thing to do and so the language designers are assuming that
the user has made some sort of mistake in even attempting this operation.

Looking online has shown that a language called Pony actually gives back zero
when dividing a number by zero. There was a lot of debate on whether or not
this is correct mathematically, but it seems there is evidence to suggest it
could in fact be valid.

Implemented.

