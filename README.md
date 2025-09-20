# Naive Bayesian Probability Fusion

This repository provides a Python implementation of **probability fusion** 
using a Naive Bayesian–style algorithm. It includes both:

- **Exact fusion** (enumerates all combinations).
- **Accelerated fusion** (sampling-based, much faster for large lists).

# Example Usage
```
from fuse_probabilities import fuse_probabilities
import numpy as np
import time

# Generate a random input list of 20 probabilities
input_list = np.random.rand(20).tolist()

# Exact fusion
t0 = time.perf_counter()
result_exact = fuse_probabilities(input_list, accelerate=False)
t1 = time.perf_counter()

# Accelerated fusion
result_accel = fuse_probabilities(input_list, accelerate=True, seed=42)
t2 = time.perf_counter()

print("Exact fused probability      :", result_exact)
print("Accelerated fused probability:", result_accel)
print(f"Exact time      : {t1 - t0:.6f} s")
print(f"Accelerated time: {t2 - t1:.6f} s")
print(f"Time saved by accelerated algorithm: {(t1 - t0) - (t2 - t1):.6f} s")
```
