# 8-bit-alu

8 Bit arithmetic-logic unit

## Functions

### Basic functions

| F2 | F1 | F0 | FNC   |
|:--:|:--:|:--:|:-----:|
| 0  | 0  | 0  | ADD   |
| 0  | 0  | 1  | AND   |
| 0  | 1  | 0  | NOT A |
| 0  | 1  | 1  | NAND  |
| 1  | 0  | 0  | OR    |
| 1  | 0  | 1  | XOR   |
| 1  | 1  | 0  | NOR   |
| 1  | 1  | 1  | XNOR  |

### Additional functions

for ``F2..0 = 000``

* ``M=1`` – subtraction ``A-B``
* ``Cin=1`` – increment ``A++``

### Shift register

| R | L | C | FNC |
|:-:|:-:|:-:|:---:|
| 1 | 0 | 0 | LSR |
| 0 | 1 | 0 | LSL |
| 1 | 0 | 1 | CSR |
| 0 | 1 | 1 | CSL |

## Status register

| Flag | Name     | Description |
|:----:|----------|-------------|
|  C   | Carry    | Enables numbers larger than a single word to be added/subtracted by carrying a binary digit from a less significant word to the least significant bit of a more significant word as needed. |
|  V   | Overflow | Indicates that the signed result of an operation is too large to fit in the register width using two's complement representation. |
|  S   | Sign     | Indicates that the result of a mathematical operation is negative. |
|  Z   | Zero     | Indicates that the result of an arithmetic or logical operation (or a load) was zero. |
|  E   | A=B      | Indicates when the entered words A and B are equal. Unaffected by arithmetic operation. |
