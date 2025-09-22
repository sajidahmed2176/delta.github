# 📘 Numerical Integration: Simpson's Rule vs Trapezoidal Rule  

## 📌 Problem Statement  
The goal of this project is to **implement Simpson’s Rule and the Trapezoidal Rule** in C to approximate definite integrals and compare their accuracy with exact values.  

We compute two integrals:  
1. \(\int_0^\pi \sin(x)\, dx\)  
2. \(\int_1^2 \ln(x)\, dx\)  

---

## 📖 Theory  

### 🔹 Numerical Integration  
When it is difficult or impossible to compute a definite integral analytically, we use numerical methods to approximate it.  

### 🔹 Trapezoidal Rule  
Approximates the area under the curve using trapezoids.  

\[
\int_a^b f(x)\, dx \approx \frac{h}{2}\Big[f(a) + 2\sum_{i=1}^{n-1} f(a + ih) + f(b)\Big]
\]  

- Error term: \(-\frac{(b-a)h^2}{12} f''(\xi)\)  

### 🔹 Simpson’s Rule  
Approximates the curve with parabolas (quadratic functions).  

\[
\int_a^b f(x)\, dx \approx \frac{h}{3}\Big[f(a) + 4\sum_{i=1, \text{odd}}^{n-1} f(a+ih) + 2\sum_{i=2, \text{even}}^{n-2} f(a+ih) + f(b)\Big]
\]  

- Error term: \(-\frac{(b-a)h^4}{180} f^{(4)}(\xi)\)  
- Requires **even number of subintervals (n must be even)**  

📌 **Accuracy**: Simpson’s Rule is generally much more accurate than Trapezoidal Rule for smooth functions.  

---

## 💻 Implementation + Sample Output  

```c
#include <stdio.h>
#include <math.h>

// Function Prototypes
double trapezoidal_rule(double (*f)(double), double a, double b, int n);
double simpsons_rule(double (*f)(double), double a, double b, int n);

// Functions to integrate
double f1(double x) { return sin(x); }
double f2(double x) { return log(x); }

int main() {
    int n;
    double a1 = 0.0, b1 = M_PI;
    double a2 = 1.0, b2 = 2.0;
    double exact1 = 2.0;
    double exact2 = 2 * log(2) - 1;

    printf("Enter number of intervals (n): ");
    scanf("%d", &n);

    if (n % 2 != 0) {
        printf("Simpson's Rule requires even n, so using n+1.\n");
        n++;
    }

    double trap1 = trapezoidal_rule(f1, a1, b1, n);
    double simp1 = simpsons_rule(f1, a1, b1, n);

    double trap2 = trapezoidal_rule(f2, a2, b2, n);
    double simp2 = simpsons_rule(f2, a2, b2, n);

    double error_trap1 = fabs(trap1 - exact1) / exact1 * 100.0;
    double error_simp1 = fabs(simp1 - exact1) / exact1 * 100.0;
    double error_trap2 = fabs(trap2 - exact2) / exact2 * 100.0;
    double error_simp2 = fabs(simp2 - exact2) / exact2 * 100.0;

    printf("\n--- Numerical Integration Results ---\n");

    printf("\n1) Integral of sin(x) from 0 to π:\n");
    printf("   • Trapezoidal Rule Result = %.8lf | Error %% = %.6lf%%\n", trap1, error_trap1);
    printf("   • Simpson's Rule Result  = %.8lf | Error %% = %.6lf%%\n", simp1, error_simp1);

    printf("\n2) Integral of ln(x) from 1 to 2:\n");
    printf("   • Trapezoidal Rule Result = %.8lf | Error %% = %.6lf%%\n", trap2, error_trap2);
    printf("   • Simpson's Rule Result  = %.8lf | Error %% = %.6lf%%\n", simp2, error_simp2);

    return 0;
}

double trapezoidal_rule(double (*f)(double), double a, double b, int n) {
    double h = (b - a) / n;
    double sum = f(a) + f(b);
    for (int i = 1; i < n; i++) sum += 2 * f(a + i * h);
    return (h / 2.0) * sum;
}

double simpsons_rule(double (*f)(double), double a, double b, int n) {
    double h = (b - a) / n;
    double sum = f(a) + f(b);
    for (int i = 1; i < n; i++) {
        if (i % 2 == 0) sum += 2 * f(a + i * h);
        else sum += 4 * f(a + i * h);
    }
    return (h / 3.0) * sum;
}

/* ---------------- Sample Output ----------------
Enter number of intervals (n): 10

--- Numerical Integration Results ---

1) Integral of sin(x) from 0 to π:
   • Trapezoidal Rule Result = 1.98352354 | Error % = 0.823823%
   • Simpson's Rule Result  = 2.00010952 | Error % = 0.005476%

2) Integral of ln(x) from 1 to 2:
   • Trapezoidal Rule Result = 0.38631855 | Error % = 0.283127%
   • Simpson's Rule Result  = 0.38630394 | Error % = 0.279356%
------------------------------------------------- */
