# Oracle Circuit Tools — Create Any Circuit from English

Type what you want. It builds the circuit.

## Tools

| Tool | What it does |
|------|-------------|
| `oracle_circuit` | "half adder" → transistor count, schematic, truth table, power |
| `transistor_scale` | MOSFET physics: Vth, Idsat from 180nm down to 0.1nm |
| `silicon_compiler` | Transistor → Gate → Flip-Flop → Register → ALU → CPU |
| `dream_computer` | Custom Oracle CPU design with CAM tables |
| `infinite_transistor` | Living substrate — cells that become transistors |
| `post_mosfet` | Storage + logic in one cell |

## Quick Start

```
gcc -O3 -o oracle_circuit oracle_circuit.c -lm
./oracle_circuit list
./oracle_circuit "half adder"
./oracle_circuit "32-bit adder"
```

## Example

```
$ ./oracle_circuit "full adder"

  Circuit: full adder
  Gates:        5
  Transistors:  42
  Delay:        28.58 ps
  Node:         14nm

  Truth Table:
  A B Cin | Cout Sum
  0 0 0   | 0    0
  0 0 1   | 0    1
  0 1 0   | 0    1
  0 1 1   | 1    0
  1 0 0   | 0    1
  1 0 1   | 1    0
  1 1 0   | 1    0
  1 1 1   | 1    1
```

## Building

All tools compile with:
```
gcc -O3 -mavx2 -march=native -o <tool> <tool>.c -lm
```
