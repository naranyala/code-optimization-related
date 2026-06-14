# 🚀 Awesome Code Optimization, Compression & Algorithms

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

> *"The fastest code is the code that never runs. The second fastest is the code that aligns with the hardware."*

In modern software, performance is no longer just an afterthought—it is a core feature. Whether you are building high-frequency trading systems, low-latency game engines, or massively scalable web services, squeezing every microsecond out of your CPU and every byte out of your network is the difference between success and failure.

This repository is a definitive, zero-fluff manual taking you from high-level algorithmic theory straight down to bare-metal hardware execution. You will learn how to structure your logic to defeat the O(n) trap, why modern CPUs hate linked lists, and how to bypass the OS kernel to transfer data at ludicrous speeds. 

Whether you write Python, Go, C++, or Rust, the hardware underneath works the same. Let's make it go fast.

![Performance Engineering Banner](https://images.unsplash.com/photo-1555066931-4365d14bab8c?auto=format&fit=crop&w=1200&q=80)

---

## ⚡ Table of Contents

- [🧠 Foundations & Algorithms](#-foundations--algorithms)
- [🧩 Low-Level Mastery (The "Dark Arts")](#-low-level-mastery-the-dark-arts)
- [🏗️ Systems & Architecture](#-systems--architecture)
- [📦 Data Compression & Serialization](#-data-compression--serialization)
- [🌐 Domain Specific Performance](#-domain-specific-performance)
- [⚙️ Infrastructure & Build Pipeline](#-infrastructure--build-pipeline)
- [🛠️ Essential Tools Checklist](#-essential-tools-checklist)
- [📚 Curated Resources & Learning Path](#-curated-resources--learning-path)

---

## 🧠 Foundations & Algorithms

Performance begins with the right mental model and algorithmic choices.

### Core Philosophy
- **Profiling First**: *Premature optimization is the root of all evil.* Use tools to identify bottlenecks before changing code.
- **Big O Notation**: Understand the time and space complexity of your data structures.
- **Time-Space Trade-off**: Often, speed is bought with memory (e.g., Caching, Memoization).

### Algorithmic Strategies
- **Dynamic Programming**: Storing sub-problem results to avoid redundant calculations.
- **Divide and Conquer**: Breaking problems into smaller, parallelizable chunks.
- **Sliding Window / Two Pointers**: Efficiently processing linear data in O(n) time.

---

## 🧩 Low-Level Mastery (The "Dark Arts")

When high-level tweaks aren't enough, you must exploit the CPU's internal logic.

### Micro-Optimizations & Bit Twiddling
- **Bit Hacks**: Using binary logic for speed (e.g., `v & -v` to isolate the rightmost bit).
- **Branchless Programming**: Avoiding `if/else` in hot loops to prevent CPU pipeline stalls.
- **SIMD (Single Instruction, Multiple Data)**: Using AVX/NEON instructions to process multiple data points in one clock cycle.

### Data Layout & Memory
- **Alignment & Padding**: Sorting struct members by size (largest to smallest) to eliminate wasted memory.
- **Cache-Friendly Design**: Organizing data in memory to maximize L1/L2 cache hits (SoA vs. AoS).
- **Small Object Optimization (SOO)**: Storing small data inline to avoid heap allocation overhead.

---

## 🏗️ Systems & Architecture

Optimizing how your software interacts with the Operating System and Hardware.

### Memory Management
- **Arena Allocators**: Extremely fast memory management for per-frame or per-request data.
- **Pool Allocators**: Pre-allocated fixed-size blocks for objects of the same type.
- **High-Perf Malloc**: Drop-in replacements like [mimalloc](https://github.com/microsoft/mimalloc) or [jemalloc](https://github.com/jemalloc/jemalloc).

### Data Transfer & I/O
- **Zero-Copy**: Using `mmap()`, `sendfile()`, and `splice()` to move data without redundant kernel/user-space copies.
- **Kernel Bypass**: High-speed networking using **DPDK** or **XDP (eBPF)** to handle packets outside the standard OS stack.
- **DMA/RDMA**: Allowing hardware to access memory directly, bypassing the CPU entirely.

---

## 📦 Data Compression & Serialization

Reducing the size of data to save bandwidth and storage.

### Compression Algorithms
| Algorithm | Speed | Ratio | Best Use Case |
|-----------|-------|-------|---------------|
| **LZ4** | Blazing Fast | Low | Real-time / High-throughput |
| **Zstd** | Fast | High | General purpose (Log files, Databases) |
| **Brotli** | Slow (Comp) | Very High | Static web assets (HTML/JS) |

### High-Performance Serialization
- **[FlatBuffers](https://github.com/google/flatbuffers)**: Zero-copy access. Ideal for games and mobile.
- **[Cap'n Proto](https://github.com/capnproto/capnproto)**: Focuses on ultra-fast RPC and IPC.
- **[SBE](https://github.com/real-logic/simple-binary-encoding)**: The gold standard for High-Frequency Trading (HFT).

---

## 🌐 Domain Specific Performance

- **Web**: Tree-shaking, code splitting, and moving heavy logic to **Web Workers**.
- **Backend**: Connection pooling, asynchronous I/O, and efficient serialization.
- **Database**: Query plan analysis, indexing strategies, and denormalization.

---

## ⚙️ Infrastructure & Build Pipeline

Automated optimizations performed by your compiler and CI/CD.

- **LTO (Link-Time Optimization)**: Whole-program analysis to inline functions across different files.
- **PGO (Profile-Guided Optimization)**: Building your app using real-world usage data to layout the "hot" paths.
- **SIMD Auto-Vectorization**: Letting the compiler automatically turn loops into SIMD instructions.

---

## 🛠️ Essential Tools Checklist

| Category | Tools | Description |
|----------|-------|-------------|
| **Profiling** | `perf`, `Valgrind`, `GProf` | Bottleneck and memory leak detection. |
| **Benchmarking** | [hyperfine](https://github.com/sharkdp/hyperfine) | Statistical CLI benchmarking. |
| **Observability** | `eBPF`, `DTrace`, `Strace` | Deep system-level tracing. |
| **Visualization** | [FlameGraph](https://github.com/brendangregg/FlameGraph) | Visualizing CPU hotspots. |

---

## 📚 Curated Resources & Learning Path

### 📄 Seminal Papers
- **Huffman (1952)**: [A Method for the Construction of Minimum-Redundancy Codes](https://ieeexplore.ieee.org/document/4051119).
- **Ziv & Lempel (1977)**: [A Universal Algorithm for Sequential Data Compression](https://ieeexplore.ieee.org/document/1055714).

### 🎥 Must-Watch Talks
- **[Data-Oriented Design] (https://www.youtube.com/watch?v=rX0ItVEVjHc)** — Mike Acton (CppCon).
- **[Efficiency with Algorithms] (https://www.youtube.com/watch?v=fHNmRkzxHWs)** — Chandler Carruth (CppCon).

### ✍️ Blogs to Follow
- **[Cloudflare Blog] (https://blog.cloudflare.com/)** — Systems performance.
- **[Brendan Gregg] (https://www.brendangregg.com/blog/)** — Observability legend.

---

## 🤝 Contributing
Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

## 📄 License
To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work under [CC0](LICENSE).
