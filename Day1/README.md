# Day 1 – RTL Design and Simulation Basics

## Objective

The objective of Day 1 was to understand the basic RTL design flow, simulation process, synthesis flow, and the tools used for digital circuit design and verification.

---

## Tools Used

- Ubuntu Linux
- Git
- GitHub
- Icarus Verilog
- GTKWave
- Yosys

---

## Concepts Learned

- Introduction to RTL Design
- Verilog Design
- Testbench
- RTL Simulation
- Waveform Analysis
- RTL Synthesis
- Standard Cell Library
- Gate-Level Netlist

---



---

## Design

A **Design** is the Verilog code that implements the required digital functionality according to the given specifications.

---

## Testbench

A **Testbench** is used to apply different input test cases (stimulus) to the design and verify the generated outputs.

**Note:** A testbench does not have primary inputs or primary outputs.

---

## RTL Simulation

RTL simulation is performed to verify whether the design behaves according to the expected functionality.

**Simulation Tool:** Icarus Verilog

Simulation Flow:

```
Verilog Design
       │
       ▼
Icarus Verilog
       │
       ▼
VCD File
       │
       ▼
GTKWave
```

---

## RTL Synthesis

RTL synthesis converts the behavioral Verilog code into a gate-level netlist using a standard cell library.

**Synthesis Tool:** Yosys

Synthesis Flow:

```
RTL Design
      │
      ▼
Yosys
      │
      ▼
Gate-Level Netlist
```

---

## Commands Practiced

### Install Icarus Verilog

```bash
sudo apt install iverilog
```

### Install GTKWave

```bash
sudo apt install gtkwave
```

### Verify Installation

```bash
iverilog
gtkwave
```

### Navigate to Workspace

```bash
cd /home
cd vsduser
cd VSDSquadron_FM
```

### Clone Workshop Repository

```bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```

### Open Repository

```bash
cd sky130RTLDesignAndSynthesisWorkshop
cd verilog_files
ls
```

---

## Important Files

| File | Purpose |
|------|---------|
| `.v` | Verilog Design File |
| `tb_*.v` | Testbench File |
| `.vcd` | Simulation Waveform File |
| `.lib` | Standard Cell Library |
| Netlist | Output generated after synthesis |

---

## Learning Outcomes

- Understood the RTL design flow.
- Learned the purpose of Design and Testbench.
- Simulated Verilog designs using Icarus Verilog.
- Viewed waveforms using GTKWave.
- Learned RTL synthesis using Yosys.
- Understood the role of the Standard Cell Library and Gate-Level Netlist.

---

## Conclusion

Day 1 introduced the complete RTL design workflow, including simulation, waveform verification, and synthesis. It provided the foundation required for implementing and verifying digital circuits in the upcoming workshop sessions.
