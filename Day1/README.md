# Day 1 – Environment Setup and RTL Workshop Initialization

## Module 1: Development Environment Setup

---

## Objective

The objective of Day 1 was to prepare the Linux development environment required for the RTL Design and Synthesis Workshop. This included installing essential tools, practicing Linux terminal commands, creating the workspace, and downloading the workshop repository from GitHub.

---

## Software Used

- Ubuntu Linux
- Git
- GitHub
- Icarus Verilog
- GTKWave

---

# Activity 1: Installing Icarus Verilog

## Objective

Icarus Verilog is an open-source Verilog compiler and simulator used to compile and simulate digital hardware designs.

### Installation Command

```bash
sudo apt install iverilog
```

### Verification Command

```bash
iverilog
```

### Learning Outcome

- Successfully installed Icarus Verilog.
- Verified that the simulator was working correctly.
- Prepared the system for Verilog compilation and simulation.

---

# Activity 2: Installing GTKWave

## Objective

GTKWave is a waveform viewer used to visualize the simulation output of Verilog designs. It helps in debugging and verifying digital circuits by displaying signal waveforms.

### Installation Command

```bash
sudo apt install gtkwave
```

### Verification Command

```bash
gtkwave
```

### Learning Outcome

- Successfully installed GTKWave.
- Verified the installation by launching the application.
- Understood the importance of waveform analysis in RTL design.

---

# Activity 3: Linux Terminal Navigation

During this session, several Linux commands were practiced to understand directory navigation and file management.

| Command | Description |
|---------|-------------|
| `cd /home` | Navigate to the home directory |
| `ls` | Display files and folders |
| `cd vsduser` | Enter the user home directory |
| `cd VSDSquadron_FM` | Open the workshop workspace |

---

# Activity 4: Cloning the Workshop Repository

The official RTL workshop repository was downloaded from GitHub using Git.

### Clone Command

```bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```

### Repository Verification

```bash
ls
```

The repository was successfully downloaded and stored inside the workspace directory.

---

# Activity 5: Exploring the Repository

The downloaded repository was opened and its contents were verified.

### Commands Used

```bash
cd sky130RTLDesignAndSynthesisWorkshop
```

```bash
ls
```

```bash
cd verilog_files
```

The **verilog_files** directory contains the Verilog source files used during the RTL workshop.

---

# Repository Structure

```text
sky130RTLDesignAndSynthesisWorkshop
│
├── DC_WORKSHOP
├── lib
├── my_lib
├── README.md
├── verilog_files
└── yosys_run.sh
```

---

# Commands Executed During Day 1

| S.No | Command | Purpose |
|------|---------|---------|
| 1 | `iverilog` | Check whether Icarus Verilog is installed |
| 2 | `sudo apt install iverilog` | Install Icarus Verilog |
| 3 | `iverilog` | Verify successful installation |
| 4 | `sudo apt install gtkwave` | Install GTKWave |
| 5 | `gtkwave` | Launch GTKWave |
| 6 | `cd /home` | Navigate to the home directory |
| 7 | `ls` | List files and folders |
| 8 | `cd vsduser` | Open the user home directory |
| 9 | `cd VSDSquadron_FM` | Enter the workshop workspace |
| 10 | `git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git` | Clone the workshop repository |
| 11 | `ls` | Verify the cloned repository |
| 12 | `cd sky130RTLDesignAndSynthesisWorkshop` | Open the workshop repository |
| 13 | `ls` | View repository contents |
| 14 | `cd verilog_files` | Navigate to the Verilog source files directory |

---

# Screenshots

Include the following screenshots inside the **screenshots** folder.

- Installing Icarus Verilog
- Verifying Icarus Verilog
- Installing GTKWave
- Launching GTKWave
- Linux Terminal Navigation
- Cloning the GitHub Repository
- Repository Contents
- Opening the **verilog_files** Directory

---

# Learning Outcomes

After completing Day 1, I was able to:

- Set up the RTL development environment on Ubuntu.
- Install and verify Icarus Verilog.
- Install and launch GTKWave.
- Practice essential Linux terminal commands.
- Clone a GitHub repository using Git.
- Explore the workshop repository structure.
- Prepare the environment for RTL simulation and synthesis experiments.

---

# Conclusion

Day 1 focused on building the development environment required for the RTL Design and Synthesis Workshop. The installation of Icarus Verilog and GTKWave, along with Linux terminal practice and GitHub repository setup, established a solid foundation for the practical RTL design activities in the upcoming modules.
