# Tools for code analysis and asm inspection

**Useful command line for inspecting assembly code generated for a function by gcc:**
```
gcc -ffunction-sections -c code.c -o code.o
readelf -S code.o | grep .text
objdump -w -d -M intel --section=.text.functionName code.o
```
* -ffunction-sections puts each function in code.c into its own code section in the ELF binary
* readelf -S dumps section header information, which is needed for the next command
* objdump: -w = use wide characters, don't trim; -d = disassemble, output assembly code;
-M intel = output intel syntax - you don't need this but I prefer intel syntax to AT&T
