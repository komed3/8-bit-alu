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

## Shift register

| R | L | C | FNC |
|:-:|:-:|:-:|:---:|
| 1 | 0 | 0 | LSR |
| 0 | 1 | 0 | LSL |
| 1 | 0 | 1 | CSR |
| 0 | 1 | 1 | CSL |
