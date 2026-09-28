# Parallel Matrix Multiplication Performance Analysis

## Overview

This project focuses on the implementation and performance analysis of matrix multiplication using different computing approaches:

- Sequential
- OpenMP
- MPI
- CUDA

The matrix size used for the experiments is **4000 × 4000**.

---

## Objective

The objective is to implement matrix multiplication using different approaches and compare their execution performance.

The implementations are compared based on:

- Execution Time
- Speedup
- Verification of Results
- Resource Utilization

---

## 1. Sequential Implementation

The sequential implementation performs matrix multiplication using the traditional CPU-based approach.

### Compilation

```bash
gcc -O2 matrix_sequential.c -o matrix_sequential
