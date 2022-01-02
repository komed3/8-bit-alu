# 8-bit arithmetic logic unit

Project to build an 8-bit arithmetic logic unit (ALU) consisting only of transistors. Further on, the construction of a transistor processor based on this ALU will follow.

## Description

The arithmetic-logic unit is a part of a CPU. This project is about building a controllable arithmetic unit with a 8-bit processing span (hex. ``00-FF``, dec. ``0-255``).

The ALU is built entirely from discrete transistors, resistors, diodes and LEDs. No integrated circuits are used. In its finished state, it will contain functions defined below and will be controlled by a CPU (also made of transistors) in the future.

The aim is to illustrate how computers calculate up to the execution of elementary programmes.

## Input

The inputs of the arithmetic-logic unit are the two 8-bit wide data words ``A`` and ``B``, and 8 control lines, defined below.

## Functions

| LS | RS | ~X | Cin | ~AND | ~C | ~B | ~A | FNC   |
|:--:|:--:|:--:|:---:|:----:|:--:|:--:|:--:|:-----:|
| 0  | 0  | 0  | 0   | 0    | 0  | 0  | 0  | ADD   |
| 0  | 0  | 0  | 0   | 0    | 0  | 0  | 1  | NOT A |
| 0  | 0  | 0  | 0   | 0    | 0  | 1  | 0  | NOT B |
| 0  | 0  | 0  | 0   | 0    | 1  | 0  | 0  | XOR   |
| 0  | 0  | 0  | 0   | 1    | 0  | 0  | 0  | OR    |
| 0  | 0  | 0  | 0   | 1    | 0  | 1  | 1  | NAND  |
| 0  | 0  | 0  | 1   | 0    | 0  | 0  | 0  | INC   |
| 0  | 0  | 0  | 1   | 0    | 0  | 1  | 0  | SUB   |
| 0  | 0  | 1  | 0   | 0    | 0  | 0  | 0  | NOT X |
| 0  | 0  | 1  | 0   | 0    | 1  | 0  | 0  | XNOR  |
| 0  | 0  | 1  | 0   | 1    | 0  | 0  | 0  | NOR   |
| 0  | 0  | 1  | 0   | 1    | 0  | 1  | 1  | AND   |
| 0  | 1  | 0  | 0   | 0    | 0  | 0  | 0  | LSR   |
| 1  | 0  | 0  | 0   | 0    | 0  | 0  | 0  | LSL   |

## Output

The output of the arithmetic-logic unit is the 8-bit wide data word ``X`` and the status register consisting of another 8 bits.

### Status register

| Flag | Name       | Description |
|:----:|------------|-------------|
| C    | Carry      | Enables numbers larger than a single word to be added/subtracted by carrying a binary digit from a less significant word to the least significant bit of a more significant word as needed. |
| V    | Overflow   | Indicates that the signed result of an operation is too large to fit in the register width using two's complement representation. |
| S    | Sign       | Indicates that the result of a mathematical operation is negative. |
| Z    | Zero       | Indicates that the result of an arithmetic or logical operation (or a load) was zero. |
| P    | Parity     | Indicates whether the number of set bits of the last result is even or odd (``Odd=1``). |
| H    | Half-carry | Indicates that a bit carry was produced between the nibbles (4-bit halves of a byte operand) as a result of the last arithmetic operation. |

### Magnitude comparator

Part of the ALU is the _magnitude comparator_. It is unaffected by arithmetic (or even shift) operations. It compares the input words ``A`` and ``B`` for equality and has two outputs that are included in the status register:

+ ``A=B`` Indicates when the entered words ``A`` and ``B`` are equal.
+ ``A>B`` Indicates when the entered word ``A`` is greather than ``B``.

If both outputs of the status register are ``0``, then ``A<B`` applies. No separate data wire is provided for this.
