# Cache_Simulator
Project Title:-Enhancement of Cache Performance using Adaptive Replacement Policy

Course:CDA5106 -Advanced Computer Architecture 

## Project Description

The goal of this project is to study how different cache replacement policies affect cache performance.  

Modern processors rely heavily on cache memory to reduce average memory access time. Traditional cache replacement policies like **LRU** and **FIFO** perform well under stable workloads but struggle with dynamically changing access patterns.

To address this limitation, this project proposes **Logical Cache Segmentation (LCS)** — a counter-based adaptive replacement policy that dynamically adjusts eviction likelihood using:
- **4-bit counters (0–15)**
- **Regions of Likeliness (ROLs)**

---

## Logical Cache Segmentation (LCS)

LCS assigns a **4-bit counter (range 0–15)** to each cache block and groups counter values into four **Regions of Likeliness (ROLs)**:

- Most Likely to be Replaced (0–1)
- Likely to be Replaced (2–5)
- Less Likely to be Replaced (6–11)
- Least Likely to be Replaced (12–15)

Replacement decisions are based on the lowest counter value.  
On cache hits, counters are promoted to higher regions, allowing frequently accessed data to remain longer in the cache.

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

Cache_Simulator/
├── traces/ # Input trace files
├── validation_runs/ # Validation outputs
├── SimulatorCacheDesign.cpp
├── Globals.h
├── Structs.h
├── Makefile
├── checkDiffChecker.sh
├── sim_cache # Generated executable
└── README.md


## Evaluation

The simulator was tested using multiple benchmark traces including:

vortex

compress

gcc

perl

go

Performance metrics collected include:

Cache hit rate

Cache miss rate

Average access time (AAT)

The results were used to compare LCS against LRU and FIFO under the same cache configurations.

