## Naive Bayesian Probability Fusion

This repository provides a Python implementation of **probability fusion** 
using a Naive Bayesian–style algorithm. It includes both:

- **Exact fusion** (enumerates all combinations).
- **Accelerated fusion** (sampling-based, much faster for large lists).

## Example Usage
```
from fuse_probabilities import fuse_probabilities
import numpy as np
import time

# Generate a random input list of 25 probabilities
input_list = np.random.rand(25).tolist()

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
## Example Output
```
Exact fused: 0.9999998894326695
Accelerated fused: 0.9395948324569728
Exact time      : 87.626295 s
Accelerated time: 0.001055 s
Time saved by accelerated algorithm: 87.625239 s
```
⚡ Note: This output was generated using a list of 25 elements.
The exact algorithm takes ~88 seconds because it evaluates 2^25 ≈ 33 million subsets.
The accelerated algorithm runs almost instantly.
👉 As the number of elements increases, the time saved by the accelerated method grows exponentially.

## Citation
If you use this code in your research or projects, please cite:
```
Liu, X., Iturburu, L., Dyke, S. J., Lenjani, A., Ramirez, J., & Zhang, X. (2022). Information fusion to automatically classify post-event building damage state. Engineering Structures, 253, 113765.
```
