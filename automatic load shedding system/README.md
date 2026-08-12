# Automatic Load Shedding System Using Verilog

## Overview

The Automatic Load Shedding System is an RTL-based digital controller
developed using Verilog HDL.

The system monitors available power and total load demand. When the
load demand exceeds the available power, the controller automatically
disconnects lower-priority loads to prevent system overload.

The system uses three load priorities:

1. Critical Load
2. Important Load
3. Non-Critical Load

Critical loads are always given the highest priority.

## Objectives

- Monitor available power.
- Monitor load demand.
- Prevent system overload.
- Automatically disconnect non-critical loads.
- Give priority to essential loads.
- Implement the control logic using Verilog HDL.
- Verify the design using a testbench.

## Load Priority

| Load | Priority | Example |
|------|----------|---------|
| Critical | Highest | Hospital/Emergency |
| Important | Medium | Office/Industrial |
| Non-Critical | Lowest | Lighting/General Loads |

## Working Principle

If available power is greater than or equal to total demand:

All loads remain connected.

If available power is insufficient:

1. Non-critical load is disconnected first.
2. If power is still insufficient, important load is disconnected.
3. Critical load is disconnected only when absolutely necessary.

## Inputs

| Input | Description |
|------|-------------|
| available_power | Available electrical power |
| critical_load | Critical load demand |
| important_load | Important load demand |
| noncritical_load | Non-critical load demand |

## Outputs

| Output | Description |
|--------|-------------|
| critical_enable | Critical load status |
| important_enable | Important load status |
| noncritical_enable | Non-critical load status |
| shed_noncritical | Non-critical load shedding |
| shed_important | Important load shedding |
| shed_critical | Critical load shedding |

## Technologies

- Verilog HDL
- RTL Design
- Digital Logic
- Icarus Verilog
- ModelSim
- Vivado

## Project Structure

automatic-load-shedding-system/

├── README.md
├── rtl/
│   └── automatic_load_shedding.v
├── testbench/
│   └── tb_automatic_load_shedding.v
└── output/
    └── expected_output.txt

## Simulation

Using Icarus Verilog:

```bash
iverilog -o load_shedding_sim rtl/automatic_load_shedding.v testbench/tb_automatic_load_shedding.v