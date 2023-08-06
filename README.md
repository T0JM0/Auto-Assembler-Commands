# Auto Assembler Commands

This repository provides a comprehensive list of all the Auto Assembler commands used in Cheat Engine, a powerful open-source memory scanner and debugger. Auto Assembler allows users to write custom scripts to manipulate and interact with the memory of a target process, making it a popular choice for game hacking and software reverse engineering tasks.

## Contents

1. [Introduction](#introduction)
2. [Commands List](#commands-list)
3. [Usage Examples](#usage-examples)
4. [Contribution](#contribution)
5. [Disclaimer](#disclaimer)

## Introduction

Cheat Engine's Auto Assembler feature empowers users with a range of powerful commands to interact with the memory of a target process. Understanding these commands is essential for effectively utilizing Cheat Engine's potential in game hacking and reverse engineering scenarios.

This repository aims to provide detailed information about each Auto Assembler command, along with usage examples, enabling both beginners and experienced users to harness the full capabilities of Cheat Engine's Auto Assembler.

## Commands List

Below is a list of Auto Assembler commands covered in this repository:

1. [aobScan](#aobscan)
2. [aobScanModule](#aobscanmodule)
3. [aobScanRegion](#aobscanregion)
4. [label](#label)
5. [alloc](#alloc)
6. [dealloc](#dealloc)
7. [globalAlloc](#globalalloc)
8. [kAlloc](#kalloc)
9. [fullAccess](#fullaccess)
10. [reassemble](#reassemble)
11. [readMem](#readmem)
12. [registerSymbol](#registersymbol)
13. [unregisterSymbol](#unregistersymbol)
14. [define](#define)
15. [assert](#assert)
16. [include](#include)
17. [createThread](#createthread)
18. [createThreadAndWait](#createthreadandwait)
19. [loadLibrary](#loadlibrary)
20. [loadBinary](#loadbinary)
21. [struct / endStruct](#struct--endstruct)
22. [luaCall](#luacall)
23. [{$LUA} / {$ASM}](#lua--asm)
24. [{$STRICT}](#strict)
25. [align](#align)
26. [{$TRY} / {$EXCEPT}](#try--except)
27. [{$LUACODE} / {$ASM}](#luacode--asm)
28. [{$CCODE} / {$ASM}](#ccode--asm)
29. [{$C} / {$ASM}](#c--asm)
30. [defineBytes](#definebytes)

## Usage Examples

### aobScan

**Description:** Scans the memory for the given array of bytes (wildcards are supported) and places a label at the first match.

**Usage:**
```autoit
aobScan(array_of_bytes, labelname)
```

### aobScanModule

**Description:** Scans a specific module (DLL) in the target process for the given array of bytes (wildcards are supported) and places a label at the first match.

**Usage:**
```autoit
aobScanModule(module_name, array_of_bytes, labelname)
```

### aobScanRegion

**Description:** Scans a specific memory range in the target process for the given array of bytes (wildcards are supported) and places a label at the first match.

**Usage:**
```autoit
aobScanRegion(start_address, end_address, array_of_bytes, labelname)
```

### label

**Description:** Enables the use of the specified `labelname` as an address in the script.

**Usage:**
```autoit
labelname:
```

### alloc

**Description:** Allocates a region of memory with a label that points to it. This allocated memory can be used to store data or code.

**Usage:**
```autoit
alloc(labelname, size)
```

### dealloc

**Description:** Deallocates a block of memory that was previously allocated using the `alloc` command.

**Usage:**
```autoit
dealloc(labelname)
```

### globalAlloc

**Description:** Allocates a certain amount of memory globally (usable across different parts of the script) and registers it with the specified name.

**Usage:**
```autoit
globalAlloc(labelname, size)
```

### kAlloc

**Description:** Kernel allocate. Allocates memory directly in the kernel space of the operating system.

**Usage:**
```autoit
kAlloc(labelname, size)
```

### fullAccess

**Description:** Makes a memory region readable, writable, and executable, which can be useful for executing code from that region.

**Usage:**
```autoit
fullAccess(labelname)
```

### reassemble

**Description:** Reassembles the given address, writing data at its declared location.

**Usage:**
```autoit
reassemble(address, data)
```

### readMem

**Description:** Reads a memory region and writes it at the location where this instruction is placed.

**Usage:**
```autoit
readMem(address, size)
```

### registerSymbol

**Description:** Adds the specified symbol to the user-defined symbol list. Symbols can be used to represent memory addresses or constants.

**Usage:**
```autoit
registerSymbol(symbol_name)
```

### unregisterSymbol

**Description:** Removes the specified symbol from the user-defined symbol list.

**Usage:**
```autoit
unregisterSymbol(symbol_name)
```

### define

**Description:** Replaces all occurrences of the specified token with the provided text.

**Usage:**
```autoit
define(token_name, replacement_text)
```

### assert

**Description:** Checks the memory address for the given bytes and throws an error if the bytes do not match.

**Usage:**
```autoit
assert(address, array_of_bytes)
```

### include

**Description:** Includes another Auto Assembler file at the specified location in the script.

**Usage:**
```autoit
include("filename")
```

### createThread

**Description:** Spawns a thread in the target process at the specified address.

**Usage:**
```autoit
createThread(address)
```

### createThreadAndWait

**Description:** Spawns a thread in the target process at the specified address and waits until it returns before continuing the script execution.

**Usage:**
```autoit
createThreadAndWait(address)
```

### loadLibrary

**Description:** Injects the specified DLL (Dynamic Link Library) into the target process.

**Usage:**
```autoit
loadLibrary("library_name.dll")
```

### loadBinary

**Description:** Loads a binary file at the specified address in the target process.

**Usage:**
```autoit
loadBinary("file_path", address)
```

### struct / endStruct

**Description:** Defines an internal structure in the Auto Assembler script.

**Usage:**
```autoit
struct(name)
... (Structure definition)
endStruct
```

### luaCall

**Description:** Executes the given Lua code within Cheat Engine's context.

**Usage:**
```autoit
luaCall("lua_code")
```

### {$LUA} / {$ASM}

**Description

:** Specifies the chosen parser for the following code block as either Lua or Assembler.

**Usage:**
```autoit
{$LUA}
... (Lua code)
{$ASM}
... (Assembler code)
```

### {$STRICT}

**Description:** Forces label declaration by throwing an error if a label is not declared before use.

**Usage:**
```autoit
{$STRICT}
```

### align

**Description:** Tells the assembler to align for a given byte size.

**Usage:**
```autoit
align(byte_size)
```

### {$TRY} / {$EXCEPT}

**Description:** Code between `{$TRY}` and `{$EXCEPT}` blocks will jump to the `{$EXCEPT}` part when an exception happens during execution.

**Usage:**
```autoit
{$TRY}
... (Code block to try)
{$EXCEPT}
... (Code block to execute on exception)
```

### {$LUACODE} / {$ASM}

**Description:** Execute the given Lua code inside Cheat Engine's context whenever the target process executes this code.

**Usage:**
```autoit
{$LUACODE}
... (Lua code)
{$ASM}
... (Assembler code)
```

### {$CCODE} / {$ASM}

**Description:** Execute the given C code inside the target process's context whenever the target process executes this code.

**Usage:**
```autoit
{$CCODE}
... (C code)
{$ASM}
... (Assembler code)
```

### {$C} / {$ASM}

**Description:** Compile the given code within the C block inside the target process.

**Usage:**
```autoit
{$C}
... (C code)
{$ASM}
... (Assembler code)
```

### defineBytes

**Description:** Defines a sequence of bytes with the specified label, which can be referenced and used in the script.

**Usage:**
```autoit
defineBytes(labelname, "array_of_bytes")
```

Please refer to each specific section above for more detailed information and usage examples of each Auto Assembler command.

## Contribution

Contributions to this repository are highly appreciated! If you have any suggestions, improvements, or additional information related to the Auto Assembler commands, please feel free to create pull requests or open issues. Let's collaborate to make this resource even more valuable for the Cheat Engine community.

## Disclaimer

Please note that while Cheat Engine and its Auto Assembler can be valuable tools for learning and experimentation, using them for unauthorized or illegal purposes may violate the terms of service of certain software or games. 
Always ensure that you have proper authorization before using these techniques.
The content provided in this repository is for educational and research purposes only. 
The authors and contributors are not responsible for any misuse or illegal activities undertaken using this information.
