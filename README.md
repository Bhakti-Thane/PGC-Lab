# PGC Lab – Parallel & Grid Computing
## Matrix Multiplication Performance Comparison

This experiment compares matrix multiplication using different **CPU-based parallel computing approaches** studied in the Parallel & Grid Computing (PGC) laboratory.

### Implementations Covered

1. Sequential CPU
2. OpenMP Multithreading
3. MPI Parallel Processing

> **Note:** CUDA/GPU implementation is not included because it is outside the topics covered in this experiment.

---

## 1. Objective

To implement 4000 × 4000 matrix multiplication using sequential and parallel CPU techniques and compare their performance in terms of:

- Execution time
- Speedup
- Computational performance
- Resource utilization

---

## 2. Matrix Size

- Matrix A: 4000 × 4000
- Matrix B: 4000 × 4000
- Result Matrix C: 4000 × 4000

The large matrix size provides enough computational work to observe the effect of parallel processing.

---

# 3. Sequential Matrix Multiplication

The sequential program performs matrix multiplication using a single CPU execution path.

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

# 4. OpenMP Matrix Multiplication

OpenMP is used to parallelize the matrix multiplication using multiple CPU threads.

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

The program uses **8 CPU threads** to perform the computation in parallel.

---

# 5. MPI Matrix Multiplication

MPI (Message Passing Interface) is used for process-based parallel computation.

The matrix multiplication workload is distributed among multiple MPI processes.

### Example execution

```bash
mpirun -np 4 ./matrix_mpi
```

### Measured Result

```text
Matrix Size = 4000 x 4000
Execution Time = 92.98 seconds
```

The experiment uses **4 MPI processes/VMs**.

---

# 6. Performance Comparison

| Implementation | Execution Time | Speedup |
|----------------|---------------:|--------:|
| Sequential CPU | 348.02 s | 1.00× |
| OpenMP (8 Threads) | 132.46 s | 2.63× |
| MPI (4 Processes/VMs) | 92.98 s | 3.74× |

---

# 7. Speedup Calculation

Speedup is calculated using:

```text
Speedup = Sequential Execution Time / Parallel Execution Time
```

### Sequential

```text
348.02 / 348.02 = 1.00×
```

### OpenMP

```text
348.02 / 132.46 ≈ 2.63×
```

### MPI

```text
348.02 / 92.98 ≈ 3.74×
```

The sequential implementation is the baseline with a speedup of **1.00×**.

---

# 8. Verification

Correctness is checked using:

```text
Verification C[0][0] = 4000.00
```

For the matrix initialization used in this experiment, the expected value of `C[0][0]` is 4000.

The verification value confirms that the matrix multiplication produced the expected result.

---

# 9. System Monitoring Using htop

The Linux `htop` utility was used to monitor system resources.

It displays:

- CPU utilization
- CPU cores/threads
- Memory usage
- Running processes
- System load

`htop` helps observe system resource usage during parallel execution.

---

# 10. Results

### Sequential CPU

```text
Execution Time = 348.02 seconds
Speedup = 1.00×
```

This is the baseline.

### OpenMP

```text
Execution Time = 132.46 seconds
Speedup = 2.63×
Threads = 8
```

OpenMP uses multiple CPU threads to perform parts of the computation concurrently.

### MPI

```text
Execution Time = 92.98 seconds
Speedup = 3.74×
Processes = 4
```

MPI distributes the computation among multiple processes.

---

# 11. Graphs

The project contains performance graphs for:

- Execution Time Comparison
- Speedup Comparison
- Overall Performance Dashboard
- CPU resource monitoring

---

# 12. Technologies Used

- C
- GCC
- OpenMP
- MPI
- Linux / Ubuntu
- htop
- Python / Matplotlib (for graphs)

---

# 13. Project Structure

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
├── Results/
│   ├── execution_time_comparison.png
│   ├── speedup_comparison.png
│   ├── performance_dashboard.png
│   └── htop_resource_monitor.png
│
└── README.md
```

---

# 14. Conclusion

This experiment demonstrates matrix multiplication using sequential execution, OpenMP multithreading, and MPI-based parallel processing.

The sequential implementation provides the baseline. OpenMP improves performance by using multiple CPU threads, while MPI distributes the computation among multiple processes.

The performance is evaluated using execution time and speedup.

---

## Key Results

| Method | Time | Speedup |
|---|---:|---:|
| Sequential | 348.02 s | 1.00× |
| OpenMP | 132.46 s | 2.63× |
| MPI | 92.98 s | 3.74× |
