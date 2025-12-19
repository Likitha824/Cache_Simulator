# Cache_Simulator
Project Title:-Enhancement of Cache Performance using Adaptive Replacement Policy

Course:CDA5106 -Advanced Computer Architecture 

## Overview

This project implements a cache simulator to study how different cache replacement policies affect cache performance. 
The simulator processes benchmark memory access traces and evaluates cache behavior under various cache configurations.

Standard replacement policies such as **LRU** and **FIFO** are implemented and compared with an adaptive policy called **Logical Cache Segmentation (LCS)**. 
Cache performance is analyzed using metrics such as hit rate, miss rate, and average access time (AAT).

---

## Logical Cache Segmentation (LCS)

Logical Cache Segmentation (LCS) is a counter-based replacement policy.

- Each cache block maintains a **4-bit counter (0–15)**
- Counter values are grouped into four **Regions of Likeliness (ROLs)**:
  - 0–1: Most Likely to be Replaced
  - 2–5: Likely to be Replaced
  - 6–11: Less Likely to be Replaced
  - 12–15: Least Likely to be Replaced
- On a cache miss, the block with the **lowest counter value** is selected for replacement
- On a cache hit, the block’s counter is promoted to higher regions, allowing frequently accessed data to remain longer in the cache (improves Priority)
---

## Features

- Trace-driven L1 cache simulation
- Supports multiple replacement policies:
  - FIFO
  - LRU
  - OPTIMAL (for comparison)
  - Logical Cache Segmentation (LCS)
- Configurable cache parameters:
  - Cache size
  - Block size
  - Associativity
- Implements write-back and write-allocate policies
- Generates cache performance statistics

---

## Repository Structure

```
Cache_Simulator/
├── traces/     # Input trace files
├── validation_runs/     # Validation outputs
├── Globals.h     # Global definitions and constants
├── Structs.h    # Data structures used in the simulator
├── SimulatorCacheDesign.cpp   # Main cache simulator implementation
├── Makefile     # Build instructions
├── checkDiffChecker.sh   # Script for output verification
├── annotated-report.pdf    # Detailed project report
└── README.md    # Project documentation
```

## Getting Started

### Prerequisites

- C++ compiler (g++)
- GNU Make

---
### Compilation

g++ SimulatorCacheDesign.cpp -o cache_simulator

### Running the Simulator

Run the simulator by providing a trace file as input:

./sim_cache <trace_file>

Example:

./sim_cache traces/gcc.trace


---
## Evaluation Summary

The simulator was evaluated using multiple benchmark traces, including:
- vortex
- compress
- gcc
- perl
- go

Results were used to compare LCS against LRU and FIFO under identical cache configurations.  
Observed trends showed that LCS reduced miss rates for some workloads and performed comparably to LRU for others. Detailed results and graphs are documented in the project report.

---

## Project Highlights

- Implemented FIFO, LRU, and Logical Cache Segmentation (LCS) replacement policies
- Evaluated cache performance using hit rate, miss rate, and average access time (AAT)
- Observed lower miss rates for LCS compared to FIFO on multiple benchmark traces
- Found LCS performance to be comparable to LRU for workloads such as perl and gcc

---
## Limitations

- LCS introduces additional storage overhead due to per-block counters
- Performance depends on workload characteristics and cache configuration
---
## References 

The complete list of references used in this project is available in the project report.

- Kharbutli & Solihin, Counter-Based Cache Replacement, IEEE
- Reineke & Grund, Cache Replacement Sensitivity
- Odule & Osinuga, Self-Adjusting Cache Replacement
