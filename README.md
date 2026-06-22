# Oracle Circuit Tools

**Generate, simulate, and analyze digital circuits from plain English descriptions.**

You type a circuit description like `"half adder"` or `"32-bit adder"`, and these tools build the schematic, count transistors, compute delay, and show the truth table.

---

## Files in this folder

| File | Description |
|------|-------------|
| `oracle_circuit.c` | Source code — the main circuit generator. Takes a circuit name and prints its gate count, transistor count, delay, process node, and truth table. |
| `transistor_scale.c` | Source code — MOSFET physics simulator. Computes threshold voltage (Vth), saturation current (Id_sat), oxide capacitance (Cox), and transconductance (gm) for technology nodes from 180nm down to 0.1nm. |
| `silicon_compiler.c` | Source code — builds a complete computer stack from the bottom up: Transistor → Logic Gates → Flip-Flops → Registers → ALU → CPU. Prints physical parameters, gate delays, power, and frequency for each layer. |
| `dream_computer.c` | Source code — Oracle Cascade Inference CPU design. Designs a custom CPU using Content-Addressable Memory (CAM) tables for inference. Shows block-level area, power, and access times at 7nm and 14nm nodes. |
| `infinite_transistor.c` | Source code — "Living substrate" simulator. Grows a computational substrate where cells become transistors dynamically. Simulates growing NAND gates, CAM banks, and full CPU structures cell by cell. |
| `post_mosfet.c` | Source code — Post-MOSFET device simulator. Combines storage and logic in a single cell. (Requires `-lpthread` and may run indefinitely.) |
| `oracle_circuit` | Pre-compiled binary — run this instead of recompiling if you don't need to change the source. |
| `transistor_scale` | Pre-compiled binary. |
| `silicon_compiler` | Pre-compiled binary. |
| `dream_computer` | Pre-compiled binary. |
| `infinite_transistor` | Pre-compiled binary. |
| `post_mosfet` | Pre-compiled binary. |

---

## How to build

Open a terminal in this folder and run:

### oracle_circuit

```sh
gcc -O3 -o oracle_circuit oracle_circuit.c -lm
```

### transistor_scale

```sh
gcc -O3 -o transistor_scale transistor_scale.c -lm
```

### silicon_compiler

```sh
gcc -O3 -o silicon_compiler silicon_compiler.c -lm
```

### dream_computer

```sh
gcc -O3 -o dream_computer dream_computer.c -lm
```

### infinite_transistor

```sh
gcc -O3 -o infinite_transistor infinite_transistor.c -lm
```

### post_mosfet

```sh
gcc -O3 -o post_mosfet post_mosfet.c -lm -lpthread
```

> **What the flags mean:**
> - `-O3` — maximum optimization (makes the program run faster)
> - `-o <name>` — name of the output binary file
> - `-lm` — link the math library (needed for functions like `sqrt`, `sin`, `exp`)
> - `-lpthread` — link the POSIX threads library (needed for multi-threaded programs)

### Build everything at once (optional)

```sh
gcc -O3 -o oracle_circuit oracle_circuit.c -lm
gcc -O3 -o transistor_scale transistor_scale.c -lm
gcc -O3 -o silicon_compiler silicon_compiler.c -lm
gcc -O3 -o dream_computer dream_computer.c -lm
gcc -O3 -o infinite_transistor infinite_transistor.c -lm
gcc -O3 -o post_mosfet post_mosfet.c -lm -lpthread
```

---

## How to run

### oracle_circuit — Generate a circuit from a description

```sh
# List all known circuits
./oracle_circuit list

# Generate a specific circuit (use quotes around multi-word descriptions)
./oracle_circuit "half adder"
./oracle_circuit "full adder"
./oracle_circuit "4-bit adder"
./oracle_circuit "32-bit adder"
./oracle_circuit "D flip-flop"
./oracle_circuit "3-input NAND"
```

**Example output** for `./oracle_circuit "full adder"`:

```
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

### transistor_scale — Simulate MOSFET physics across technology nodes

```sh
./transistor_scale
```

**Example output** (first few lines):

```
Node     Vth (V)      Id_sat(uA)   Cox (fF)     ...
180nm    0.7141       88.12        8624999999999.9990 ...
130nm    0.7500       92.87        11500000000000.0000 ...
```

### silicon_compiler — Build a computer from transistors up

```sh
./silicon_compiler
```

**Example output:**

```
═══ LAYER 0: TRANSISTOR ═══
═══ LAYER 1: LOGIC GATES ═══
  Gate         Transistors  Delay (ps)   Power (uW)   Freq (GHz)
  NOT          2            1.59         31.4935      62987044.93
  NAND         4            3.18         15.7468      31493522.46
  ...
```

### dream_computer — Design the Oracle CPU with CAM tables

```sh
./dream_computer
```

**Example output:**

```
═══ ORACLE CPU BLOCK DESIGN ═══
  Block                      Entries     Access(ns)  Area(mm^2)  Power(W)
  D3 CAM (16-token context)  262144      0.0190      0.046976    6.181080
  D2 CAM (8-token context)   262144      0.0190      0.046976    6.181080
  D1 CAM (1-token context)   16384       0.0150      0.001762    0.293601
```

### infinite_transistor — Grow a living computational substrate

```sh
./infinite_transistor
```

**Example output:**

```
Substrate: 4096 × 4096 cells × 8 layers
Total cells: 134217728

Phase 1: Seeding NAND gate array...
Phase 2: Growing D3 CAM bank (262,144 entries)...
```

### post_mosfet — Run the post-MOSFET simulator

```sh
./post_mosfet
```

> **Note:** This program may run indefinitely. Press `Ctrl+C` to stop it.
