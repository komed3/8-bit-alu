# 8 Bit arithmetic-logic unit

Project to build an 8-bit arithmetic logic unit consisting only of transistors. Further on, the construction of a transistor processor based on this ALU will follow.

## Input

The 8-bit wide data words ``P`` and ``Q`` and the control lines ``F0..2``, ``M``, ``Cin``, ``R``, ``L`` and ``C`` are set as inputs.

### Basic functions

| F2 | F1 | F0 | FNC   |
|:--:|:--:|:--:|:-----:|
| 0  | 0  | 0  | ADD   |
| 0  | 0  | 1  | AND   |
| 0  | 1  | 0  | NOT P |
| 0  | 1  | 1  | NAND  |
| 1  | 0  | 0  | OR    |
| 1  | 0  | 1  | XOR   |
| 1  | 1  | 0  | NOR   |
| 1  | 1  | 1  | XNOR  |

### Additional functions

for ``F2..0 = 000``

* ``M=1`` Subtraction ``P-Q``
* ``Cin=1`` Increment ``P++``

### Shift functions

The shift functions can be performed independently of the previously used arithmetic calculations and do not affect the parity check (``P``) or the zero (``Z``), sign (``S``), half-carry (``H``) and overflow (``V``) flags.

| R | L | C | FNC |
|:-:|:-:|:-:|:---:|
| 1 | 0 | 0 | LSR |
| 0 | 1 | 0 | LSL |
| 1 | 0 | 1 | CSR |
| 0 | 1 | 1 | CSL |

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

Part of the ALU is the _Magnitude comparator_. It is unaffected by arithmetic (or even shift) operations. It compares the input words ``P`` and ``Q`` for equality and has two outputs that are included in the status register:

+ ``P=Q`` Indicates when the entered words ``P`` and ``Q`` are equal.
+ ``P>Q`` Indicates when the entered word ``P`` is greather than ``Q``.

If both outputs of the status register are ``0``, then ``P<Q`` applies. No separate data wire is provided for this.
