# Cache_Simulator
Project Title:-Enhancement of Cache Performance using Adaptive Replacement Policy

Course:CDA5106 -Advanced Computer Architecture 
# Project Overview

Modern processors rely heavily on cache memory to reduce average memory access time. Traditional cache replacement policies like **LRU** and **FIFO** perform well under stable workloads but struggle with dynamically changing access patterns.

To address this limitation, this project proposes **Logical Cache Segmentation (LCS)** — a counter-based adaptive replacement policy that dynamically adjusts eviction likelihood using:
- **4-bit counters (0–15)**
- **Regions of Likeliness (ROLs)**

The simulator evaluates cache behavior using multiple workloads and performance metrics such as:
- Cache Hit Rate
- Cache Miss Rate
- Average Access Time (AAT)
