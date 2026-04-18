# 📊 Taller Práctico: Programación Dinámica y Técnicas de Optimización Algorítmica

**Nivel:** Algoritmos Avanzados - Optimización  
**Duración Estimada:** 8-10 horas  
**Objetivo:** Dominar Programación Dinámica (DP), Memorización, Tabulación y diferenciar con enfoques Greedy (Avaro)

---

## 📋 Tabla de Contenidos

1. [Herramientas Requeridas](#herramientas-requeridas)
2. [Conceptos Fundamentales](#conceptos-fundamentales)
3. [Actividad 1: Fibonacci - Memorización Top-Down](#actividad-1-fibonacci---memorización-top-down)
4. [Actividad 2: Tabulación Bottom-Up](#actividad-2-tabulación-bottom-up)
5. [Actividad 3: Problema del Cambio - Greedy vs DP](#actividad-3-problema-del-cambio---greedy-vs-dp)
6. [Actividad 4: Auditoría Comparativa de Rendimiento](#actividad-4-auditoría-comparativa-de-rendimiento)
7. [Rúbrica de Evaluación](#rúbrica-de-evaluación)
8. [Preguntas de Reflexión](#preguntas-de-reflexión-final)
9. [Entregables](#entregables-requeridos)

---

## 🛠️ Herramientas Requeridas

### PSeInt - Pseudocódigo Estructurado

**Instalación:**
- Descarga desde: http://pseint.sourceforge.net/
- Selecciona la versión compatible con tu SO (Windows/Linux/macOS)
- Ejecuta el instalador y sigue: Siguiente → Siguiente → Instalar

**Configuración Inicial:**
1. Abre PSeInt
2. Ve a **Configurar → Opciones**
3. Selecciona **Perfil: Estricto** (modo educativo riguroso)
4. Acepta cambios

### Replit - Entorno Colaborativo en la Nube

**¿Por qué Replit?**
- Ejecución inmediata sin instalación local
- Colaboración en tiempo real con compañeros
- Ideal para auditoría y debugging compartido
- Acceso desde cualquier dispositivo

**Setup Inicial:**
1. Ve a: https://replit.com/
2. Crea cuenta gratuita
3. Click "Create Repl"
4. Selecciona lenguaje: **Python** (recomendado para DP)
5. Nombra tu proyecto: `taller-programacion-dinamica`

**Para trabajar en equipo:**
- Click en botón "Share" (arriba derecha)
- Copia el link o invita por email
- ¡Tú y tu compañero pueden programar simultáneamente!

---

## 🎓 Conceptos Fundamentales

### ¿Qué es Programación Dinámica?
Programación Dinámica es una técnica de optimización que:
1. Descompone un problema complejo en subproblemas más pequeños
2. Almacena resultados intermedios (Caché) para evitar recálculos
3. Reutiliza esos resultados cuando los vuelva a necesitar

> **Principio de Bellman:** "Si recalculas lo mismo dos veces, tu código es ineficiente"

### Dos Condiciones Necesarias para DP
Para saber si DP es aplicable, verifica:

| Condición | Explicación | Ejemplo |
|-----------|-------------|---------|
| **Subestructura Óptima** | El problema grande se resuelve combinando soluciones pequeñas óptimas | Fibonacci: `f(n) = f(n-1) + f(n-2)` |
| **Subproblemas Superpuestos** | El mismo subproblema se calcula múltiples veces | Fibonacci: `f(3)` se calcula 3 veces en `f(5)` |

### Dos Enfoques de Implementación

**1. Memorización (Top-Down)**
- **Estrategia:** Recursión + Caché
- **Flujo:** De arriba hacia abajo, almacenando resultados
- **Estructura:** Array o diccionario para caché
- **Ventaja:** Intuitivo, solo resuelve subproblemas necesarios
- **Desventaja:** Riesgo de Stack Overflow en recursión profunda

**2. Tabulación (Bottom-Up)**
- **Estrategia:** Iteración + Tabla
- **Flujo:** De abajo hacia arriba, construyendo soluciones
- **Estructura:** Arrays 1D o 2D
- **Ventaja:** No hay recursión, muy eficiente en memoria
- **Desventaja:** Requiere entender el patrón desde el inicio

### Greedy (Avaro) vs Programación Dinámica

| Criterio | Greedy | DP |
|----------|--------|----|
| **Enfoque** | Elige lo mejor en cada paso | Considera todas las opciones |
| **Garantía Óptima** | ❌ NO siempre | ✅ SÍ (si cumple DP) |
| **Velocidad** | ⚡ Ultra rápido `O(n log n)` | 🐢 Más lento `O(n)` o `O(n²)` |
| **Memoria** | Mínima `O(1)` | Más `O(n)` |
| **Casos de Uso**| Dijkstra, Huffman, Monedas (casos EE.UU) | Fibonacci, Cambio Complejo, Mochila |

---

## 🎯 Actividad 1: Fibonacci - Memorización Top-Down

### Objetivo Pedagógico
Comparar Fibonacci recursivo puro vs Fibonacci optimizado con memorización, visualizando la explosión de llamadas recursivas.

### ¿Por Qué Es Importante?
Fibonacci es el ejemplo clásico de por qué DP existe:
- **Recursión pura:** `O(2ⁿ)` - Explosivo, inviable
- **Memorización:** `O(n)` - Lineal, manejable
- Mejoa para `n=40`: De ~1 billón de operaciones a ~40 operaciones.

### 📝 Instrucciones Paso a Paso

#### Paso 1: Crear en Replit
1. Ve a https://replit.com/
2. Click "Create Repl"
3. Selecciona **Python**
4. Nombre: `Fibonacci_Memorizacion`

#### Paso 2: Código Recursión Pura (SIN DP) - EL PROBLEMA

```python
# ============================================
# FIBONACCI PURO RECURSIVO - O(2^n) - MALO
# ============================================

def fibonacci_puro(n):
    """Recursión sin optimización. ¡NUNCA uses esto en producción!"""
    if n <= 1:
        return n
    return fibonacci_puro(n - 1) + fibonacci_puro(n - 2)

# Prueba
print("=== FIBONACCI PURO (SIN DP) ===")
print(f"fib(35) = {fibonacci_puro(35)}")
print("Nota: ¡Tarda varios segundos!")
print()
```

**Salida esperada:**
```text
=== FIBONACCI PURO (SIN DP) ===
fib(35) = 9227465
Nota: ¡Tarda varios segundos!
```

#### Paso 3: Código Memorización (CON DP) - LA SOLUCIÓN

```python
# ============================================
# FIBONACCI CON MEMORIZACIÓN - O(n) - BUENO
# ============================================

def fibonacci_memo(n, cache=None):
    """Recursión optimizada con caché/memorización"""
    
    # Inicializar caché si es la primera llamada
    if cache is None:
        cache = {}
    
    # Base case
    if n <= 1:
        return n
    
    # ¡AQUÍ ESTÁ LA MAGIA!
    # Antes de calcular, verificamos si ya lo tenemos en caché
    if n in cache:
        print(f"  → Caché hit para f({n}), retornando {cache[n]}")
        return cache[n]
    
    # Si no está en caché, calculamos y guardamos
    print(f"  → Calculando f({n})")
    cache[n] = fibonacci_memo(n - 1, cache) + fibonacci_memo(n - 2, cache)
    
    return cache[n]

# Prueba
print("=== FIBONACCI CON MEMORIZACIÓN (TOP-DOWN) ===")
resultado = fibonacci_memo(10)
print(f"fib(10) = {resultado}")
print("Nota: ¡Instantáneo!")
print()
```

**Salida esperada (recortada):**
```text
=== FIBONACCI CON MEMORIZACIÓN (TOP-DOWN) ===
  → Calculando f(10)
  → Calculando f(9)
  → Calculando f(8)
  ...
  → Caché hit para f(2)
  → Caché hit para f(3)
  ...
fib(10) = 55
Nota: ¡Instantáneo!
```

#### Paso 4: Comparación de Rendimiento

Agrega esto al final de tu proyecto Replit:

```python
import time

# ============================================
# COMPARATIVA: PURO vs MEMORIZACIÓN
# ============================================

print("\n=== AUDITORÍA DE RENDIMIENTO ===")

# Test 1: Fibonacci 35
print("\nTest: fib(35)")

# Puro (advertencia: tarda mucho)
print("Puro (SIN DP):", end=" ")
start = time.time()
try:
    result_puro = fibonacci_puro(35)
    end = time.time()
    print(f"Resultado={result_puro}, Tiempo={end-start:.2f}s")
except:
    print("Timeout o error")

# Memorización
print("Memorización (CON DP):", end=" ")
start = time.time()
result_memo = fibonacci_memo(35)
end = time.time()
print(f"Resultado={result_memo}, Tiempo={end-start:.4f}s")

# Test 2: Fibonacci 50
print("\nTest: fib(50)")
print("Puro: Imposible (tomaría horas)")
print("Memorización:", end=" ")
start = time.time()
result_memo = fibonacci_memo(50)
end = time.time()
print(f"Resultado={result_memo}, Tiempo={end-start:.4f}s")

print("\n=== CONCLUSIÓN ===")
print("Mejora: De O(2^n) a O(n)")
print("Para n=50: De ~1 billón operaciones a ~50 operaciones")
```

#### Paso 5: Tabla de Análisis
Completa esta tabla en tus apuntes ejecutando el código:

| n | Puro (s) | Memo (s) | Mejora | Llamadas Puro | Llamadas Memo |
|---|----------|----------|--------|---------------|---------------|
| 20 | ~0.01 | ~0.0001 | 100x | 21,891 | 21 |
| 30 | ~3 | ~0.0002 | 15,000x | 2.1M | 30 |
| 35 | ~50 | ~0.0003 | 166,000x | 29.8M | 35 |
| 40 | ~500+ | ~0.0004 | 1,250,000x| 331M | 40 |

---

## 🎯 Actividad 2: Tabulación Bottom-Up

### Objetivo Pedagógico
Implementar Fibonacci usando iteración pura (sin recursión), evitando problemas de Stack Overflow.

### ¿Por Qué Es Importante?
- Evita completamente problemas de recursión profunda
- A veces es más eficiente en memoria que la propia memorización
- Mejor para sistemas con limitaciones estrictas de "stack".

### 📝 Instrucciones Paso a Paso

#### Paso 1: Código Tabulación Iterativa
En el mismo Replit, agrega:

```python
# ============================================
# FIBONACCI CON TABULACIÓN - O(n) - MEJOR
# ============================================

def fibonacci_tabla(n):
    """
    Tabulación (Bottom-Up): Construimos tabla desde abajo hacia arriba.
    Sin recursión, solo iteración.
    """
    
    # Crear tabla para almacenar resultados
    tabla = [0] * (n + 1)
    
    # Casos base
    tabla[0] = 0
    if n >= 1:
        tabla[1] = 1
    
    print(f"Inicializando tabla: {tabla}")
    print()
    
    # Llenar tabla iterativamente de abajo hacia arriba
    for i in range(2, n + 1):
        tabla[i] = tabla[i - 1] + tabla[i - 2]
        print(f"tabla[{i}] = tabla[{i-1}] + tabla[{i-2}] = {tabla[i-1]} + {tabla[i-2]} = {tabla[i]}")
    
    print()
    print(f"Tabla final: {tabla}")
    return tabla[n]

# Prueba
print("=== FIBONACCI CON TABULACIÓN (BOTTOM-UP) ===")
resultado = fibonacci_tabla(10)
print(f"fib(10) = {resultado}")
print()

# Comparativa de espacios de tabla
print("=== OPTIMIZACIÓN DE ESPACIO ===")
def fibonacci_tabla_optimizado(n):
    """Tabulación optimizada: solo almacenamos últimos 2 valores"""
    if n <= 1:
        return n
    
    prev2 = 0  # fib(0)
    prev1 = 1  # fib(1)
    
    for i in range(2, n + 1):
        actual = prev1 + prev2
        prev2 = prev1
        prev1 = actual
    
    return prev1

print("Versión optimizada (O(1) memoria):")
print(f"fib(50) = {fibonacci_tabla_optimizado(50)}")
print("Memoria usada: Solo 2 variables (O(1))")
print()
```

#### Paso 2: Tabla Comparativa de Enfoques

| Criterio | Memorización (Top-Down) | Tabulación (Bottom-Up) | Ganador |
|----------|-----------------------|-----------------------|---------|
| Complejidad Tiempo | O(n) | O(n) | Empate |
| Complejidad Espacio | O(n) | O(n) o O(1) opt | Tabulación opt |
| Riesgo Stack Overflow| Posible si N es gigante| Nulo | Tabulación |
| Recursión | Sí | No | Memorización (si odias iterar) |

---

## 🎯 Actividad 3: Problema del Cambio - Greedy vs DP

### Objetivo Pedagógico
Comparar enfoque Greedy (Avaro) con Programación Dinámica en un problema práctico: Buscar el mínimo de monedas para dar cambio.

### ¿Por Qué Es Importante?
Este es un caso donde:
✅ **Greedy** funciona a veces (EUA: 1, 5, 10, 25)
❌ **Greedy** FALLA espectacularmente en otros sistemas (EJ: monedas [1, 6, 10] para dar 14)
✅ **DP** funciona SIEMPRE optimizando.

### 📝 Instrucciones Paso a Paso

#### Paso 1: Implementar Greedy (Avaro) y Detectar el Fallo

```python
# ============================================
# PROBLEMA DEL CAMBIO: GREEDY (AVARO)
# ============================================

def cambio_greedy(monto, monedas):
    """
    Enfoque Avaro: Toma siempre la moneda más grande disponible.
    ¡FALLA en muchos casos asimétricos!
    """
    monedas_sorted = sorted(monedas, reverse=True)  # Mayor a menor
    resultado = []
    
    for moneda in monedas_sorted:
        while monto >= moneda:
            resultado.append(moneda)
            monto -= moneda
    
    return resultado, monto  # monto restante

# Prueba Case 1: Sistema estándar
print("=== GREEDY: CAMBIO CON MONEDAS ===\n")
print("Case 1: Monedas [1,5,10,25], Monto=41")
monedas1 = [1, 5, 10, 25]
resultado1, restante1 = cambio_greedy(41, monedas1)
print(f"Greedy selecciona: {resultado1} (Total: {len(resultado1)})")

# Prueba Case 2: Sistema problemático (El Fallo Avaro)
print("\nCase 2: Monedas [1,6,10], Monto=14")
monedas2 = [1, 6, 10]
resultado2, restante2 = cambio_greedy(14, monedas2)
print(f"Greedy selecciona: {resultado2} (Total: {len(resultado2)})")

print("\n⚠️ PROBLEMA: Greedy toma [10,1,1,1,1] = 5 monedas")
print("             Pero lo óptimo es [6,6,1,1] = 4 monedas")
print("             Greedy FALLA: Usa 5 en lugar de 4\n")
```

#### Paso 2: Implementar Programación Dinámica

```python
# ============================================
# PROBLEMA DEL CAMBIO: PROGRAMACIÓN DINÁMICA
# ============================================

def cambio_dp(monto, monedas):
    """DP Bottom-Up: Garantiza MÍNIMA cantidad de monedas."""
    
    # Tabla: dp[i] = mínimo número de monedas para hacer el monto i
    dp = [float('inf')] * (monto + 1)
    dp[0] = 0  # Base: 0 monedas para monto 0
    
    # Traza: qué moneda usamos para llegar a i
    dp_trace = [-1] * (monto + 1)
    
    # Llenar tabla DP
    for i in range(1, monto + 1):
        for moneda in monedas:
            if moneda <= i and dp[i - moneda] + 1 < dp[i]:
                dp[i] = dp[i - moneda] + 1
                dp_trace[i] = moneda
    
    # Reconstruir la solución
    solucion = []
    actual = monto
    while actual > 0:
        moneda_usada = dp_trace[actual]
        solucion.append(moneda_usada)
        actual -= moneda_usada
    
    return solucion, dp[monto]

print("=== PROGRAMACIÓN DINÁMICA: CAMBIO CON MONEDAS ===\n")
resultado_dp2, total_dp2 = cambio_dp(14, [1, 6, 10])
print(f"DP selecciona: {resultado_dp2} (Total: {total_dp2})")
print("\n✅ DP GANA: Usa 4 monedas vs 5 del modo Greedy")
```

---

## ⚖️ Actividad 4: Auditoría Comparativa de Rendimiento

### Objetivo Pedagógico
Medir el rendimiento real entre diferentes enfoques y datasets masivos.

```python
# ============================================
# AUDITORÍA COMPLETA: RENDIMIENTO Y VIABILIDAD
# ============================================
import time

print("\n╔════════════════════════════════════════════════════════════╗")
print("║  AUDITORÍA: PROGRAMACIÓN DINÁMICA vs OTRAS TÉCNICAS        ║")
print("╚════════════════════════════════════════════════════════════╝\n")

print("TEST 1: RESUMEN DE COMPLEJIDADES")
print("─" * 80)
print(f"{'Algoritmo':25} | {'Tiempo':10} | {'Espacio':15} | Viabilidad")
print("─" * 80)
print(f"{'Fibonacci Puro':25} | {'O(2^n)':10} | {'O(n) stack':15} | Solo N<35")
print(f"{'Fibonacci Memo':25} | {'O(n)':10} | {'O(n) cache':15} | Muy Alta")
print(f"{'Fibonacci Tabla':25} | {'O(n)':10} | {'O(n) tabla':15} | Muy Alta")
print(f"{'Cambio Monedas Greedy':25} | {'O(m log m)':10} | {'O(1)':15} | Falla precisión")
print(f"{'Cambio Monedas DP':25} | {'O(n*m)':10} | {'O(n) tabla':15} | Garantizado óptimo")

print("\nCONCLUSIÓN: Programación Dinámica es superior al garantizar")
print("soluciones óptimas tangibles, sacrificando solo un mínimo de memoria.")
```

---

## 📋 Rúbrica de Evaluación

### Criterios Generales

| Criterio | Excelente (5) | Bueno (4) | Aceptable (3) | Mejora Requerida (≤2) |
|----------|--------------|----------|--------------|----------------------|
| **Código Funciona** | Resultados perfectos y limpios | 1-2 bugs menores | Funciona a medias | Falla constante |
| **Comprensión DP** | Diferencia Memo vs Tabla exacto | Entiende conceptos | Ligeramente confuso | No asimila |
| **Optimización Greedy** | Reconoce su falla sistemática | Reconoce mayoría | Duda en casos | No diferencia |

---

## 🎓 Preguntas de Reflexión Final

### Nivel 1: Comprensión
1. **¿Cuál es la diferencia fundamental entre memorización y tabulación?**
   R: Memorización (Top-Down, Recursiva, perezosa). Tabulación (Bottom-Up, Iterativa, proactiva).
2. **¿Por qué Fibonacci recursivo puro es O(2ⁿ)?**
   R: Porque cada llamada clona dos ramas inútilmente recalculando el mismo subárbol infinitas veces.

### Nivel 2: Aplicación
3. **¿Cuál técnica usarías para calcular el 100º número de Fibonacci?**
   R: Tabulación. Superaríamos el Stack Memory límite nativo de recursión en Memoria (Top-Down) dependiendo del compilador.
4. **¿En qué casos NO puedes usar Greedy?**
   R: Cuando el óptimo local entorpece un global (Como agarrar la de 10 primero en el arreglo de [1, 6, 10] para dar 14).

---

## 📦 Entregables Requeridos

### Carpeta de Entrega: `/TALLER_SOLUCION/`

```text
TALLER_SOLUCION/
├── Actividad1_Fibonacci_TopDown.py
├── Actividad2_Fibonacci_BottomUp.py
├── Actividad3_Cambio_Greedy_vs_DP.py
├── Actividad4_Auditoria_Completa.py
├── REPLIT_LINK.txt
│   └── (Enlace compartido de tu proyecto en Replit)
└── REPORTE_FINAL.md
```

### Formato esperado en `REPORTE_FINAL.md`

```markdown
# Reporte Final - Taller de Programación Dinámica

## Resumen Ejecutivo
[Escribe 2-3 párrafos sobre programación dinámica y su impacto]

## Actividad 1 y 2: Fibonacci Optimizados
- Explicación de Memorización vs Tabulación: [Tus argumentos]
- Rendimiento Observado: [Comprueba con datos]

## Actividad 3: La Falacia Greedy
- Casos documentados de fallo de Greedy contra DP: [Ejemplificando su ruptura]

## Conclusiones Industriales
[¿Vale la pena ocupar más memoria RAM O(n) por ahorrar 20 minutos de proceso y pasarlo a milisegundos? Argumenta].
```

---

## 💡 Consejos para Analistas

*   **DIBUJA ÁRBOLES:** No memorices DP, dibuja la recursión y entiende el camino.
*   **PRUEBA EL GREEDY:** A veces la programación ávara (Greedy) es suficiente si la empresa define reglas muy cerradas; no la odies.
*   **O(2ⁿ) ES EL ENEMIGO:** Jamás subas a un entorno corporativo un algoritmo exponencial desnudo.
