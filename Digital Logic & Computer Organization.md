## 1. What is Boolean Algebra?

Boolean Algebra is a branch of mathematics that deals with binary values:

- `1` → True
- `0` → False

It is mainly used to simplify digital circuits.

### Key Laws of Boolean Algebra

#### Idempotent Law
```math
A + A = A
```

```math
A \cdot A = A
```

#### Complement Law
```math
A + A' = 1
```

```math
A \cdot A' = 0
```

#### De Morgan's Theorem
```math
(A + B)' = A' \cdot B'
```

```math
(A \cdot B)' = A' + B'
```

---

## 2. What is a K-Map?

A **Karnaugh Map (K-Map)** is a graphical method used to simplify Boolean expressions.

### Features
- Uses **Gray Code**
- Adjacent cells differ by only one bit
- Groups are formed in powers of:

- 2
- 4
- 8
- 16

### Rules
1. Group only `1`s
2. Groups must be powers of 2
3. Larger groups provide more simplification
4. Remove changing variables

---

## 3. Types of Logic Gates

### Basic Gates

### AND Gate
Output becomes `1` only when all inputs are `1`.

| A | B | Output |
|---|---|---|
|0|0|0|
|0|1|0|
|1|0|0|
|1|1|1|

### OR Gate
Output becomes `1` if any input is `1`.

### NOT Gate
Inverts the input.

```math
Y = A'
```

---

### Universal Gates

#### NAND Gate
Can create all other logic gates.

```math
Y = (A \cdot B)'
```

#### NOR Gate
Also used to implement any logic circuit.

```math
Y = (A + B)'
```

---

### Special Gates

#### XOR Gate
Output is `1` when inputs differ.

```math
Y = A \oplus B
```

#### XNOR Gate
Output is `1` when inputs are same.

---

## 4. Combinational vs Sequential Circuits

| Feature | Combinational Circuit | Sequential Circuit |
|----------|----------------------|-------------------|
| Memory | No memory | Has memory |
| Output | Depends only on input | Depends on present + previous state |
| Clock | Not required | Required |
| Examples | Adders, MUX, DEMUX | Flip-Flops, Counters |

---

## 5. Multiplexer (MUX) and Demultiplexer (DEMUX)

### Multiplexer (MUX)

MUX means **Many-to-One**.

It selects one input from many inputs and sends it to one output.

Example:

```text
4 Inputs → 1 Output
```

Uses **Select Lines** to choose input.

---

### Demultiplexer (DEMUX)

DEMUX means **One-to-Many**.

It takes one input and sends it to one output line among many outputs.

Example:

```text
1 Input → 8 Outputs
```

Also uses select lines.

---

## 6. Half Adder vs Full Adder

### Half Adder

Adds only two bits.

Inputs:

- A
- B

Outputs:

### Sum

```math
S = A \oplus B
```

### Carry

```math
C = A \cdot B
```

Limitation:

- Cannot accept carry input.

---

### Full Adder

Adds three bits:

- A
- B
- Carry In (`Cin`)

Outputs:

### Sum

```math
S = A \oplus B \oplus Cin
```

### Carry Out

```math
Cout = AB + BCin + ACin
```

---

## 7. What is a Flip-Flop? Types of Flip-Flops

A Flip-Flop is a **1-bit memory device**.

It stores binary data and changes state using clock signals.

### Types

### SR Flip-Flop

S = Set

R = Reset

Invalid condition:

```text
S = 1
R = 1
```

---

### JK Flip-Flop

Improved version of SR Flip-Flop.

Condition:

```text
J = 1
K = 1
```

Result:

- Toggles continuously
- Causes Race Around Condition

---

### D Flip-Flop

Stores data directly.

```math
Q(next) = D
```

---

### T Flip-Flop

Used for toggling.

When:

```text
T = 1
```

Output changes state.

---

## 8. Asynchronous vs Synchronous Counters

| Feature | Asynchronous Counter | Synchronous Counter |
|----------|---------------------|--------------------|
| Clock Input | Applied only to first FF | Applied to all FFs |
| Speed | Slower | Faster |
| Delay | More propagation delay | Less delay |
| Example | Ripple Counter | Parallel Counter |

### Asynchronous Counter
- Output of one flip-flop becomes clock for next flip-flop
- Delay accumulates

### Synchronous Counter
- Same clock for all flip-flops
- State changes simultaneously

---

## 9. Cache Mapping Techniques

### 1. Direct Mapping

Each memory block maps to exactly one cache location.

Advantages:
- Simple
- Fast implementation

Disadvantage:
- High conflict misses
- Cache thrashing

---

### 2. Fully Associative Mapping

Memory block can go anywhere in cache.

Advantages:
- Flexible
- Less conflict

Disadvantages:
- Expensive
- Complex hardware

---

### 3. Set Associative Mapping

Cache divided into sets.

Memory block goes to:

```text
Specific Set → Any Line Inside Set
```

Advantages:
- Balanced performance
- Reduced conflicts

---

## 10. Von Neumann vs Harvard Architecture

| Feature | Von Neumann | Harvard |
|----------|-------------|----------|
| Memory | Shared | Separate |
| Bus | Single bus | Separate buses |
| Speed | Slower | Faster |
| Issue | Bottleneck | Parallel access |

### Von Neumann Architecture

- Same memory for instructions and data
- Causes:

```text
Von Neumann Bottleneck
```

---

### Harvard Architecture

- Separate instruction memory
- Separate data memory
- Allows parallel processing

---

# Scenario-Based Questions

---

## Scenario 1

### Question

A JK Flip-Flop is toggling continuously between `0` and `1` during one clock pulse when:

```text
J = 1
K = 1
```

What is the solution?

### Answer

This is called:

**Race Around Condition**

Fixes:

1. Use Edge Triggering
2. Use Master-Slave JK Flip-Flop
3. Reduce clock pulse width

---

## Scenario 2

### Question

Two memory blocks repeatedly replace each other inside cache and CPU performance becomes slow.

What happened?

### Answer

This is:

**Cache Thrashing**

Cause:

- Direct Mapping conflict

Solution:

Use:

- Set Associative Mapping

---

## Scenario 3

### Question

A TV remote sends a 3-bit signal and one video input must be routed to one of eight screens.

Which circuit is needed?

### Answer

Use:

```text
1-to-8 Demultiplexer (DEMUX)
```

Working:

- Video signal → Input
- 3-bit code → Select lines
- Output → Selected screen

---

# Quick Revision Table

| Topic | Key Point |
|--------|-----------|
| Boolean Algebra | Binary mathematics |
| K-Map | Simplifies expressions |
| Logic Gates | Basic building blocks |
| MUX | Many inputs → One output |
| DEMUX | One input → Many outputs |
| Half Adder | Adds 2 bits |
| Full Adder | Adds 3 bits |
| Flip-Flop | Memory element |
| Counter | Sequential circuit |
| Cache Mapping | Memory optimization |
| Von Neumann | Shared memory |
| Harvard | Separate memory |

---

## End of Notes
**Subject:** Digital Logic & Computer Organization (DLCO)

Prepared for quick revision and GitHub documentation.
