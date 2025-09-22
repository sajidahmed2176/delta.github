# Numerical Integration: Simpson's Rule vs Trapezoidal Rule

## Description
This project implements **Simpson's Rule** and the **Trapezoidal Rule** to approximate definite integrals and compares their accuracy. Numerical integration is essential for functions that cannot be integrated analytically.

## Mathematical Background

### Trapezoidal Rule
Approximates the integral by summing areas of trapezoids:

\[
\int_a^b f(x)dx \approx \frac{h}{2} \Big[f(a) + 2\sum_{i=1}^{n-1} f(x_i) + f(b)\Big]
\]

- Step size: \(h = \frac{b-a}{n}\)
- Accuracy: \(O(h^2)\)

### Simpson's Rule
Approximates the integral using parabolic segments:

\[
\int_a^b f(x)dx \approx \frac{h}{3} \Big[f(a) + 4\sum_{\text{odd } i} f(x_i) + 2\sum_{\text{even } i} f(x_i) + f(b)\Big]
\]

- Requires even \(n\)
- Accuracy: \(O(h^4)\)

## Implemented Integrals
1. \(\int_0^\pi \sin(x) dx = 2\)  
2. \(\int_1^2 \ln(x) dx = 2\ln(2) - 1\)

## How to Run
```bash
git clone <repository-url>
cd <repository-folder>
python integration_comparison.py

![Solution Comparison](solutions_graph.WhatsApp Image 2025-09-22 at 23.00.31_06b8146c.jpg)
