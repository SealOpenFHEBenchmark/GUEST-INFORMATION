# FHE Performance Benchmark: OpenFHE vs. Microsoft SEAL on Raspberry Pi 5

This organization contains the results and analysis from a performance comparison study between two leading Fully Homomorphic Encryption (FHE) libraries: **OpenFHE** and **Microsoft SEAL**.

All benchmarks were executed on a **Raspberry Pi 5** device to evaluate the efficiency and scalability of both libraries on edge/IoT devices.

## 📊 About This Project

The primary objective of this project is to measure and compare the head-to-head performance of OpenFHE and Microsoft SEAL when executing a specific IoT telemetry protocol.

This comparison focuses on three core algorithms used in the protocol:

1.  **Algorithm 1: RoundInit (Initialization & Encryption)**
    * Measures the overhead of random mask generation and initial encryption.
2.  **Algorithm 2: NodeProcess (Homomorphic Operation)**
    * Measures the core FHE performance, specifically repeated ciphertext-plaintext addition (`EvalAdd` vs `add_plain_inplace`). This is the primary scalability metric.
3.  **Algorithm 3: RoundVerify (Decryption & Verification)**
    * Measures the overhead of decryption, unmasking, and data verification.

Cryptographic parameters (BFV, N=8192, q=65537) were kept identical across both libraries to ensure a fair comparison.

## 🛠️ Technology Stack

* **Language:** C++17
* **FHE Libraries:**
    * OpenFHE
    * Microsoft SEAL
* **Build System:** CMake
* **Hardware:** Raspberry Pi 5 (ARM64)
* **OS:** Raspberry Pi OS (Debian 12 Bookworm)

## 📈 Results (Summary)

Analysis of the benchmark data (averaged over 5 runs for node counts `n` from 16 to 4096) shows the following findings:

* **Overhead (Alg 1 & 3):** OpenFHE consistently demonstrated faster performance for non-homomorphic operations such as initial encryption and decryption/verification.
* **Homomorphic Performance (Alg 2):** Microsoft SEAL was significantly superior in performance and scalability for the `NodeProcess` operation. At a workload of 4096 nodes, SEAL proved to be **~2.5x faster** than OpenFHE.

---

## 🔒 Source Code Access

The complete source code files (`IoT_FHE.cpp`, `benchmark_seal.cpp`, and `CMakeLists.txt`) for this benchmark are not publicly available.

To obtain access to the complete code for academic, research, or collaboration purposes, please use the contact information below:

* **Name:** Ardea Himawan Nugroho
* **Phone/WA:** (+62) 85600009732
* **Email:** ardeahnugroho@gmail.com
