# 8-bit arithmetic logic unit

Project to build an 8-bit arithmetic logic unit (ALU) consisting only of transistors. Further on, the construction of a transistor processor based on this ALU will follow.

## Description

The arithmetic-logic unit is a part of a CPU. This project is about building a controllable arithmetic unit with a 8-bit processing span (hex. ``0-FF``, dec. ``0-255``).

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
