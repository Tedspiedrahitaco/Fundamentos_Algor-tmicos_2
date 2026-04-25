# 📊 Taller Práctico: Ordenamiento Avanzado y Algoritmos Divide y Conquista

**Nivel:** Algoritmos Intermedios  
**Duración Estimada:** 8-10 horas  
**Objetivo:** Dominar algoritmos de ordenamiento eficiente y patrones arquitectónicos de clase mundial (Merge Sort, Quick Sort, DFS, BFS)

---

## 📋 Tabla de Contenidos

1. [Herramientas Requeridas](#herramientas-requeridas)
2. [Actividad 1: Configuración VS Code y Python Básico](#actividad-1-configuración-vs-code-y-python-básico)
3. [Actividad 2: Análisis Línea por Línea de Python](#actividad-2-análisis-línea-por-línea-de-python)
4. [Actividad 3: Reto Analítico de Script en Python](#actividad-3-reto-analítico-de-script-en-python)
5. [Actividad 4: Merge Sort - Divide y Conquista](#actividad-4-merge-sort---divide-y-conquista)
6. [Actividad 5: Quick Sort - Estrategia del Pivote](#actividad-5-quick-sort---estrategia-del-pivote)
7. [Actividad 6: Análisis DFS vs BFS con Flowgorithm](#actividad-6-análisis-dfs-vs-bfs-con-flowgorithm)
8. [Actividad 7: Comparativa de Algoritmos de Ordenamiento](#actividad-7-comparativa-de-algoritmos-de-ordenamiento)
9. [Rúbrica de Evaluación](#rúbrica-de-evaluación)
10. [Preguntas de Reflexión](#preguntas-de-reflexión-final)
11. [Entregables](#entregables-requeridos)

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

**Interfaz Clave:**
- Panel blanco central: Escritura de código
- Botón ▶ (arriba-izquierda): Ejecutar
- Panel inferior: Consola de salida
- `Escribir`: Imprime en consola
- `Leer`: Recibe entrada del usuario

### Flowgorithm - Diagramas de Flujo Interactivos

**Instalación:**
- Descarga desde: http://www.flowgorithm.org/download/
- Descomprime el `.zip` descargado
- Ejecuta `flowgorithm.exe` (Windows) o equivalente en tu SO

**Interfaz Clave:**
- Área blanca central: Lienzo de diseño
- Clic derecho en caja: Insertar estructura (Entrada, Salida, Proceso, Decisión)
- Botón ▶ Play: Ejecutar simulación
- Flechas entre cajas: Flujo de control

---

### Visual Studio Code y Entorno Python Básico

**Instalación y Configuración:**
1. Descarga VS Code desde: https://code.visualstudio.com/
2. Instala Python nativo desde: https://www.python.org/downloads/
3. Abre VS Code e instala las extensiones base (Python, Pylance, Code Runner).
4. Opcional: Vincula tu cuenta universitaria para GitHub Copilot y habilita tu entorno para integrar herramientas mediante MCP.

---

## 🎯 Actividad 1: Configuración VS Code y Python Básico

### Objetivo Pedagógico
Instalar y configurar el entorno de desarrollo profesional y asegurar su funcionamiento estructurando tu primer script lógico de Python puro.

### ¿Por Qué Es Importante?
Los algoritmos complejos no pueden ejecutarse sobre papel. Asegurar el funcionamiento del IDE y de las extensiones (como Prettier o Code Runner) elimina el 50% de las frustraciones tempranas por errores de sintaxis y te prepara para integrar Inteligencia artificial en tu flujo.

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Extensiones Esenciales y Setup
1. En VS Code abre el menú de Extensiones (`Ctrl+Shift+X`).
2. Asegúrate de instalar "Python" (Microsoft) y "Code Runner" (Jun Han).

#### Paso 2: Tu Primer Archivo en Python
Crea un archivo llamado `01_base_python.py` y digita lo siguiente para probar las condicionales y ciclos básicos:

```python
# Mi primera asimilación de variables, ciclos y funciones
def evaluar_numeros(lista):
    print("Iniciando análisis algorítmico...")
    for numero in lista:
        if numero % 2 == 0:
            print(f"[{numero}] - Cumple como condición de PAR")
        else:
            print(f"[{numero}] - Rechazado (IMPAR)")

# Declaramos nuestra lista y la procesamos
mis_numeros = [1, 2, 3, 4, 5, 8, 10]
evaluar_numeros(mis_numeros)
```

#### Paso 3: Ejecutar con Code Runner
En VS Code, presiona el botón "Play" arriba a la derecha. 
Deberás obtener una salida en tu consola inferior separando perfectamente los números pares de los impares. Si esto ocurre, ¡tu sistema y tu IDE están listos para la batalla!

#### Paso 4: Análisis Línea por Línea del Código (Desglose Estructural)
Para un ingeniero, ninguna línea de código es magia. Analiza esta traducción nativa a nivel conceptual:
- `def evaluar_numeros(lista):` -> Así se declara una función (una tarea autónoma empaquetada). `def` significa *define*. Lo que está en paréntesis es el insumo necesario (en este caso, un conjunto de datos llamado *lista*). Fíjate en los dos puntos `:` al final, que abren un bloque subordinado (hijo).
- `print(...)` -> El equivalente directo a `Escribir` en tu diagrama de flujo. Imprime texto o variables en la pantalla del usuario velozmente.
- `for numero in lista:` -> Un ciclo "Para" automático. Significa "Por cada elemento individual en el iterador, ejecuta repetidamente la rutina inferior". No necesitas configurar un tedioso `Con Paso 1 Hacer` como en PSeInt; Python lo infiere usando sus motores en C.
- `if numero % 2 == 0:` -> Condicional Clásico "Si". La expresión `%` se llama *Módulo* y no divide, sino que **extrae el residuo** de una división. Aquí la computadora pregunta: "Si al dividir por 2 lo que me sobra es nulo (0), entonces el número obligatoriamente es PAR".
- `else:` -> El infalible "Sino" de PSeInt. Atrapa incondicionalmente todos aquellos eventos matemáticos descartados por tu `if` primario. En este caso es el basurero que recolecta impares.
- `f"[{numero}] -..."` -> La 'f' inicial indica un *f-string* (format string). Es probablemente el truco más genial del lenguaje. Exime de engorrosas concatenaciones con signos de resta o suma. Permite insertar el valor de una variable viva directo en el texto si la rodeas de llaves `{}`.
- `mis_numeros = [...]` -> Usamos llaves cuadradas (`[]`) para estipular en memoria una lista (Arreglo o Matriz de 1D) sin requerir declaración rigurosa temporal.

---

## 🎯 Actividad 2: Reto Analítico de Script en Python

### Objetivo Pedagógico
Instanciar variables matemáticas nativamente, ensamblar bucles de control base `for`, e identificar la funcionalidad al modular problemas enrutados en funciones lógicas separadas.

### 📝 Instrucciones Paso a Paso
Crea un nuevo archivo `02_sumatoria_promedio.py` en tu IDE y escribe el siguiente algoritmo de facturación de productos. Léelo rigurosamente e intenta predecir qué hará el procesador en cada renglón antes de pulsar Play.

```python
def calcular_factura_final(precios):
    # Inicializamos celdas acumuladoras locales (PILA LIFO virtual)
    total_acumulado = 0
    cantidad_items = 0
    
    # Análisis cíclico de facturación
    for monto in precios:
        total_acumulado = total_acumulado + monto
        cantidad_items += 1  # Variante elegante corporativa de: cantidad = cantidad + 1
    
    # Condicional Catcher Error: Mitigación de riesgos para base datos vacía
    if cantidad_items == 0:
        print("Error Crítico: No hay métricos ni productos dictaminados")
        return # Expulsa al código de la función inmediatamente, parando el desastre
        
    promedio = total_acumulado / cantidad_items
    print(f"El cobro sistemático final es de: ${total_acumulado}")
    print(f"La dispersión matemática (promedio por producto): ${promedio}")

# Creamos la inyección en nuestro arreglo de precios de mercado
carrito_compras = [100.5, 45.0, 30.2, 500.0, 150.7]

print(">>> SISTEMA LOGÍSTICO DE FACTURACIÓN (ON) <<<")
calcular_factura_final(carrito_compras)
```
*Ejecuta este archivo usando el botón Play del Code Runner y evalúa matemáticamente si el script cumplió su propósito algorítmico y deduce qué papel jugó el `return` si hipotéticamente mandáramos una lista vacía `[]`.*

---

## 🎯 Actividad 4: Merge Sort - Divide y Conquista

### Objetivo Pedagógico
Implementar el algoritmo Merge Sort validando complejidad **O(n log n)** y comprendiendo el patrón "Divide y Conquista".

### ¿Por Qué Es Importante?
En sistemas empresariales con millones de registros, usar algoritmos primitivos como Bubble Sort ($O(n^2)$) pararía los servidores. Merge Sort garantiza rendimiento estable y predecible $O(n \log n)$ en TODOS los casos (mejor, peor y promedio), sacrificando solo $O(n)$ de memoria adicional.

**Comparación de Escala:**
- **Bubble Sort** con 1,000,000 usuarios: ~1 billón de operaciones
- **Merge Sort** con 1,000,000 usuarios: ~20 millones de operaciones
- **Mejora:** 99.998% ⚡

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Crear el Archivo Base
1. Abre PSeInt
2. Crea un nuevo archivo: `Archivo → Nuevo`
3. Guarda como: `MergeSort.psc`

#### Paso 2: Código a Implementar
Escribe el siguiente pseudocódigo en PSeInt:

```text
Algoritmo MergeSort
    // ============================================
    // PROCEDIMIENTO AUXILIAR: MEZCLA (MERGE)
    // ============================================
    Procedimiento Mezclar(arreglo, izq, medio, der)
        Definir izq_temp, der_temp, pos_temp Como Entero
        Definir temp, i Como Entero
        Dimension temp[100]
        
        izq_temp <- izq
        der_temp <- medio + 1
        pos_temp <- 1
        
        Mientras (izq_temp <= medio) Y (der_temp <= der) Hacer
            Si arreglo[izq_temp] <= arreglo[der_temp] Entonces
                temp[pos_temp] <- arreglo[izq_temp]
                izq_temp <- izq_temp + 1
            Sino
                temp[pos_temp] <- arreglo[der_temp]
                der_temp <- der_temp + 1
            FinSi
            pos_temp <- pos_temp + 1
        FinMientras
        
        Mientras izq_temp <= medio Hacer
            temp[pos_temp] <- arreglo[izq_temp]
            izq_temp <- izq_temp + 1
            pos_temp <- pos_temp + 1
        FinMientras
        
        Mientras der_temp <= der Hacer
            temp[pos_temp] <- arreglo[der_temp]
            der_temp <- der_temp + 1
            pos_temp <- pos_temp + 1
        FinMientras
        
        Para i <- izq Hasta der Con Paso 1 Hacer
            arreglo[i] <- temp[i - izq + 1]
        FinPara
    FinProcedimiento
    
    // ============================================
    // PROCEDIMIENTO PRINCIPAL: DIVIDE Y CONQUISTA
    // ============================================
    Procedimiento OrdenarMerge(arreglo, izq, der)
        Definir medio Como Entero
        Si izq < der Entonces
            medio <- TRUNC((izq + der) / 2)
            Escribir "Dividiendo: [", izq, "..", medio, "] y [", medio+1, "..", der, "]"
            OrdenarMerge(arreglo, izq, medio)
            OrdenarMerge(arreglo, medio+1, der)
            Mezclar(arreglo, izq, medio, der)
            Escribir "Mezclado: [", izq, "..", der, "]"
        FinSi
    FinProcedimiento
    
    // ============================================
    // PROGRAMA PRINCIPAL
    // ============================================
    Definir arreglo Como Entero
    Definir n, i Como Entero
    
    Dimension arreglo[10]
    
    // Inicializar arreglo desordenado
    arreglo[1] <- 38
    arreglo[2] <- 27
    arreglo[3] <- 43
    arreglo[4] <- 3
    arreglo[5] <- 9
    arreglo[6] <- 82
    arreglo[7] <- 10
    arreglo[8] <- 5
    arreglo[9] <- 65
    arreglo[10] <- 1
    
    n <- 10
    
    Escribir "╔════════════════════════════════════╗"
    Escribir "║       MERGE SORT VISUALIZADO       ║"
    Escribir "║    Divide y Conquista - O(n log n) ║"
    Escribir "╚════════════════════════════════════╝"
    Escribir ""
    Escribir "Arreglo ORIGINAL:"
    Para i <- 1 Hasta n Con Paso 1 Hacer
        Escribir arreglo[i], " " Sin Saltar
    FinPara
    Escribir ""
    Escribir ""
    
    OrdenarMerge(arreglo, 1, n)
    
    Escribir ""
    Escribir "Arreglo ORDENADO:"
    Para i <- 1 Hasta n Con Paso 1 Hacer
        Escribir arreglo[i], " " Sin Saltar
    FinPara
    Escribir ""
FinAlgoritmo
```

#### Paso 3: Ejecución y Pruebas
**Test Case 1: Ejecución Completa**
Ejecuta el programa (botón ▶). La salida esperada debería asemejarse visualmente a:

```text
╔════════════════════════════════════╗
║       MERGE SORT VISUALIZADO       ║
║    Divide y Conquista - O(n log n) ║
╚════════════════════════════════════╝

Arreglo ORIGINAL:
38 27 43 3 9 82 10 5 65 1 

Dividiendo: [1..5] y [6..10]
Dividiendo: [1..3] y [4..5]
Dividiendo: [1..1] y [2..3]
Mezclado: [1..3]
Dividiendo: [4..4] y [5..5]
Mezclado: [1..5]
...
Arreglo ORDENADO:
1 3 5 9 10 27 38 43 65 82
```

#### Paso 4: Análisis de Complejidad
Completa la siguiente tabla en tus apuntes o entorno de desarrollo:

| Métrica | Valor |
|---------|-------|
| Tamaño del arreglo (n) | 10 |
| Niveles de división | log₂(10) ≈ 3-4 |
| Operaciones totales | n × log n = 10 × 3.3 ≈ 33 |
| Complejidad Big O | O(n log n) |
| Complejidad Espacial | O(n) |
| Vs Bubble Sort (n²) | 10 × 10 = 100 ops |
| **Mejora** | 67% menos operaciones |

**Preguntas a considerar:**
- ¿Cuántos niveles de división necesita Merge Sort para un arreglo de 1,000 elementos? (Respuesta: log₂(1,000) ≈ 10 niveles)
- ¿Cuál es el costo de la memoria en Merge Sort y vale la pena? (Sí, O(n) memoria extra compensa con creces con la enorme ganancia de velocidad logarítmica).

---

## 🎯 Actividad 5: Quick Sort - Estrategia del Pivote

### Objetivo Pedagógico
Implementar Quick Sort usando partición por pivote y comprender la recursión generada a través del stack de llamadas.

### ¿Por Qué Es Importante?
Quick Sort es el algoritmo de ordenamiento más utilizado en la industria (implementado a nivel binario en Java, Python, C++):
- O(n log n) en promedio.
- O(log n) de memoria adicional (muy barato transaccionalmente).
- Mejor aprovechamiento o localidad de la memoria caché.
- Estadísticamente, es el más rápido de todos en la práctica asimétrica.

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Crear el Archivo Base
1. Abre PSeInt
2. Crea un nuevo archivo: `Archivo → Nuevo`
3. Guarda como: `QuickSort.psc`

#### Paso 2: Código a Implementar

```text
Algoritmo QuickSort
    // ============================================
    // PROCEDIMIENTO: PARTICIÓN POR PIVOTE
    // ============================================
    Procedimiento Particionar(arreglo, izq, der, pivote_idx)
        Definir pivote, izq_temp, der_temp, temp Como Entero
        
        pivote <- arreglo[pivote_idx]
        Escribir "Pivote seleccionado: ", pivote, " en índice ", pivote_idx
        
        // Intercambiar pivote al final temporalmente
        temp <- arreglo[pivote_idx]
        arreglo[pivote_idx] <- arreglo[der]
        arreglo[der] <- temp
        
        izq_temp <- izq
        der_temp <- der - 1
        
        Mientras izq_temp <= der_temp Hacer
            // Buscar elemento mayor o igual al pivote desde izquierda
            Mientras (izq_temp <= der_temp) Y (arreglo[izq_temp] < pivote) Hacer
                izq_temp <- izq_temp + 1
            FinMientras
            
            // Buscar elemento menor que pivote desde derecha
            Mientras (der_temp >= izq_temp) Y (arreglo[der_temp] >= pivote) Hacer
                der_temp <- der_temp - 1
            FinMientras
            
            // Intercambiar si encontramos cruce
            Si izq_temp < der_temp Entonces
                temp <- arreglo[izq_temp]
                arreglo[izq_temp] <- arreglo[der_temp]
                arreglo[der_temp] <- temp
            FinSi
        FinMientras
        
        // Colocar pivote en posición correcta
        temp <- arreglo[izq_temp]
        arreglo[izq_temp] <- arreglo[der]
        arreglo[der] <- temp
        
        Escribir "Partición completada. Pivote ahora en índice ", izq_temp
        
        // No manejaremos retorno directo aquí en Perfil Estricto con arreglos, 
        // usamos variable global 'nuevo_pivote_global' si es estrictamente necesario, 
        // pero la partición muta el arreglo.
    FinProcedimiento
    
    // NOTA: Para PSeInt estricto, el cruce y partición se adapta mejor con 
    // lógicas embebidas o variables super globales ya que no permite devolver enteros 
    // desde Procedimientos con matrices por referencia sin trucos. 
    // Adapta este esqueleto según tu avance en aula.
FinAlgoritmo
```

#### Paso 3: Ejecución y Pruebas
**Test Case: Ejecución Completa**
Ejecuta el programa y obsrva cómo se selecciona un número, la terminal reacomodará iterativamente todos los más pequeños a su izquierda, dejando el pivote fijo tras cada vuelta hasta llegar a estar todo organizado.

#### Paso 4: Tabla Comparativa Quick Sort vs Merge Sort

| Criterio | Quick Sort | Merge Sort |
|----------|------------|------------|
| Complejidad Promedio | O(n log n) | O(n log n) |
| Complejidad Peor Caso | O(n²) | O(n log n) |
| Memoria Adicional | O(log n) | O(n) |
| Localidad de Caché | Excelente | Buena |
| Uso Industria | 95% | 5% |
| Predecibilidad | Media | Alta |

---

## 📊 Actividad 6: Análisis DFS vs BFS con Flowgorithm

### Objetivo Pedagógico
Visualizar y comparar dos estrategias fundamentales de recorrido en topologías complejas y grafos: Recorrido en Profundidad (DFS) y Amplitud (BFS).

### ¿Por Qué Es Importante?
Las topologías modernas dictaminan tu entorno habitual:
- **GPS/Mapas:** Utilizan BFS para hallar la ruta incondicionalmente más corta.
- **Redes Sociales:** Utilizan DFS para rastrear ramificaciones lejanas o niveles de conexión de amistades.
- **Motores de Búsqueda de IA:** Basados conceptualmente en una fusión modular abstracta de ambos.

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Conceptualización Visual (Grafo de Pruebas)

Imagina esta Red de Ciudades o Familia:
```text
        A (Origen)
       / \
      B   C
     / \ / \
    D   E   F
         \
          G
```

- **Recorrido DFS (Profundidad - LIFO Stack):**
  - Estrategia: Sigue una rama agresivamente hasta el final de ella, retrocede y busca otra punta. 
  - Ruta de Ejemplo: `A → B → D → E → G → C → F`
- **Recorrido BFS (Amplitud - FIFO Queue):**
  - Estrategia: Cautelosa, explora todo mirando los alrededores perimetrales por capas.
  - Ruta de Ejemplo: `A → B → C → D → E → F → G`

#### Paso 2 & 3: Diseñar el diagrama de exploración (Pilas y Colas Cíclicas en Diagrama)
Debido a la topología abstracta requerirás trazar a papel o en sistema las estructuras "Mientras" evaluando condiciones base para desencolar y encolar como se vio en la Clase 2 usando diagramas base con ciclos apuntando a los niveles.

#### Paso 4: Tablas de Comparación Teórica y Modular

| Aspecto | DFS | BFS |
|---------|-----|-----|
| Estructura de Datos Base | Stack (Pila) | Queue (Cola) |
| Consumo de Memoria | Moderado | Alto (Debes retener el nivel local perimetral completo) |
| Encuentra Ciclos | Sí | Sí |
| Capaz de hallar Ruta Más Corta | No garantizado | Totalmente Garantizado |
| Complejidad | O(V + E) | O(V + E) |
| Mejor Escenario de Uso | Ir a la Profundidad máxima| Mapeo completo en Amplitud |

---

## ⚖️ Actividad 7: Comparativa de Algoritmos de Ordenamiento

### Objetivo Pedagógico
Ejecutar el letárgico Bubble Sort vs Merge/Quick Sort sobre el mismo dataset, visualizando en vivo diferencias de rendimiento.

### 📝 Instrucciones Paso a Paso

#### Paso 1: Construir el Bubble Sort en PSeInt
Archivo: `BubbleSort.psc`

```text
Algoritmo BubbleSort
    // ============================================
    // BÚSQUEDA LINEAL - O(n²) - JAMÁS USAR EN PRODUCCIÓN
    // ============================================
    Definir arreglo Como Entero
    Definir n, i, j, temp, comparaciones Como Entero
    
    Dimension arreglo[10]
    
    arreglo[1] <- 64; arreglo[2] <- 34; arreglo[3] <- 25; arreglo[4] <- 12; arreglo[5] <- 22; 
    arreglo[6] <- 11; arreglo[7] <- 90; arreglo[8] <- 88; arreglo[9] <- 45; arreglo[10] <- 50
    
    n <- 10
    comparaciones <- 0
    
    Escribir "=== BUBBLE SORT - O(n²) ==="
    Escribir "Arreglo original:"
    Para i <- 1 Hasta n Con Paso 1 Hacer
        Escribir arreglo[i], " " Sin Saltar
    FinPara
    Escribir ""
    
    // Ciclo Bubble Sort Estándar
    Para i <- 1 Hasta n - 1 Con Paso 1 Hacer
        Para j <- 1 Hasta n - i Con Paso 1 Hacer
            comparaciones <- comparaciones + 1
            Si arreglo[j] > arreglo[j + 1] Entonces
                temp <- arreglo[j]
                arreglo[j] <- arreglo[j + 1]
                arreglo[j + 1] <- temp
            FinSi
        FinPara
    FinPara
    
    Escribir "Arreglo ordenado:"
    Para i <- 1 Hasta n Con Paso 1 Hacer
        Escribir arreglo[i], " " Sin Saltar
    FinPara
    Escribir ""
    Escribir "Total de comparaciones internas: ", comparaciones
    Escribir "Complejidad: O(n²) = ", n * n
FinAlgoritmo
```

#### Paso 2 & 3: Evaluar Ejecución y Comparación Tabulada

Toma los métricos del "Bubble Sort (O(n²))", sus casi 45+ cruces transaccionales y compáralos si corrieras tu "Merge o Quick" de las secciones pasadas:

| Algoritmo | Comparaciones Observadas | Complejidad | Industria |
|-----------|--------------------------|-------------|-----------|
| **Bubble Sort** | 45 | O(n²) | ❌ Prohibido |
| **Selection Sort** | 45 | O(n²) | ❌ Prohibido |
| **Merge Sort** | ~33 | O(n log n) | ✅ Garantizado |
| **Quick Sort** | ~28 | O(n log n) | ✅ Estándar y Preferido |

#### Paso 4: Análisis Escalable Masivo (1 Millón de Usuarios N=1,000,000)

| Algoritmo | Operaciones Estipuladas | Tiempo Estimado Ficticio |
|-----------|-------------------------|--------------------------|
| **Bubble Sort** | 1,000,000,000,000 (1 Billón) | ~16 a 20 Minutos ⚠️ |
| **Merge / Quick Sort** | ~20,000,000 (20 Millones)| ~15 a 20 Milisegundos ✅ |

**Conclusión Base:** La diferencia entre O(n²) y O(n log n) es la diferencia absoluta entre un sistema o servidor "congelado/inutilizable" y un sistema "veloz en tiempo real".

---

## 📋 Rúbrica de Evaluación

### Criterios Generales (Aplica a todas las actividades)

| Criterio | Excelente (5) | Bueno (4) | Aceptable (3) | Deficiente (≤2) |
|----------|---------------|-----------|---------------|-----------------|
| **Compilación y Bugs** | Ejecuta sin errores todos los casos | 1 o 2 fallos ignorables | Ejecución a medias con errores | No ejecuta |
| **Arquitectura de Código** | Formulación excelente, variables legibles | Buena estructura base | Confuso, nombres pobres | Spaghetti puro |
| **Análisis de Límite Matemático** | Deduce e informa justificación pura asintótica | Matemática asimilada correcta | Intento de análisis superficial | Negado Ausente |

### Criterios de Asignación Particular

| Entregable | Puntos Globales |
|------------|-----------------|
| Funcionalidad y particiones de Algoritmo Merge Sort | 25 Pts |
| Entendimiento recursivo e intercambios de Pivote Quick Sort | 25 Pts |
| Correcta estipulación conceptual de Modelos BFS y DFS en grafo | 25 Pts |
| Comparativa de rendimientos con métricas tangibles contra algoritmos malos | 25 Pts |

---

## 🎓 Preguntas de Reflexión Final

### Nivel 1: Comprensión y Aprobación
1. ¿A qué se refiere conceptualmente o fácticamente la premisa *"Divide y Conquista"*? (R: A despedazar cíclicamente vectores muy abrumadores en problemas unitarios elementales que se resuelven solos).
2. ¿Por qué es inadmisible y prohibitivo desplegar el algoritmo de burbuja (Bubble Sort) en un banco? 

### Nivel 2: Aplicación y Adaptabilidad
1. Si te exigen por límite que ocupes casi `Nula RAM (O(log n))` extra en tu servidor. ¿Invocas Quick Sort o Merge Sort?
2. Si te dicen que todos los apellidos llegan por letras locas y requieres obligatoriamente la vía más rápida (BFS). ¿Lo montas en FIFO o en LIFO?

---

## 📦 Entregables Requeridos

### Estructura Mandatoria a la hora de Entrega TALLER_SOLUCION/:

```text
TALLER_SOLUCION/
├── Actividad1_MergeSort.psc
├── Actividad2_QuickSort.psc
├── Actividad3_DFS_Diagrama_Explicativo.txt o .fsg
├── Actividad4_BubbleSort_y_Comparativa.psc
└── REPORTE_FINAL.md
```

### El Archivo Documental de Respaldo (`REPORTE_FINAL.md`):

```markdown
# Reporte Final - Taller de Ordenamiento Avanzado

## Resumen Ejecutivo de Base Lógica Analítica
[2 Párrafos sintetizando por qué lograste la mejora transaccional frente al O(n^2)]

## Actividades Evaluadas (Merge Sort y Quick Sort)
- Merge Sort Comportamiento: [Detalla tus deducciones tras verlo actuar en Consola]
- Quick Sort Modificación: [Explica a consciencia qué es lo que hace y aisla tu pivote central]

## Análisis Modular 
- Grafos: [Plasma tu entendimiento sobre en qué circunstancias aplicará DFS contra BFS]
- Conclusión Operacional Base 1 Millón Récords: [Escribe la comparativa total y por qué esto define la infraestructura de una nube]
```

---

## 💡 Consejos Finales y Direccionamiento a Analistas

**✅ HACES REQUERIMIENTOS CORRECTOS CUANDO:**
- Visualizas tu arreglo cortándose por la mitad una y otra vez mentalmente.
- Proyectas tu número de clientes hipotéticos a niveles demográficos irreales para testar (millones).

**❌ EVITA A TODA COSTA:**
- Sentarse a escribir sin tener el diagrama mental de cruzamiento iteracional dibujado en un boceto básico.
- Mezclar lógicamente de qué trata un sistema que va profundo hasta toparse pared, vs sistemas de "Capa en Capa" como la cebolla. Piense antes de ejecutar.
