# 02 - Registers
Registers are the main/only way to dynamically store values in memory. Each register is a stack of different integer sizes with no upper bound.

Below is a list of all registers and what their intended use is. The intended use is only a guideline, not a rule.<br>
Each register ends in a number (except for ssi and sui), this number shows the bit size of the integers it can hold. These are 8, 16, 32, and 64.<br>
To make the list easier to read, each register that has multiple bit sizes will be suffixed by `8/16/32/64`

| Name | Function |
|---|---|
| SI8/16/32/64 | Signed integers for general use |
| ASI8/16/32/64 | Signed integers for arithmetics |
| PSI8/16/32/64 | Signed integers for function parameters |
| TSI8/16/32/64 | Signed integers for temporary values |
| UI8/16/32/64 | Unsigned integers for general use |
| AUI8/16/32/64 | Unsigned integers for arithmetics |
| PUI8/16/32/64 | Unsigned integers for function parameters |
| TUI8/16/32/64 | Unsigned integers for temporary values |
| SSI | Signed 16-bit integers used for strings |
| SUI | Unsigned 16-bit integers used for strings |
