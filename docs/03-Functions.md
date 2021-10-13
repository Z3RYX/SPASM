# Functions
Functions are self explanitory. They bring logic and functionality into SPASM.

There is a multitude of functions available and each follows the pattern of `opcode register [parameter]`<br>
The only functions to break this pattern are `END` and `NOP`, which take no register or parameter, and `LOD`, which takes multiple parameters.

In byte code, a function can have a modifier prefix. These are there to differentiate between function overloads. When working with mnemonics, these modifiers can be ignored, as the compiler will figure them out for you.

In the register column you will mostly find `REGx`. This means that any register can be used here. If only a specific size can be used, then it will say so (e.g. `REG16`). It may also use `REG16+` meaning a register with the size 16 or higher. Same goes for `REG16-`.

Parameters are shown as `ix` meaning an integer of the same size as the register. It may also show a specific size like `i32`, or `ix+` if the integer can be of the same size as the register or higher. Parameters can also be registers, which are explained in the paragraph above.

Parameters wrapped in [square brackets] are optional. This only really applies to the `LOD` function.

Here is a list of all available functions:
| Modifier | Opcode | Mnemonic | Register | Parameter | Description |
|---|---|---|---|---|---|
|| 00 | NOP |  |  | No Operation, literally does nothing |
|| 01 | END |  |  | Exits the program with a code of 0 |
| FF | 01 | END | REGx |  | Exits the program with the specified code from the stack |
|| 02 | PRN | REG16 |  | Prints a string<br>Top value on the register determines the string length |
|| 03 | PSH | REGx | ix | Pushes a value onto the register |
| FF | 03 | PSH | REGx | REGx | Pops a value from the parameter register on pushes it onto the first register |
|| 04 | POP | REGx |  | Discards the top value of a register |
|| 05 | EMT | REGx |  | Completely empties the entire register |
|| 06 | DUP | REGx |  | Duplicates the top value |
|| 07 | CPY | REGx | REGx | Duplicates the top value on the second register and pushes it onto the first |
|| 08 | CPR | REGx | REGx | Copies the entire second register onto the first |
|| 09 | LEN | REGx |  | Pushes the register's length (in values, not bytes) onto itself |
| FF | 09 | LEN | REGx | REGx | Pushes the length of the second register onto the first |
