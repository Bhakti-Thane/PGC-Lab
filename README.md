# PGC Lab – Parallel & Grid Computing
## Matrix Multiplication Performance Comparison

This experiment compares 4000 × 4000 matrix multiplication using:

1. Sequential CPU
2. OpenMP Multithreading
3. MPI Parallel Processing

---

## Objective

To implement matrix multiplication using sequential and parallel CPU techniques and compare their performance using execution time and speedup.

## Matrix Size

- Matrix A: 4000 × 4000
- Matrix B: 4000 × 4000
- Result Matrix C: 4000 × 4000

---

## 1. Sequential Matrix Multiplication

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

The sequential execution time is approximately **348.02 seconds** and is used as the baseline.

---

## 2. OpenMP Matrix Multiplication

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

---

## 3. MPI Matrix Multiplication

MPI (Message Passing Interface) is used for process-based parallel computation.

### Example execution

```bash
mpirun -np 4 ./matrix_mpi
```

### Result

```text
Matrix Size = 4000 x 4000
Execution Time = 92.98 seconds
```

The experiment uses **4 MPI processes/VMs**.

---

## 4. Performance Comparison

| Implementation | Execution Time | Speedup |
|---|---:|---:|
| Sequential CPU | 348.02 s | 1.00× |
| OpenMP (8 Threads) | 132.46 s | 2.63× |
| MPI (4 Processes/VMs) | 92.98 s | 3.74× |

### Speedup Formula

```text
Speedup = Sequential Execution Time / Parallel Execution Time
```

OpenMP:

```text
348.02 / 132.46 ≈ 2.63×
```

MPI:

```text
348.02 / 92.98 ≈ 3.74×
```

---

## 5. Verification

```text
Verification C[0][0] = 4000.00
```

This verifies the expected matrix multiplication result for the initialization used in the experiment.

---

# 6. Graphs and Results

## Speedup Comparison

![Speedup Comparison](speedup_comparison.png)

---

## Execution Time Comparison

![Execution Time Comparison](execution_time_comparison.png)

---

## Overall Performance Dashboard

![Overall Performance Dashboard](overall_performance_dashboard.png)

---

## System Monitoring Using htop

Linux `htop` was used to monitor CPU utilization, memory usage, processes, and system load.

![htop Resource Monitor](htop_resource_monitor.jpeg)

---

# 7. Technologies Used

- C
- GCC
- OpenMP
- MPI
- Linux / Ubuntu
- htop
- Python / Matplotlib for graphs

---

# 8. Project Structure

```text
PGC-Lab/
│
├── README.md
├── matrix_sequential.c
├── matrix_openmp.c
├── matrix_mpi.c
│
├── speedup_comparison.png
├── execution_time_comparison.png
├── overall_performance_dashboard.png
└── htop_resource_monitor.jpeg
```

---

# 9. Conclusion

This experiment demonstrates matrix multiplication using sequential execution, OpenMP multithreading, and MPI-based parallel processing.

The sequential implementation provides the baseline. OpenMP uses multiple CPU threads, while MPI distributes computation among multiple processes.

The performance is evaluated using execution time and speedup.
