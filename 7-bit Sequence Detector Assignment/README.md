# 🔍 Sequence Detector – RTL Design and Synthesis

A complete RTL design flow for a **7-bit Sequence Detector** using Verilog. This project covers FSM design, functional simulation, waveform analysis, synthesis using Yosys, gate-level netlist generation, and Gate-Level Simulation (GLS).

---

# 1. 📌 Introduction

This project focuses on designing and verifying a **7-bit sequence detector** using Verilog RTL.

The design uses a **Finite State Machine (FSM)** to monitor a serial input stream. Whenever the required sequence appears at the input, the output signal `detected` becomes high.

The complete design flow performed in this project is:

```text
RTL Design
    │
    ▼
Testbench
    │
    ▼
RTL Simulation
    │
    ▼
Waveform Analysis
    │
    ▼
Yosys Synthesis
    │
    ▼
Gate-Level Netlist
    │
    ▼
Gate-Level Simulation
```

---

# 2. 🎯 Target Sequence

The FSM is designed to detect the following **7-bit binary sequence**:

```text
0101001
```

The input is applied serially through the `din` signal.

Once all seven bits match the required pattern, the `detected` signal becomes `1`.

---

# 3. 🏗️ Design Overview

The main RTL module is:

```text
sequence_detector.v
```

The design contains the following main signals:

| Signal | Description |
|--------|-------------|
| `clk` | Clock input |
| `reset` | Reset signal |
| `din` | Serial input data |
| `detected` | Sequence detection output |
| `state` | Current FSM state |
| `next_state` | Next FSM state |

The design follows a synchronous FSM architecture.

---

# 4. 🔄 FSM Architecture

The FSM moves through different states depending on the incoming input bits.

Each state represents how much of the target sequence has been matched.

```text
Input Sequence Progress

Start
  │
  ▼
  0
  │
  ▼
  01
  │
  ▼
  010
  │
  ▼
  0101
  │
  ▼
  01010
  │
  ▼
  010100
  │
  ▼
0101001  ───► DETECTED = 1
```

The FSM contains **7 states** to track the sequence.

---

# 5. 💾 State Storage

The current FSM state is stored in the following register:

```verilog
reg [STATE_W-1:0] state;
```

The state width is defined as:

```verilog
localparam integer STATE_W = 3;
```

Since 3 bits can represent:

```text
2³ = 8 states
```

Three bits are sufficient to represent the required FSM states.

---

# 6. ⚙️ Next-State Logic

The combinational logic calculates the next state based on:

- Current FSM state
- Current input `din`

The logic is implemented using:

```verilog
always @(*)
```

Inside this block, a `case(state)` statement determines the transition to the next state.

```text
Current State + Input
          │
          ▼
   Next-State Logic
          │
          ▼
      next_state
```

---

# 7. 🔔 Output Generation

The `detected` output is generated using:

```verilog
next_detected
```

The output depends on:

```text
Current State + Input
```

Therefore, the sequence detector behaves as a **Mealy FSM**.

The output becomes high when the final bit of the sequence `0101001` is received.

---

# 8. ⏱️ Clock Operation

The clock is generated in the testbench using:

```verilog
always #4 clk = ~clk;
```

This produces the following clock characteristics:

| Parameter | Value |
|-----------|-------|
| Half Period | 4 ns |
| Full Period | 8 ns |
| Frequency | 125 MHz |

The FSM updates its state only on the positive edge of the clock.

---

# 9. 🔄 Reset Operation

The reset signal initializes the FSM.

When reset is active:

```verilog
state <= 'd0;
detected <= 1'b0;
```

The FSM returns to the initial state and the detection output becomes zero.

```text
RESET = 1
    │
    ▼
State = 0
Detected = 0
```

The testbench initially keeps reset active for **four clock cycles**.

---

# 10. 🧪 Testbench Design

The testbench is responsible for verifying the RTL functionality.

The main operations performed are:

- Clock generation
- Reset generation
- Serial input generation
- Detection monitoring
- Detection counting
- VCD waveform generation

The `drive_bit` task is used to apply one bit at a time.

```text
Input Bit
   │
   ▼
drive_bit()
   │
   ▼
Apply on Clock Cycle
   │
   ▼
Check detected Output
```

---

# 11. 🖥️ RTL Functional Simulation

The RTL design was simulated using **Icarus Verilog**.

The simulation flow was:

```text
sequence_detector.v
        +
      tb.v
        │
        ▼
    Icarus Verilog
        │
        ▼
    RTL Simulation
        │
        ▼
      dump.vcd
        │
        ▼
      GTKWave
```

The waveform was used to verify the behavior of:

- `clk`
- `reset`
- `din`
- `detected`
- `detection_count`

---

# 12. 📊 RTL Simulation Results

The RTL simulation successfully detected the target sequence:

```text
0101001
```

The observed results showed:

- Correct FSM state transitions
- Correct detection pulses
- No unexpected detections
- Total successful detections: **5**

The `detected` signal becomes high for one clock cycle whenever the complete sequence is found.

---

# 13. 🔧 RTL Synthesis Using Yosys

After successful RTL simulation, the design was synthesized using **Yosys**.

Synthesis converts the RTL description into a gate-level hardware implementation.

The general synthesis flow is:

```text
Verilog RTL
    │
    ▼
Read Verilog
    │
    ▼
Process FSM Logic
    │
    ▼
Logic Optimization
    │
    ▼
Technology Mapping
    │
    ▼
Gate-Level Netlist
```

The synthesis process completed successfully.

---

# 14. 📈 Synthesis Statistics

The synthesis report produced the following cell statistics:

| Cell Type | Count |
|-----------|------:|
| `$ANDNOT_` | 9 |
| `$DFF_P_` | 7 |
| `$NOR_` | 4 |
| `$ORNOT_` | 2 |
| `$OR_` | 3 |
| `$SDFF_PP0_` | 1 |
| **Total Cells** | **26** |

### Summary

```text
Sequential Cells     : 8
Combinational Cells  : 18
Total Cells          : 26
```

---

# 15. 🧩 Synthesized Netlist

After synthesis, the RTL design was converted into a gate-level netlist.

The synthesized design contains:

- D Flip-Flops
- AND-NOT gates
- NOR gates
- OR gates
- Reset flip-flops

The state register is implemented using multiple flip-flops because the FSM requires three state bits.

The synthesized netlist represents the actual hardware implementation generated from the RTL code.

---

# 16. 🔬 Gate-Level Simulation

The synthesized netlist was simulated using the same testbench.

The GLS flow was:

```text
Synthesized Netlist
        +
     Testbench
        │
        ▼
Gate-Level Simulation
        │
        ▼
    gls_dump.vcd
        │
        ▼
      GTKWave
```

The GLS waveform was compared with the RTL simulation waveform.

---

# 17. ✅ RTL vs GLS Comparison

The RTL and Gate-Level Simulation results were compared.

| Parameter | RTL | GLS |
|-----------|-----|-----|
| Target Sequence | `0101001` | `0101001` |
| Detection Output | Correct | Correct |
| Total Detections | 5 | 5 |
| Functional Behavior | Match | Match |

The logical detection behavior was preserved after synthesis.

---

# 18. 🏁 Final Conclusion

The **7-bit sequence detector for `0101001`** was successfully designed using Verilog RTL and verified using a custom testbench.

The design was successfully synthesized using **Yosys**, producing a gate-level implementation with **26 cells**. Gate-Level Simulation confirmed that the synthesized design preserved the RTL functionality, with both RTL and GLS producing **5 successful detection pulses**.

This project helped me understand the complete RTL design flow from:

```text
RTL Coding
    ↓
Functional Simulation
    ↓
Waveform Analysis
    ↓
Synthesis
    ↓
Netlist Generation
    ↓
Gate-Level Simulation
```

---

# 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Verilog | RTL Design |
| Icarus Verilog | Simulation |
| GTKWave | Waveform Analysis |
| Yosys | RTL Synthesis |
| GitHub | Project Documentation |

---

# 📚 Key Learning Outcomes

Through this project, I learned:

- Finite State Machine design
- Mealy FSM implementation
- Sequential and combinational RTL logic
- State encoding
- Clock and reset handling
- Verilog testbench development
- Functional simulation
- VCD waveform analysis
- RTL synthesis using Yosys
- Synthesis statistics interpretation
- Gate-level netlist generation
- Gate-Level Simulation
- RTL versus GLS verification
