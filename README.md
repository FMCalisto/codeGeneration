# Postfix Machine Code Generation

### Topics

* Interpretation: syntax-directed and based on abstract syntax tree.

* Code generation: syntax-directed and based on abstract syntax tree.

The approach described here is based on generation from the intermediate representation in the form of a an abstract syntax tree formed by the nodes created during the parsing process.

The target machine is the Postfix engine described below.

## The Postfix Machine

SL0 - single stack, large stack, 0 operand machine.

Three special purpose registers: IP (instruction pointer), for jumps and function calls; FP (frame pointer), the basis of the frame pointer for each function; SP (stack pointer), keeps track of the top of the stack.

The stack grows in the direction of lower addresses.

Almost all operations use the stack as input and output (exceptions are PUSH and POP, for returning values from functions in accordance with CDecl), and instructions that use either immediate arguments or arguments in global memory (i.e., with explicit named addressing).

The [Postfix reference guide](https://www.l2f.inesc-id.pt/~david/w/pt/Postfix_Reference_Guide) (a.k.a. Appendix B) contains further details about the Postfix machine and its operations.

## Compiling and Running

To compile the Postfix code directly, pf2asm can be used:

```
pf2asm <program_name>.pf
```

```
yasm -felf <program_name>.asm
```

```
ld -o <program_name> <program_name>.o -lrts
```

```
./<program_name>
```

Please change the ```<program_name>``` for the real name of the program, for example:

```
pf2asm while.pf
```

```
yasm -felf while.asm
```

```
ld -o while while.o -lrts
```

```
./while
```
