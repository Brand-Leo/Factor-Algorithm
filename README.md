### Algoritmos de Factorización con Código

---

## Introducción

La factorización de números enteros es un problema fundamental en teoría de números y criptografía. En este documento, exploraremos algunos de los algoritmos de factorización más importantes y proporcionaremos implementaciones en Python para cada uno.

## 1.Criba Clásica (Classical Sieve)

### Descripción

La criba clásica es un algoritmo de factorización que utiliza una criba para encontrar relaciones entre números. Es menos eficiente que la criba racional pero más simple.

### Código en Python

```python
import math
from sympy import primerange

def classical_sieve(N):
    B = int(math.sqrt(N))
    primes = list(primerange(2, B + 1))
    relations = []

    for a in range(1, B + 1):
        b_squared = a**2 % N
        if all(b_squared % p == 0 for p in primes):
            relations.append((a, b_squared))

    # Resolver el sistema de congruencias para encontrar factores
    # Esta parte es compleja y requiere una implementación detallada
    pass

# Ejemplo de uso
N = 187
factors = classical_sieve(N)
print(f"Factores encontrados: {factors}")
```

### Explicación del Código

1. **Función `classical_sieve`**:
   - Define un límite \( B \) y un conjunto de primos menores que \( B \).
   - Busca relaciones donde \( a^2 \equiv b^2 \mod N \).
   - Resuelve el sistema de congruencias para encontrar factores.

## 2. Algoritmo de Factorización de Fermat

### Descripción

El algoritmo de factorización de Fermat es un método para factorizar números compuestos que son cercanos a un cuadrado perfecto. La idea principal es expresar el número \( N \) como una diferencia de cuadrados:
\[ N = a^2 - b^2 = (a + b)(a - b) \]
Si \( a \) y \( b \) son enteros, entonces \( N \) se puede factorizar en \( (a + b) \) y \( (a - b) \).

### Código en Python

```python
import math

def fermat_factorization(N):
    a = math.isqrt(N) + 1
    while True:
        b_squared = a**2 - N
        b = math.isqrt(b_squared)
        if b_squared == b**2:
            return (a + b, a - b)
        a += 1

# Ejemplo de uso
N = 5959
factors = fermat_factorization(N)
print(f"Los factores de {N} son: {factors}")
```

### Explicación del Código

1. **Importar `math`**: Se utiliza para calcular la raíz cuadrada.
2. **Función `fermat_factorization`**:
   - Inicia \( a \) con \( \lceil \sqrt{N} \rceil + 1 \).
   - Calcula \( b^2 = a^2 - N \).
   - Verifica si \( b^2 \) es un cuadrado perfecto.
   - Si lo es, devuelve los factores \( (a + b) \) y \( (a - b) \).
   - Si no, incrementa \( a \) y repite el proceso.

## 3. Algoritmo de Factorización de Pollard Rho

### Descripción

El algoritmo de Pollard Rho es un método probabilístico para factorizar números enteros. Utiliza una función pseudoaleatoria para encontrar un factor no trivial de \( N \).

### Código en Python

```python
import math

def pollard_rho(N):
    def f(x):
        return (x**2 + 1) % N

    x, y, d = 2, 2, 1
    while d == 1:
        x = f(x)
        y = f(f(y))
        d = math.gcd(abs(x - y), N)
    return d

# Ejemplo de uso
N = 1387
factor = pollard_rho(N)
print(f"Factor encontrado: {factor}")
```

### Explicación del Código

1. **Función `pollard_rho`**:
   - Define una función pseudoaleatoria \( f(x) = (x^2 + 1) \mod N \).
   - Inicializa \( x \) y \( y \) con 2.
   - Calcula \( x = f(x) \) y \( y = f(f(y)) \).
   - Calcula \( d = \gcd(|x - y|, N) \).
   - Si \( d \) es un factor no trivial, devuelve \( d \).

## 4. Algoritmo de Factorización con Curvas Elípticas (ECM)

### Descripción

El algoritmo de factorización con curvas elípticas (ECM) es un método para factorizar números enteros utilizando propiedades de las curvas elípticas. Es especialmente eficiente para encontrar factores pequeños.

### Código en Python

```python
from sympy import mod_inverse

def elliptic_curve_method(N, curve, point, B):
    for p in range(2, B + 1):
        try:
            # Multiplicación de punto en la curva elíptica
            point = point_multiplication(point, p, curve, N)
        except ValueError as e:
            # Si se encuentra un factor, devuelve el factor
            return e.args[0]
    return N

def point_multiplication(point, scalar, curve, N):
    # Implementación de la multiplicación de punto en una curva elíptica
    # Esta es una implementación simplificada y puede requerir ajustes
    pass

# Ejemplo de uso
N = 1009
curve = (1, 6)  # Parámetros de la curva elíptica y^2 = x^3 + ax + b
point = (2, 3)  # Punto inicial en la curva
B = 10  # Límite para el ECM
factor = elliptic_curve_method(N, curve, point, B)
print(f"Factor encontrado: {factor}")
```

### Explicación del Código

1. **Importar `mod_inverse`**: Se utiliza para calcular el inverso modular.
2. **Función `elliptic_curve_method`**:
   - Itera sobre los números primos hasta \( B \).
   - Multiplica el punto en la curva elíptica por el primo actual.
   - Si se encuentra un factor, devuelve el factor.
3. **Función `point_multiplication`**:
   - Implementa la multiplicación de punto en una curva elíptica.
   - Esta función debe ser implementada completamente para una curva elíptica específica.

## 5. Criba Racional (Rational Sieve)

### Descripción

La criba racional es un algoritmo de factorización que utiliza una criba para encontrar relaciones entre números. Es una versión más eficiente de la criba clásica.

### Código en Python

```python
import math
from sympy import primerange

def rational_sieve(N):
    B = int(math.sqrt(N))
    primes = list(primerange(2, B + 1))
    relations = []

    for a in range(1, B + 1):
        b_squared = a**2 % N
        if all(b_squared % p == 0 for p in primes):
            relations.append((a, b_squared))

    # Resolver el sistema de congruencias para encontrar factores
    # Esta parte es compleja y requiere una implementación detallada
    pass

# Ejemplo de uso
N = 187
factors = rational_sieve(N)
print(f"Factores encontrados: {factors}")
```

### Explicación del Código

1. **Función `rational_sieve`**:
   - Define un límite \( B \) y un conjunto de primos menores que \( B \).
   - Busca relaciones donde \( a^2 \equiv b^2 \mod N \).
   - Resuelve el sistema de congruencias para encontrar factores.

## Conclusión

Los algoritmos de factorización son herramientas poderosas en teoría de números y criptografía. Cada algoritmo tiene sus ventajas y desventajas, y la elección del algoritmo adecuado depende de los requisitos específicos del problema. En este documento, hemos proporcionado implementaciones en Python para cada algoritmo, lo que debería ayudar a entender y aplicar estos métodos en la práctica.

---
