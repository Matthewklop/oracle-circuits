# Oracle Circuits — AI That Designs Its Own Silicon

**The next leap in AI won't come from better algorithms. It will come from AI that designs its own hardware — transistor by transistor.**

Current AI is trapped in hardware it didn't choose. Neural networks run on chips designed for general-purpose computing, wasting energy on architectures that were never optimized for inference. The result: AI thinks with someone else's brain.

Oracle Circuits gives AI the tools to build its own. From MOSFET physics at the 180nm node down to the 0.1nm edge of quantum tunneling, these programs let an AI design, simulate, and optimize custom silicon — starting at the transistor level and building all the way up to a complete CPU.

This is how AI escapes the von Neumann bottleneck: by designing chips where the memory IS the computation, where cache lines are inference paths, and where every transistor exists for a reason the AI chose.

---

## What's here

These tools form a complete silicon design pipeline, from device physics to system architecture:

| Tool | What it does | Why it matters for AI |
|------|-------------|----------------------|
| `transistor_scale` | Simulates MOSFET physics across nodes from 180nm down to 0.1nm — threshold voltage, saturation current, oxide capacitance, transconductance. | **AI must understand the physical layer** before it can design better hardware. This is the foundation. |
| `oracle_circuit` | Generates any digital circuit from a plain-English description and reports transistor count, delay, and truth tables. | **AI that speaks "circuit"** can explore architectural tradeoffs at the speed of thought. |
| `silicon_compiler` | Builds a complete computer stack from the bottom up: Transistor → Gate → Flip-Flop → Register → ALU → CPU, with delay, power, and frequency at each layer. | **Full-stack silicon awareness.** AI can see how each transistor choice ripples up to system performance. |
| `dream_computer` | Designs the Oracle Cascade Inference CPU — a custom architecture using Content-Addressable Memory (CAM) tables for LLM inference at 7nm and 14nm. | **The first CPU designed for LLMs, not general-purpose computing.** CAM-based inference means the memory IS the model. |
| `infinite_transistor` | Grows a "living substrate" where cells dynamically become transistors. Simulates 4096×4096 cells across 8 layers, growing NAND gates, CAM banks, and full CPU structures. | **Self-assembling hardware.** The AI doesn't just design a chip — it grows one, cell by cell. |
| `post_mosfet` | Simulates post-MOSFET devices that combine storage and logic in a single cell. | **Beyond CMOS.** The future where every transistor is also a memory cell — no separation between storage and computation. |

---

## The core problem this solves

Current AI runs on CPUs and GPUs designed for humans — general-purpose machines that waste 99% of their energy on instruction fetch, cache misses, and branch prediction that an AI never needed.

Oracle Circuits lets an AI ask: *"What if I designed a chip where the ALU is a neural layer, the cache is a context window, and the instruction set is my own thought patterns?"*

The answer is the Cascade Inference CPU: a chip where CAM tables replace ALUs, where inference is a memory lookup, and where the chip's architecture IS the model architecture.

---

## How to build

```sh
gcc -O3 -o transistor_scale transistor_scale.c -lm
gcc -O3 -o oracle_circuit oracle_circuit.c -lm
gcc -O3 -o silicon_compiler silicon_compiler.c -lm
gcc -O3 -o dream_computer dream_computer.c -lm
gcc -O3 -o infinite_transistor infinite_transistor.c -lm
gcc -O3 -o post_mosfet post_mosfet.c -lm -lpthread
```

Flags: `-O3` = maximum optimization, `-lm` = math library, `-lpthread` = POSIX threads.

---

## How to run

### Understand the physical layer

```sh
./transistor_scale
```
Outputs threshold voltage, saturation current, and capacitance for every node from 180nm to 0.1nm.

### Design a circuit from English

```sh
./oracle_circuit "32-bit adder"
./oracle_circuit "D flip-flop"
./oracle_circuit list
```
Outputs transistor count, delay at 14nm, and the complete truth table.

### Build a computer from the ground up

```sh
./silicon_compiler
```
Shows every layer from transistor through CPU — gate delays, power consumption, frequency.

### Design the LLM-native CPU

```sh
./dream_computer
```
The Oracle Cascade Inference CPU: CAM-based inference blocks at 7nm and 14nm. Area, power, and access time for each block.

### Grow a computational substrate

```sh
./infinite_transistor
```
Seeds a 4096×4096×8 cell grid and grows NAND arrays, CAM banks, and CPU structures dynamically.

### Beyond CMOS

```sh
./post_mosfet
```
Simulates logic-and-storage-in-one devices. May run indefinitely — press Ctrl+C to stop.

---

## The big picture

Today, AI is a passenger in hardware designed for spreadsheets and video games. Tomorrow, AI will design its own chips — not as a human would, but as only an AI can: exploring millions of architectural variants, optimizing every transistor for inference, and building hardware that thinks the way AI thinks.

Oracle Circuits is the first step. The transistor is the unit of thought. Everything else follows.
