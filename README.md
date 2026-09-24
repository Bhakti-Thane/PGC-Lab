# PGC Lab – Parallel & Grid Computing
## Matrix Multiplication Performance Comparison

This experiment compares 4000 × 4000 matrix multiplication using:

1. Sequential CPU
2. OpenMP Multithreading
3. MPI Parallel Processing

---

## 1. Objective

To implement matrix multiplication using sequential and parallel CPU techniques and compare their performance using execution time and speedup.

---

## 2. Matrix Size

- Matrix A: 4000 × 4000
- Matrix B: 4000 × 4000
- Result Matrix C: 4000 × 4000

---

## 3. Sequential Matrix Multiplication

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

## 4. OpenMP Matrix Multiplication

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

---

## 5. MPI Matrix Multiplication

MPI (Message Passing Interface) is used for process-based parallel computation.

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

## 6. Performance Comparison

| Implementation | Execution Time | Speedup |
|---|---:|---:|
| Sequential CPU | 348.02 s | 1.00× |
| OpenMP (8 Threads) | 132.46 s | 2.63× |
| MPI (4 Processes/VMs) | 92.98 s | 3.74× |

---

## 7. Speedup Calculation

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

---

## 8. Verification

The result is checked using:

```text
Verification C[0][0] = 4000.00
```

This confirms the expected matrix multiplication result for the initialization used in the experiment.

---

# 9. Graphs and Results

## 9.1 Speedup Comparison

This graph compares the speedup of OpenMP and MPI with the sequential baseline.

![Speedup Comparison](Results/speedup_comparison.png)

---

## 9.2 Execution Time Comparison

This graph compares the execution time of the tested implementations.

![Execution Time Comparison](Results/execution_time_comparison.png)

---

## 9.3 Overall Performance Dashboard

The dashboard summarizes execution time, speedup, and computational performance.

![Overall Performance Dashboard](Results/overall_performance_dashboard.png)

---

## 9.4 System Monitoring Using htop

Linux `htop` was used to observe CPU, memory, processes, and system load.

![htop Resource Monitor](Results/htop_resource_monitor.jpeg)

---

## 10. Technologies Used

- C
- GCC
- OpenMP
- MPI
- Linux / Ubuntu
- htop
- Python / Matplotlib for graphs

---

## 11. Project Structure

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
│   ├── speedup_comparison.png
│   ├── execution_time_comparison.png
│   ├── overall_performance_dashboard.png
│   └── htop_resource_monitor.jpeg
│
└── README.md
```

---

## 12. Conclusion

This experiment demonstrates matrix multiplication using sequential execution, OpenMP multithreading, and MPI-based parallel processing.

The sequential implementation provides the baseline. OpenMP uses multiple CPU threads, while MPI distributes computation among multiple processes.

The performance is evaluated using execution time and speedup.
