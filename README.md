# 🚀 Awesome Code Optimization, Compression & Algorithms

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

> *"The fastest code is the code that never runs. The second fastest is the code that aligns with the hardware."*

A definitive compendium of performance engineering resources, bridging the gap between high-level algorithmic theory and low-level hardware exploitation. This guide provides a multi-layered approach to optimization—spanning cache-friendly architecture, highly efficient data transfer systems, kernel-bypass networking, and advanced compiler-driven optimizations—empowering developers to build software that is inherently fast, lean, and scalable.

---

## ⚡ Table of Contents

- [🧠 Algorithms & Data Structures](#-algorithms--data-structures)
- [🧩 Low-Level Mastery (SIMD & Bits)](#-low-level-mastery-simd--bits)
- [🏗️ Systems & Architecture](#-systems--architecture)
- [📦 Compression & Serialization](#-compression--serialization)
- [🌐 Networking & Async I/O](#-networking--async-io)
- [📊 Language-Specific Champions](#-language-specific-champions)
- [⚙️ The Build Pipeline](#-the-build-pipeline)
- [🛠️ Tooling & Observability](#-tooling--observability)
- [📚 Curated Resources](#-curated-resources)

---

## 🧠 Algorithms & Data Structures

- **[Intel oneTBB](https://github.com/oneapi-src/oneTBB)** (C++): Industry standard for task-based parallelism.
- **[Abseil](https://github.com/abseil/abseil-cpp)** (C++): Google's optimized hash maps (`Swiss Tables`).
- **[Folly](https://github.com/facebook/folly)** (C++): Facebook’s library of high-performance concurrent primitives.
- **[Crossbeam](https://github.com/crossbeam-rs/crossbeam)** (Rust): Gold standard for lock-free data structures in Rust.
- **[JCTools](https://github.com/JCTools/JCTools)** (Java): Specialized concurrent queues that outperform `java.util.concurrent`.

---

## 🧩 Low-Level Mastery (SIMD & Bits)

- **[simdjson](https://github.com/simdjson/simdjson)**: Gigabytes of JSON parsing per second via SIMD.
- **[Highway](https://github.com/google/highway)**: Portable C++ library for SIMD (AVX, NEON, SVE).
- **[StringZilla](https://github.com/ashvardanian/StringZilla)**: Ultra-fast substring search and sorting using SIMD.
- **[BitTwiddling Hacks](https://graphics.stanford.edu/~seander/bithacks.html)**: The definitive collection of bit-level tricks.

---

## 🏗️ Systems & Architecture

- **[mimalloc](https://github.com/microsoft/mimalloc)**: Microsoft's compact, high-performance allocator.
- **[jemalloc](https://github.com/jemalloc/jemalloc)**: Scalable concurrency-focused allocator.
- **[RocksDB](https://github.com/facebook/rocksdb)**: High-performance persistent key-value store.

---

## 📦 Compression & Serialization

- **[Zstandard (Zstd)](https://github.com/facebook/zstd)**: High compression ratio + high speed.
- **[LZ4](https://github.com/lz4/lz4)**: Blazing fast compression, limited only by RAM speed.
- **[FlatBuffers](https://github.com/google/flatbuffers)**: Direct memory access without decoding (C++, Rust, Go, Java).
- **[MemoryPack](https://github.com/Cysharp/MemoryPack)** (.NET): Ultra-fast minimal-overhead binary serializer for C#.
- **[rkyv](https://github.com/rkyv/rkyv)** (Rust): Direct memory serialization for the Rust ecosystem.

---

## 🌐 Networking & Async I/O

- **[DPDK](https://github.com/DPDK/dpdk)**: Kernel bypass for ultra-fast packet processing.
- **[Aeron](https://github.com/real-logic/aeron)** (Java/C++): Low-latency UDP and IPC messaging (HFT standard).
- **[liburing](https://github.com/axboe/liburing)**: The interface for Linux's `io_uring`.
- **[Kestrel](https://github.com/dotnet/aspnetcore)** (.NET): One of the fastest web servers in the world.
- **[Gnet](https://github.com/panjf2000/gnet)** (Go): Lightweight, non-blocking networking for Go.

---

## 📊 Language-Specific Champions

### ⚙️ C & C++ (The Bare Metal)
- **[Boost](https://www.boost.org/)**: The definitive, peer-reviewed collection of highly optimized libraries.
- **[Folly](https://github.com/facebook/folly)**: Facebook’s open-source library of performance concurrent primitives.
- **[Abseil](https://github.com/abseil/abseil-cpp)**: Google's collection including `Swiss Tables` (ultra-fast hash maps).
- **Sanitizers (`ASan`, `TSan`)**: Essential compiler tooling for catching memory leaks and race conditions safely.

### 🦀 Rust (Safe Speed)
- **[Rayon](https://github.com/rayon-rs/rayon)**: Data-parallelism library that easily converts iterators to parallel execution.
- **[Crossbeam](https://github.com/crossbeam-rs/crossbeam)**: The gold standard for lock-free data structures and concurrency.
- **[Tokio](https://github.com/tokio-rs/tokio)**: The foundational asynchronous runtime for Rust.
- **[Criterion.rs](https://github.com/bheisler/criterion.rs)**: Statistics-driven benchmarking library.

### 🐹 Go (High-Concurrency)
- **[pprof](https://pkg.go.dev/net/http/pprof)**: Go's unparalleled, built-in profiling tool for CPU, memory, and goroutine blocking.
- **[Fasthttp](https://github.com/valyala/fasthttp)**: Minimal-overhead, high-performance HTTP server up to 10x faster than `net/http`.
- **[sync.Pool](https://pkg.go.dev/sync#Pool)**: The built-in package for reducing garbage collection by reusing object allocations.
- **[Gnet](https://github.com/panjf2000/gnet)**: A high-performance, lightweight, non-blocking networking framework.

### 🐍 Python (High-Perf Glue)
- **[Polars](https://github.com/pola-rs/polars)**: Rust-powered dataframes, 10-100x faster than Pandas.
- **[NumPy](https://github.com/numpy/numpy)**: The foundational SIMD-accelerated numerical library.
- **[uvloop](https://github.com/MagicStack/uvloop)**: Ultra-fast drop-in replacement for the `asyncio` event loop written in Cython.
- **[Cython](https://cython.org/) / [Numba](https://numba.pydata.org/)**: Compiling Python code down to native C/LLVM execution.

### ☕ Java / JVM (Low Latency)
- **[Chronicle Queue](https://github.com/OpenHFT/Chronicle-Queue)**: Persistent low-latency IPC (< 4μs).
- **[LMAX Disruptor](https://github.com/LMAX-Exchange/disruptor)**: High-performance inter-thread messaging (Ring Buffer).
- **[Netty](https://github.com/netty/netty)**: Async event-driven network application framework.
- **[JMH (Java Microbenchmark Harness)](https://github.com/openjdk/jmh)**: The JVM standard for accurately measuring micro-performance.

### 🌐 JavaScript / Node.js
- **[Clinic.js](https://clinicjs.org/)**: Open-source diagnostic tool for Node.js to identify bottlenecks and event-loop delays.
- **[uWebSockets.js](https://github.com/uNetworking/uWebSockets.js)**: A C++ port acting as a ludicrously fast HTTP/WebSocket server for Node.js.
- **[Pino](https://github.com/pinojs/pino)**: Extremely fast Node.js logger utilizing asynchronous streams.

### 🔷 .NET / C#
- **[Span<T> / Memory<T>](https://learn.microsoft.com/en-us/dotnet/standard/memory-and-spans/memory-t-and-span-t-usage-guidelines)**: Highly efficient memory primitives for safe array slicing.
- **[Channels](https://github.com/dotnet/runtime/tree/main/src/libraries/System.Threading.Channels)**: High-performance producer/consumer library.
- **[NetCoreServer](https://github.com/chronoxor/NetCoreServer)**: Ultra-fast asynchronous socket library.

---

## ⚙️ The Build Pipeline

- **[ThinLTO](https://clang.llvm.org/docs/ThinLTO.html)**: Scalable Whole-Program Optimization.
- **[LLVM BOLT](https://github.com/facebookincubator/BOLT)**: Post-link binary optimizer for improved cache utilization.
- **[PGO](https://en.wikipedia.org/wiki/Profile-guided_optimization)**: Profile-Guided Optimization (GCC, Clang, MSVC).

---

## 🛠️ Tooling & Observability

- **[hyperfine](https://github.com/sharkdp/hyperfine)**: Statistical CLI benchmarking.
- **[FlameGraph](https://github.com/brendangregg/FlameGraph)**: Visualization for CPU profile samples.
- **[Tracy](https://github.com/wolfpld/tracy)**: Real-time nanosecond-resolution frame profiler.

---

## 📚 Curated Resources

### 📄 Seminal Papers
- **Huffman (1952)**: [A Method for the Construction of Minimum-Redundancy Codes](https://ieeexplore.ieee.org/document/4051119).
- **Ziv & Lempel (1977)**: [A Universal Algorithm for Sequential Data Compression](https://ieeexplore.ieee.org/document/1055714).
- **Burrows & Wheeler (1994)**: [A Block-sorting Lossless Data Compression Algorithm](https://www.hpl.hp.com/techreports/Compaq-DEC/SRC-RR-124.pdf).
- **Facebook (Yann Collet)**: [Zstandard: Fast and Data-Independent Compression](https://github.com/facebook/zstd).

### 🎥 Must-Watch Talks
- **[Data-Oriented Design] (https://www.youtube.com/watch?v=rX0ItVEVjHc)** — Mike Acton.
- **[When a Microsecond Is an Eternity] (https://www.youtube.com/watch?v=NH1Tta7purM)** — Carl Cook.
- **[Efficiency with Algorithms, Performance with Data Structures] (https://www.youtube.com/watch?v=fHNmRkzxHWs)** — Chandler Carruth.
- **[Performance Matters] (https://www.youtube.com/watch?v=r-TLSBdHe1A)** — Emery Berger.

### ✍️ High-Authority Engineering Blogs & Articles
- **[Agner Fog's Software Optimization Resources](https://www.agner.org/optimize/)**: The definitive guide to x86 microarchitecture optimizations.
- **[Latency Numbers Every Programmer Should Know](https://gist.github.com/jboner/2841832)**: A legendary cheat sheet on computer latencies.
- **[Cloudflare Blog](https://blog.cloudflare.com/)**: Deep dives into Linux kernel tuning and network performance.
- **[Netflix Tech Blog](https://netflixtechblog.com/)**: Lessons on JVM tuning, high-throughput systems, and caching strategies.
- **[Brendan Gregg's Blog](https://www.brendangregg.com/blog/)**: The definitive source for eBPF, flame graphs, and Linux performance analysis.
- **[Dan Luu's Blog](https://danluu.com/)**: Data-driven analysis of hardware latency and system architecture.

### 📖 Recommended Books
- **[Designing Data-Intensive Applications](https://dataintensive.net/)** *by Martin Kleppmann*.
- **[Computer Systems: A Programmer's Perspective (CSAPP)](https://csapp.cs.cmu.edu/)** *by Randal E. Bryant and David R. O'Hallaron*.
- **[Systems Performance: Enterprise and the Cloud](https://www.brendangregg.com/systems-performance-2nd-edition-book.html)** *by Brendan Gregg*.

---

## 🤝 Contributing
Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

## 📄 License
To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work under [CC0](LICENSE).
