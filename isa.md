TRISC (Tiny RISC) Instruction Set Architecture
==============================================

Instruction Formats
-------------------

### Register-Register (RR)
`cccc 00 sss ddd 00 cc`

- `cccc`: 4-bit opcode
- `00`: 2-bit format specifier
- `sss`: 3-bit source register (Rs)
- `ddd`: 3-bit destination register (Rd)
- `00`: 2-bit format specifier
- `cc`: 2-bit extended opcode

#### RR Instructions

- `0000` ADD
- `0001` SUB
- `0010` AND
- `0011` OR
- `0100` XOR
- `0101` LSL
- `0110` LSR
- `0111` ASR
- `1000` CMP
- `1001` MOV
- `1010` LDR b
- `1011` STR b
- `1100` LDR w
- `1101` STR w
- `1110` LDR d
- `1111` STR d

### Register-Immediate (RI)

`cccc 01 ddd iiiiiii`

- `cccc`: 4-bit opcode
- `01`: 2-bit format specifier
- `ddd`: 3-bit destination register (Rd)
- `iiiiiii`: 7-bit signed immediate value

### Branch (B)

`cccc 10 oooooooooo`

- `cccc`: 4-bit opcode
- `10`: 2-bit format specifier
- `oooooooooo`: 10-bit signed immediate value

Positive Form	Negative Form
Mnemonic	Description	Boolean Expression	Mnemonic	Description	Boolean Expression
Unconditional
bra	Branch Always	1	brn	Branch Never	0
Single Condition Code
bcs	Branch Carry Set	C = 1	bcc	Branch Carry Clear	C = 0
bmi	Branch Minus	N = 1	bpl	Branch Plus	N = 0
bvs	Branch oVerflow Set	V = 1	bvc	Branch oVerflow Clear	V = 0
beq	Branch Equal (to 0)	Z = 1	bne	Branch Not Equal (to 0)	Z = 0
Signed Branches
blt	Branch Less Than	N ^ V = 1	bge	Branch Greater Than or Equal	N ^ V = 0
ble	Branch Less Than or Equal	(N ^ V) | Z = 1	bgt	Branch Greater Than	(N ^ V) | Z = 0
Unsigned Branches
blo	Branch Lower	C = 1	bhs	Branch Greater Than or Equal	C = 0
bls	Branch Less Than or Equal	C | Z = 1	bhi	Branch Higher	C | Z = 0

### Register-Register-Register (RRR)

`cccc 11 sss ddd nnn c`

- `cccc`: 4-bit opcode
- `11`: 2-bit format specifier
- `sss`: 3-bit source register (Rs)
- `ddd`: 3-bit destination register (Rd)
- `nnn`: 3-bit register (Rn)
- `c`: 1-bit extended opcode
