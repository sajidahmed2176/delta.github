# Numerical Integration: Simpson’s Rule vs Trapezoidal Rule

## 1. Project Overview
This project implements **Simpson’s Rule** and **Trapezoidal Rule** for numerical integration.  
The goal is to **approximate definite integrals** and compare the accuracy of these two methods on sample test functions.

Numerical integration (also called *numerical quadrature*) is the process of approximating
the value of a definite integral when an exact analytical solution is difficult or impossible to obtain.

The general form of a definite integral is:

\[
I = \int_a^b f(x)\,dx
\]

where \(f(x)\) is a continuous function defined on the interval \([a,b]\).

---

## 2. Theoretical Background
- **Trapezoidal Rule**: Approximates the area under the curve by dividing it into trapezoids.  
  Formula:  
  \[
  I \approx \frac{h}{2}\left[f(a) + 2\sum_{i=1}^{n-1} f(x_i) + f(b)\right]
  \]
  where \(h = \frac{b-a}{n}\).

- **Simpson’s Rule**: Uses parabolic arcs instead of straight lines for approximation.  
  Formula (for even \(n\)):  
  \[
  I \approx \frac{h}{3}\left[f(a) + 4\sum_{i=1,3,5,\dots}^{n-1} f(x_i) + 2\sum_{i=2,4,6,\dots}^{n-2} f(x_i) + f(b)\right]
  \]

- **Expected Accuracy**:  
  - Simpson’s Rule is generally more accurate than the Trapezoidal Rule for smooth functions.  
  - Trapezoidal Rule converges slower compared to Simpson’s Rule.

---

## 3. Features
- Implementation of **Trapezoidal Rule** in C.
- Implementation of **Simpson’s Rule** in C.
- Comparison of accuracy on:
  1. \(\int_0^\pi \sin(x)\, dx = 2\)
  2. \(\int_1^{2} \ln(x)\, dx = 2\ln(2) - 1\)

---

## 4. Project Structure
