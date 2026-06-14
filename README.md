# 🚀 Awesome Code Optimization, Compression & Algorithms

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

> *"The fastest code is the code that never runs. The second fastest is the code that aligns with the hardware."*

A definitive compendium of performance engineering resources, bridging the gap between high-level algorithmic theory and low-level hardware exploitation. This guide provides a multi-layered approach to optimization—spanning cache-friendly architecture, zero-copy systems, kernel-bypass networking, and advanced compiler-driven optimizations—empowering developers to build software that is inherently fast, lean, and scalable.

---

## ⚡ Table of Contents

- [🧠 Algorithms & Data Structures](#-algorithms--data-structures)
- [🧩 Low-Level Mastery & SIMD](#-low-level-mastery--simd)
- [🏗️ Memory Management & Allocators](#-memory-management--allocators)
- [🚀 Networking & Data Transfer](#-networking--data-transfer)
- [📦 Data Compression](#-data-compression)
- [💽 Serialization & Storage Formats](#-serialization--storage-formats)
- [⚙️ High-Performance Databases & Caching](#-high-performance-databases--caching)
- [🛠️ Profiling, Tracing & Observability](#-profiling-tracing--observability)
- [📚 Curated Resources & Learning Path](#-curated-resources--learning-path)

---

## 🧠 Algorithms & Data Structures

Performance begins with the right mental model and algorithmic choices. Time-Space trade-offs (like memoization) and understanding Big O notation are fundamental.

### Open-Source Standard Libraries
When standard libraries aren't fast enough, the open-source community provides highly optimized drop-in replacements.
- **[Abseil](https://abseil.io/)**: Google's open-source C++ library, heavily optimized for performance.
- **[Folly](https://github.com/facebook/folly)**: Facebook's open-source C++ library containing incredibly fast data structures (e.g., `ConcurrentHashMap`).
- **[JCTools](https://github.com/JCTools/JCTools)**: High-performance concurrent data structures for the JVM.
- **[Boost](https://www.boost.org/)**: The legendary peer-reviewed C++ library collection.
- **[Guava](https://github.com/google/guava)**: Google's core libraries for Java, including highly optimized caching.

---

## 🧩 Low-Level Mastery & SIMD

When high-level tweaks aren't enough, you must exploit the CPU's internal logic. This includes Bit Hacks, avoiding branch mispredictions, and utilizing **SIMD** (Single Instruction, Multiple Data).

### Open-Source SIMD & Math Libraries
- **[simdjson](https://github.com/simdjson/simdjson)**: Parsing gigabytes of JSON per second using SIMD instructions.
- **[Google Highway](https://github.com/google/highway)**: A C++ library providing performance-portable SIMD intrinsics.
- **[Intel MKL / oneMKL](https://www.intel.com/content/www/us/en/developer/tools/oneapi/onemath.html)**: Extremely fast math routines (though primarily Intel-focused, widely used in open-source HPC).
- **[RoaringBitmap](https://github.com/RoaringBitmap/RoaringBitmap)**: Compressed bitmaps used in almost every major open-source database for high-speed set intersections.

---

## 🏗️ Memory Management & Allocators

Heap allocation is slow. Using custom allocators (Arena, Pool) or dropping in a high-performance standard allocator replacement can yield instant 10-20% speedups.

### Open-Source Allocators
- **[mimalloc](https://github.com/microsoft/mimalloc)**: Microsoft's compact, extremely fast general-purpose allocator.
- **[jemalloc](https://github.com/jemalloc/jemalloc)**: Created for FreeBSD, heavily used by Meta, excellent at avoiding memory fragmentation in multithreaded systems.
- **[tcmalloc](https://github.com/google/tcmalloc)**: Google's Thread-Caching Malloc, highly optimized for C++.
- **[snmalloc](https://github.com/microsoft/snmalloc)**: Microsoft's message-passing based allocator designed for high-concurrency systems.
- **[rpmalloc](https://github.com/mjansson/rpmalloc)**: A lock-free, thread-caching allocator written in C.

---

## 🚀 Networking & Data Transfer

Moving data across the network requires bypassing the kernel for ultimate speed (Zero-Copy, Kernel Bypass, RDMA).

### Open-Source Networking Frameworks
- **[DPDK (Data Plane Development Kit)](https://www.dpdk.org/)**: Bypasses the Linux kernel's networking stack entirely to handle millions of packets per second.
- **[eBPF / XDP](https://ebpf.io/)**: Allows running sandboxed programs within the Linux kernel to filter and redirect packets at lightning speed.
- **[io_uring](https://kernel.dk/io_uring.pdf)**: The modern Linux kernel asynchronous I/O API, vastly outperforming `epoll`.
- **[Seastar](https://seastar.io/)**: An advanced C++ framework for high-performance asynchronous applications, used to build ScyllaDB.

---

## 📦 Data Compression

Compression reduces data size to save network bandwidth and disk I/O, often speeding up systems despite the CPU cost.

### Open-Source Compression Algorithms
| Algorithm | Organization | Speed | Ratio | Best Use Case |
|-----------|--------------|-------|-------|---------------|
| **[LZ4](https://github.com/lz4/lz4)** | Yann Collet | Blazing Fast | Low | Real-time compression, databases. |
| **[Zstandard (zstd)](https://github.com/facebook/zstd)**| Meta | Fast | High | General purpose, log files. |
| **[Brotli](https://github.com/google/brotli)** | Google | Slow (Comp) | Very High | Static web assets (HTML/JS/CSS). |
| **[Snappy](https://github.com/google/snappy)** | Google | Very Fast | Low | MapReduce, BigTable, internal RPCs. |
| **[xz (LZMA)](https://tukaani.org/xz/)** | Community | Very Slow | Maximum | Archiving release binaries. |

---

## 💽 Serialization & Storage Formats

Parsing strings (JSON/XML) is a massive bottleneck. Use dense binary or zero-copy formats.

### Open-Source Serialization
- **[FlatBuffers](https://github.com/google/flatbuffers)** (Google): Zero-copy deserialization. Data maps directly to memory. Ideal for mobile and games.
- **[Cap'n Proto](https://capnproto.org/)**: Focuses on "time travel" (zero-copy) and ultra-fast RPC.
- **[Protocol Buffers (Protobuf)](https://github.com/protocolbuffers/protobuf)** (Google): Dense binary format, widely used in gRPC.
- **[MessagePack](https://msgpack.org/)**: "It's like JSON, but fast and small."
- **[SBE (Simple Binary Encoding)](https://github.com/real-logic/simple-binary-encoding)**: The standard for High-Frequency Trading (HFT) messaging.

### Open-Source Analytical Storage (Columnar)
- **[Apache Arrow](https://arrow.apache.org/)**: The gold standard for zero-copy, in-memory columnar data sharing across languages (Python, Rust, C++).
- **[Apache Parquet](https://parquet.apache.org/)**: Disk-based columnar storage for Hadoop/Spark.
- **[Apache ORC](https://orc.apache.org/)**: Highly optimized columnar storage format for Hive.

---

## ⚙️ High-Performance Databases & Caching

Choosing a data store explicitly engineered for performance over generic solutions.

### Open-Source High-Perf Data Stores
- **[ScyllaDB](https://www.scylladb.com/)**: A C++ rewrite of Cassandra, utilizing the Seastar framework to achieve millions of operations per second per node.
- **[ClickHouse](https://clickhouse.com/)**: Blazing fast open-source columnar database for real-time analytics (OLAP).
- **[Dragonfly](https://dragonflydb.io/)**: A modern, multi-threaded drop-in replacement for Redis written in C++, utilizing shared-nothing architecture.
- **[VictoriaMetrics](https://victoriametrics.com/)**: High-performance, cost-effective time-series database.

---

## 🛠️ Profiling, Tracing & Observability

You cannot optimize what you cannot measure. 

### Open-Source Profiling Tools
- **[perf](https://perf.wiki.kernel.org/)**: The official Linux profiler for CPU and hardware counters.
- **[hyperfine](https://github.com/sharkdp/hyperfine)**: A command-line benchmarking tool written in Rust with statistical analysis.
- **[BCC / bpftrace](https://github.com/iovisor/bcc)**: Powerful eBPF-based tools for deep kernel and application tracing.
- **[FlameGraph](https://github.com/brendangregg/FlameGraph)**: Brendan Gregg's iconic tool for visualizing CPU hotspots.
- **[Tracy Profiler](https://github.com/wolfpld/tracy)**: A real-time, nanosecond resolution frame profiler for games and C++ apps.
- **[Pprof](https://github.com/google/pprof)**: A tool for visualization and analysis of profiling data (heavily used in the Go ecosystem).
- **[Valgrind](https://valgrind.org/)**: Essential for memory leak detection and profiling (Cachegrind/Callgrind).

---

## 📚 Curated Resources & Learning Path

### 📄 Seminal Papers
- **Huffman (1952)**: [A Method for the Construction of Minimum-Redundancy Codes](https://ieeexplore.ieee.org/document/4051119).
- **Ziv & Lempel (1977)**: [A Universal Algorithm for Sequential Data Compression](https://ieeexplore.ieee.org/document/1055714).

### 🎥 Must-Watch Talks
- **[Data-Oriented Design](https://www.youtube.com/watch?v=rX0ItVEVjHc)** — Mike Acton (CppCon).
- **[Efficiency with Algorithms](https://www.youtube.com/watch?v=fHNmRkzxHWs)** — Chandler Carruth (CppCon).

### ✍️ Blogs to Follow
- **[Cloudflare Blog](https://blog.cloudflare.com/)** — Systems performance and networking at massive scale.
- **[Brendan Gregg](https://www.brendangregg.com/blog/)** — Observability and Linux performance legend.
- **[Dan Luu](https://danluu.com/)** — Hardware latency and architecture.

---

## 🤝 Contributing
Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

## 📄 License
To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work under [CC0](LICENSE).
