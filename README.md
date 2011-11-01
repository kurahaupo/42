This small C program demonstrates the danger of improper use of the
C preprocessor.

A macro that's intended to be used in an expression context generally
needs to be aggressively parenthesized.  You should have parentheses
around each reference to a macro parameter, and around the entire definition.

The reason is that macro expansion works on sequences of tokens.
The C preprocessor doesn't deal with high-level C syntax.

In the example, the macro `SIX` expands to the token sequence `1 + 5`,
and the macro `NINE` expands to `8 + 1`.  If each of these expressions
were evaluated on its own, the results would be 6 and 9, respectively,
But when they'e combined in the expression `SIX * NINE`, the expansion is:

    1+5*8+1

which is equivalent to:

    1+(5*8)+1

or 42.

The program is also a reference to [a joke](http://en.wikipedia.org/wiki/Phrases_from_The_Hitchhiker%27s_Guide_to_the_Galaxy#Answer_to_the_Ultimate_Question_of_Life.2C_the_Universe.2C_and_Everything_.2842.29) in The Hitchhiker's Guide to the Galaxy, by Douglas Adams.

-- Keith Thompson <Keith.S.Thompson@gmail.com> Tue 2011-11-01
