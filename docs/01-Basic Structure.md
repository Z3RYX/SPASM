# 01 - Basic SPASM Structure
A SPASM program consists of at most 3 sections:
- Data section (`.dat`)
  - This stores strings, numbers, etc.
- Register section (`.reg`)
  - Here you can preload the registers
- Text section (`.txt`)
  - This is where the executable code is

Out of these, only the text section is required. <br>
When executed, it first reads the data section, then the register section, and lastly the text section; no matter in which order they are put in the script.

To show this in an example, we are going to write a Hello World program, which stores the string "Hello World" in the data section, then retrieves it, and prints it to the console. <br>
(notice how the data section comes after the text section, but it won't matter since the data section is read before the text section is executed)
```
.txt
  DAT SSI 0x0         ; This loads the string from data with an offset of 0 into the register SSI, the last value on the stack indicates the length of the string
  PRN SSI             ; This prints the string by checking the length (last value on the stack), then printing that amount of characters

.dat
  s "Hello World\n"   ; We specify the data type with s, then specify the value; we also add a new line character at the end, since the print function doesn't do that itself
```

<hr>

### Data Section
The data section is simple.<br>
You specify a type to store, followed by the value of that type.<br>
In this table you can find all the types that can be stored.

| Mnemonic | Type | Example |
|----------|------|---------|
| i8 | 8-bit integer | `i8 0x80` |
| i16 | 16-bit integer | `i16 0x5401` |
| i32 | 32-bit integer | `i32 0x000c298a` |
| i64 | 64-bit integer | `i64 0x01c099f017baa409` |
| s | string | `s "Hello"` |

String is a special cases because when loading it, it will push all the characters as 16-bit integers onto the stack (right-to-left) and then push the string length.


### Register Section
In this section you can preload the registers with data, so that you won't need to do that in the code.<br>
This however won't work with strings, only integers.<br>
The register loading takes this simple structure: `register value [, value, ...]`<br>
In an example it would look like this:
```
.reg
  ASI16 0x1, 0x2  ; Loads 1 and 2 into ASI16
  SI16  0x30      ; Loads hex 30 (ASCII character '0') into SI16
  
.txt
  ADD ASI16 ASI16 ; Adds both values on ASI16 together (1+2)
  ADD SI16  ASI16 ; Adds result to hex 30 (0x30 + 3)
  PSH SI16  0x1   ; Pushes length of the string we want to print (1 character)
  PRN SI16        ; Prints our result
```


### Text Section
Here we find the executable code. Code in this section follows this basic structure: `operator register [parameter]`<br>
A list of operators and registers can be found in the later docs.

Each operation is on a separate line. You can't put multiple operations on the same line.


### Comments
Comments are easily added with the prefix: `;`<br>
Everything following that character will not be regarded by the program.

