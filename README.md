# Parallel Matrix Multiplication Performance Analysis

## Overview

This project implements and compares matrix multiplication using four different approaches:

- Sequential
- OpenMP
- MPI
- CUDA

The matrix size used for the experiment is **4000 × 4000**.

---

## 1. Sequential Execution

The sequential implementation performs matrix multiplication without parallel processing.

### Compilation

```bash
gcc -O2 matrix_sequential.c -o matrix_sequential
