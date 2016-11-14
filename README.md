Derivative Calculator
=====================

Methodology
-----------

1. Converts user input to [RPN](https://en.wikipedia.org/wiki/Reverse_Polish_notation)
2. Parses user input by + and - and performs differentiation, marking as necessary parts for chain rule.
3. Repeats and prints output. (Will likely need recursion for chain rule)

This is purely hypothetical at this point.

Checklist
---------

| Functionality                      | Status |
| ---                                | ---    |
| Compile user input to PN           | X      |
| Identify sections to differentiate | X      |
| Chain Rule                         | X      |
| Output                             | X      |

Sample Calculation
------------------

`1+sin(2x+1)`

RPN: `1 2 x * 1 + sin +`

1. Put `1 2 x` into stack.
2. See `*`, so unload `2 x *`
3. Differentiate `2 x *`, get `2 1 * 0 x +` using product rule
4. Loads special `OUTPUT` and next `1` into stack. Stack is now `1 OUTPUT 1`.
5. Sees `+`, so unloads last two.
6. Evaluates `1 +` as `0 +`. Output stack is now `2 1 * 0 x + 0 +`. Stack adds another OUTPUT `1 OUTPUT OUTPUT`.
7. Sees `sin`, so evaluates all evaluated. Adds `2 x * 1 + cos`, the derivative, to output. Output is now `2 1 * 0 x + 0 + 2 x * 1 + cos *`.
8. Sees final `+`, and adds on final `1` in input stack. Final answer is `0 2 1 * 0 x + 0 + 2 x * 1 + cos * +`.

Final: `0+(2*1+0*x)*cos(2*x+1)`
