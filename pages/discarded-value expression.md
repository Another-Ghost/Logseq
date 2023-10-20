### Discarded-value expressions
- A *discarded-value expression* is an expression that is used for its side-effects only. The value calculated from such expression is discarded. Such expressions include the full-expression of any [expression statement](https://en.cppreference.com/w/cpp/language/statements#Expression_statements), the left-hand operand of the built-in comma operator, or the operand of a cast-expression that casts to the type void.
- Array-to-pointer and function-to-pointer conversions are never applied to the value calculated by a discarded-value expression. The lvalue-to-rvalue conversion is applied if and only if the expression is a [volatile-qualified](https://en.cppreference.com/w/cpp/language/cv) glvalue and has one of the following forms (built-in meaning required, possibly parenthesized):
- id-expression,
- array subscript expression,
- class member access expression,
- indirection,
- pointer-to-member operation,
- conditional expression where both the second and the third operands are one of these expressions,
- comma expression where the right operand is one of these expressions.
- In addition, if the lvalue is of volatile-qualified class type, a volatile copy constructor is required to initialize the resulting rvalue temporary.
- | If the expression is a non-void prvalue (after any lvalue-to-rvalue conversion that might have taken place), [temporary materialization](https://en.cppreference.com/w/cpp/language/implicit_conversion#Temporary_materialization) occurs.Compilers may issue warnings when an expression other than cast to void discards a value declared `[[[nodiscard](https://en.cppreference.com/w/cpp/language/attributes/nodiscard)]]`. | (since C++17) |
- | ### Expression-equivalence
  A number of expressions e1, e2, ..., eN are *expression-equivalent* if
- they have the same effects;
- either they are all [constant subexpressions](https://en.cppreference.com/w/cpp/language/constant_expression#Constant_subexpression) or neither is;
- either they are all [noexcept](https://en.cppreference.com/w/cpp/language/noexcept_spec) or else neither is.
- e1 is *expression-equivalent to* e2 if and only if e1 and e2 are expression-equivalent (which means e2 is also expression-equivalent to e1). | (since C++20) |
- TODO 
  :LOGBOOK:
  CLOCK: [2023-10-20 Fri 15:02:33]--[2023-10-20 Fri 15:02:34] =>  00:00:01
  CLOCK: [2023-10-20 Fri 15:02:35]--[2023-10-20 Fri 15:02:35] =>  00:00:00
  CLOCK: [2023-10-20 Fri 15:02:36]--[2023-10-20 Fri 15:02:37] =>  00:00:01
  :END:
-