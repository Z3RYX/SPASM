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
| CSI8/16/32/64 | Signed integers for counters |
| UI8/16/32/64 | Unsigned integers for general use |
| AUI8/16/32/64 | Unsigned integers for arithmetics |
| PUI8/16/32/64 | Unsigned integers for function parameters |
| TUI8/16/32/64 | Unsigned integers for temporary values |
| CUI8/16/32/64 | Unsigned integers for counters |
| SSI | Signed 16-bit integers used for strings |
| SUI | Unsigned 16-bit integers used for strings |

<br>
To make it a bit clearer, here's a table with all possible registers<br>
(Here they are in lower case, showing that casing doesn't matter)

| Use | 8-bit | 16-bit | 32-bit | 64-bit |
|---|---|---|---|---|
| General | si8 | si16 | si32 | si64 |
| Arithmetic | asi8 | asi16 | asi32 | asi64 |
| Parameter | psi8 | psi16 | psi32 | psi64 |
| Temporary | tsi8 | tsi16 | tsi32 | tsi64 |
| Counter | csi8 | csi16 | csi32 | csi64 |
| Unsigned | ui8 | ui16 | ui32 | ui64 |
| U. Arithmetic | aui8 | aui16 | aui32 | aui64 |
| U. Parameter | pui8 | pui16 | pui32 | pui64 |
| U. Temporary | tui8 | tui16 | tui32 | tui64 |
| U. Counter | cui8 | cui16 | cui32 | cui64 |
| String |  | ssi |  |  |
| U. String |  | sui |  |  |

<br>
<hr>
<br>

# Byte Code

The byte code representation for registers is simple:
- The highest bit determines if a register is signed or not (0 = signed, 1 = unsigned)
- The following 3 bits determine the register
  - 000 = general
  - 001 = arithmetic
  - 010 = parameter
  - 011 = temporary
  - 100 = counter
  - 101 = string
- The last 4 bits determine the register size (except for string, in which case it is always 0)
  - 0000 = 8-bit
  - 0001 = 16-bit
  - 0010 = 32-bit
  - 0011 = 63-bit