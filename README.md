### Algoritmos de Factorización con Código

---

## Introducción

La factorización de números enteros es un problema fundamental en teoría de números y criptografía. En este documento, exploraremos algunos de los algoritmos de factorización más importantes y proporcionaremos implementaciones en Python para cada uno.

## 1.Criba Clásica (Classical Sieve)

### Descripción

La criba clásica es un algoritmo de factorización que utiliza una criba para encontrar relaciones entre números. Es menos eficiente que la criba racional pero más simple.

### Explicación conceptual del Código

1. **Función `classical_sieve`**:
   - Define un límite \( B \) y un conjunto de primos menores que \( B \).
   - Busca relaciones donde \( a^2 \equiv b^2 \mod N \).
   - Resuelve el sistema de congruencias para encontrar factores.

## 2. Algoritmo de Factorización de Fermat

### Descripción

El algoritmo de factorización de Fermat es un método para factorizar números compuestos que son cercanos a un cuadrado perfecto. La idea principal es expresar el número \( N \) como una diferencia de cuadrados:
\[ N = a^2 - b^2 = (a + b)(a - b) \]
Si \( a \) y \( b \) son enteros, entonces \( N \) se puede factorizar en \( (a + b) \) y \( (a - b) \).

### Explicación conceptual del Código

1. **Función `fermat_factorization`**:
   - Inicia \( a \) con \( \lceil \sqrt{N} \rceil + 1 \).
   - Calcula \( b^2 = a^2 - N \).
   - Verifica si \( b^2 \) es un cuadrado perfecto.
   - Si lo es, devuelve los factores \( (a + b) \) y \( (a - b) \).
   - Si no, incrementa \( a \) y repite el proceso.

## 3. Algoritmo de Factorización de Pollard Rho

### Descripción

El algoritmo de Pollard Rho es un método probabilístico para factorizar números enteros. Utiliza una función pseudoaleatoria para encontrar un factor no trivial de \( N \).

### Explicación conceptual del Código

1. **Función `pollard_rho`**:
   - Define una función pseudoaleatoria \( f(x) = (x^2 + 1) \mod N \).
   - Inicializa \( x \) y \( y \) con 2.
   - Calcula \( x = f(x) \) y \( y = f(f(y)) \).
   - Calcula \( d = \gcd(|x - y|, N) \).
   - Si \( d \) es un factor no trivial, devuelve \( d \).

## 4. Algoritmo de Factorización con Curvas Elípticas (ECM)

### Descripción

El algoritmo de factorización con curvas elípticas (ECM) es un método para factorizar números enteros utilizando propiedades de las curvas elípticas. Es especialmente eficiente para encontrar factores pequeños.

### Explicación conceptual del Código

1. **Función `elliptic_curve_method`**:
   - Itera sobre los números primos hasta \( B \).
   - Multiplica el punto en la curva elíptica por el primo actual.
   - Si se encuentra un factor, devuelve el factor.
2. **Función `point_multiplication`**:
   - Implementa la multiplicación de punto en una curva elíptica.
   - Esta función debe ser implementada completamente para una curva elíptica específica.

## 5. Criba Racional (Rational Sieve)

### Descripción

La criba racional es un algoritmo de factorización que utiliza una criba para encontrar relaciones entre números. Es una versión más eficiente de la criba clásica.

### Explicación conceptual del Código

1. **Función `rational_sieve`**:
   - Define un límite \( B \) y un conjunto de primos menores que \( B \).
   - Busca relaciones donde \( a^2 \equiv b^2 \mod N \).
   - Resuelve el sistema de congruencias para encontrar factores.

## Conclusión

Los algoritmos de factorización son herramientas poderosas en teoría de números y criptografía. Cada algoritmo tiene sus ventajas y desventajas, y la elección del algoritmo adecuado depende de los requisitos específicos del problema. En este documento, hemos proporcionado implementaciones en Python para cada algoritmo, lo que debería ayudar a entender y aplicar estos métodos en la práctica.

---
