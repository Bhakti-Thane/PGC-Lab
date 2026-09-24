# Parallel & Grid Computing Lab
## Matrix Multiplication Performance Comparison

This project implements and compares 4000 × 4000 matrix multiplication using four computing approaches:

1. Sequential CPU
2. OpenMP Multithreading
3. MPI Parallel Processing
4. CUDA GPU Acceleration

The objective is to study execution time, speedup, and computational throughput for different parallel computing approaches.

---

## 1. Objective

To implement matrix multiplication using sequential and parallel computing techniques and compare their performance.

The following implementations are evaluated:

- Sequential CPU execution
- OpenMP-based CPU parallelism
- MPI-based process parallelism
- CUDA-based GPU parallelism

---

## 2. Matrix Size

- Matrix A: 4000 × 4000
- Matrix B: 4000 × 4000
- Result Matrix C: 4000 × 4000

The large matrix size provides a sufficiently large computational workload to observe performance differences.

---

# 3. Implementations

## 3.1 Sequential CPU

The sequential implementation performs matrix multiplication using normal CPU execution.

### Compilation

```bash
gcc -O2 matrix_sequential.c -o matrix_sequential
```

### Execution

```bash
./matrix_sequential
```

### Result

```text
Matrix Size = 4000 x 4000
Execution Time = 348.023990 seconds
Verification C[0][0] = 4000.00
```

The sequential execution time of approximately **348.02 seconds** is used as the baseline.

---

# 3.2 OpenMP

OpenMP is used to parallelize matrix multiplication using multiple CPU threads.

### Compilation

```bash
gcc -O2 -fopenmp matrix_openmp.c -o matrix_openmp
```

### Execution

```bash
./matrix_openmp
```

### Result

```text
Matrix Size = 4000 x 4000
Number of Threads Used = 8
Execution Time = 132.457362 seconds
Verification C[0][0] = 4000.00
```

The implementation uses **8 CPU threads**.

---

# 3.3 MPI

MPI (Message Passing Interface) is used for process-based parallel computation.

The workload is distributed across multiple MPI processes/nodes/VMs.

### Example execution

```bash
mpirun -np 4 ./matrix_mpi
```

### Measured Result

```text
Matrix Size = 4000 x 4000
Execution Time = 92.98 seconds
```

The experiment uses **4 MPI processes/nodes/VMs**.

---

# 3.4 CUDA GPU

CUDA is used to perform matrix multiplication on an NVIDIA GPU.

### Compilation

```bash
nvcc matrix_cuda.cu -o matrix_cuda
```

### Execution

```bash
./matrix_cuda
```

### Measured Result

```text
CUDA Kernel Time ≈ 0.1464 seconds
CUDA Total Phase ≈ 0.1650 seconds
```

The CUDA implementation uses GPU parallelism to execute many matrix operations concurrently.

---

# 4. Performance Comparison

| Implementation | Execution Time | Speedup |
|----------------|---------------:|--------:|
| Sequential CPU | 348.02 s | 1.00× |
| OpenMP (8 Threads) | 132.46 s | 2.63× |
| MPI (4 Processes/VMs) | 92.98 s | 3.74× |
| CUDA GPU | 0.165 s | 2109.18× |

**Note:** CUDA is measured on GPU hardware, while Sequential, OpenMP, and MPI use CPU/process-based configurations. Therefore, these are measurements of the tested implementations and hardware configurations, not a like-for-like CPU-only comparison.

---

# 5. Speedup Calculation

Speedup is calculated as:

```text
Speedup = Sequential Execution Time / Parallel Execution Time
```

### OpenMP

```text
348.02 / 132.46 ≈ 2.63×
```

### MPI

```text
348.02 / 92.98 ≈ 3.74×
```

### CUDA

```text
348.02 / 0.165 ≈ 2109.18×
```

The sequential implementation is the baseline with a speedup of **1.00×**.

---

# 6. Verification

Correctness is checked using:

```text
Verification C[0][0] = 4000.00
```

For the matrix initialization used in this experiment, the expected value of `C[0][0]` is 4000.

The verification value confirms that the matrix multiplication produced the expected result.

---

# 7. Performance Metrics

## Execution Time

Execution time represents the time required to complete matrix multiplication.

## Speedup

Speedup measures improvement relative to the sequential baseline.

```text
Speedup = Sequential Time / Parallel Time
```

## GFLOPS

GFLOPS stands for **Giga Floating-Point Operations Per Second**.

Measured values:

| Implementation | Approx. GFLOPS |
|----------------|---------------:|
| Sequential | 0.37 |
| OpenMP | 0.97 |
| MPI | 1.38 |
| CUDA GPU | 775.74 |

---

# 8. System Monitoring

The Linux `htop` utility was used to monitor system resources.

It provides information about:

- CPU utilization
- CPU cores/threads
- Memory usage
- Running processes
- System load

This helps observe system resource usage during parallel execution.

---

# 9. Results

### Sequential CPU

```text
348.02 seconds
```

This is the baseline.

### OpenMP

```text
132.46 seconds
2.63× speedup
```

Multiple CPU threads reduce execution time.

### MPI

```text
92.98 seconds
3.74× speedup
```

The workload is distributed across multiple MPI processes.

### CUDA

```text
0.165 seconds total CUDA phase
2109.18× relative speedup
```

The CUDA implementation uses GPU parallelism for matrix computation.

---

# 10. Graphs

The project includes performance visualizations for:

- Speedup comparison
- Execution time comparison
- CPU vs CUDA execution time
- Computational throughput
- Overall performance dashboard

---

# 11. Technologies Used

- C
- GCC
- OpenMP
- MPI
- CUDA
- NVIDIA GPU
- Linux / Ubuntu
- htop
- Python / Matplotlib

---

# 12. Suggested Project Structure

```text
PGC-Lab/
│
├── Sequential/
│   ├── matrix_sequential.c
│   └── matrix_sequential
│
├── OpenMP/
│   ├── matrix_openmp.c
│   └── matrix_openmp
│
├── MPI/
│   ├── matrix_mpi.c
│   └── matrix_mpi
│
├── CUDA/
│   ├── matrix_cuda.cu
│   └── matrix_cuda
│
├── Results/
│   ├── execution_time_comparison.png
│   ├── speedup_comparison.png
│   ├── performance_dashboard.png
│   └── htop_resource_monitor.png
│
└── README.md
```

---

# 13. Conclusion

This experiment demonstrates matrix multiplication using sequential CPU execution, OpenMP multithreading, MPI process-based parallelism, and CUDA GPU acceleration.

The sequential implementation provides the baseline. OpenMP uses multiple CPU threads, MPI distributes computation among processes, and CUDA uses GPU parallelism for the computationally intensive workload.

Execution time, speedup, and GFLOPS are used to evaluate the performance of the tested implementations.

---

## References

- OpenMP: https://www.openmp.org/
- MPI Forum: https://www.mpi-forum.org/
- NVIDIA CUDA Documentation: https://docs.nvidia.com/cuda/
- NVIDIA CUDA Programming Guide: https://docs.nvidia.com/cuda/cuda-programming-guide/
