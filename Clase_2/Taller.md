# 📊 Taller Práctico: Análisis y Diseño de Algoritmos Base

**Nivel:** Fundamentos de Algoritmia  
**Duración Estimada:** 6-8 horas  
**Objetivo:** Dominar notación asintótica, búsqueda optimizada, recursividad y estructuras de datos

---

## 📋 Tabla de Contenidos

1. [Herramientas Requeridas](#herramientas-requeridas)
2. [Actividad 1: Búsqueda Binaria con PSeInt](#actividad-1-búsqueda-binaria-con-pseint)
3. [Actividad 2: Análisis de Complejidad con Flowgorithm](#actividad-2-análisis-de-complejidad-con-flowgorithm)
4. [Actividad 3: Simulador de Colas FIFO](#actividad-3-simulador-de-colas-fifo)
5. [Actividad 4: Comparativa Linear vs Binaria](#actividad-4-comparativa-linear-vs-binaria)
6. [Rúbrica de Evaluación](#rúbrica-de-evaluación)
7. [Preguntas de Reflexión](#preguntas-de-reflexión-final)
8. [Entregables](#entregables-requeridos)

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

---

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

## 🎯 Actividad 1: Búsqueda Binaria con PSeInt

### Objetivo Pedagógico
Implementar el algoritmo de búsqueda binaria validando complejidad **O(log n)** frente a búsqueda lineal **O(n)**.

### ¿Por Qué Es Importante?
En sistemas bancarios con millones de cuentas, una búsqueda lineal pararía servidores de tiempo crítico. La búsqueda binaria divide el problema logarítmicamente, reduciendo millones de operaciones a apenas ~20 comparaciones.

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Crear el Archivo Base
1. Abre PSeInt
2. Crea un nuevo archivo: `Archivo → Nuevo`
3. Guarda como: `BusquedaBinaria.psc`

#### Paso 2: Código a Implementar

Escribe el siguiente pseudocódigo en PSeInt:

```pseint
Algoritmo BusquedaBinaria
	Definir registros Como Entero;
	Definir inicio, final, mitad, meta Como Entero;
	Definir encontrado Como Logico;
	Definir i Como Entero;

	Dimension registros[8];
	registros[0] <- 1002;
	registros[1] <- 1045;
	registros[2] <- 2098;
	registros[3] <- 3301;
	registros[4] <- 3311;
	registros[5] <- 4005;
	registros[6] <- 5020;
	registros[7] <- 6081;

	encontrado <- Falso;

	Escribir "=== SISTEMA BÚSQUEDA BINARIA ===";
	Escribir "Registros disponibles:";
	Escribir "1002, 1045, 2098, 3301, 3311, 4005, 5020, 6081";
	Escribir "";
	Escribir "Ingrese el número de registro a localizar:";
	Leer meta;

	inicio <- 0;
	final <- 7;

	Mientras (inicio <= final) Y (encontrado = Falso) Hacer
		mitad <- TRUNC((inicio + final) / 2);
		
		Escribir "Comparando con posición ", mitad, ": ", registros[mitad];
		
		Si registros[mitad] = meta Entonces
			Escribir "";
			Escribir "✓ ¡ÉXITO! Registro localizado";
			Escribir "Posición en el sistema: ", mitad;
			Escribir "Valor del registro: ", registros[mitad];
			encontrado <- Verdadero;
		Sino
			Si registros[mitad] < meta Entonces
				Escribir "  → Buscando en mitad superior";
				inicio <- mitad + 1;
			Sino
				Escribir "  → Buscando en mitad inferior";
				final <- mitad - 1;
			FinSi;
		FinSi;
	FinMientras;

	Si encontrado = Falso Entonces
		Escribir "";
		Escribir "✗ ERROR: Registro ", meta, " no existe en la base de datos";
	FinSi;
FinAlgoritmo
```

#### Paso 3: Ejecución y Pruebas

**Test Case 1 (Caso Éxito):**
- Ejecuta el programa (botón ▶)
- Ingresa: `3301`
- **Salida esperada:**
```text
Comparando con posición 3: 3301 
✓ ¡ÉXITO! Registro localizado 
Posición en el sistema: 3 
Valor del registro: 3301
```

**Test Case 2 (Caso No Encontrado):**
- Ejecuta nuevamente
- Ingresa: `9999`
- **Salida esperada:**
```text
Comparando con posición 3: 3301 → Buscando en mitad superior 
Comparando con posición 5: 4005 → Buscando en mitad superior 
Comparando con posición 6: 5020 → Buscando en mitad superior 
Comparando con posición 7: 6081 → Buscando en mitad superior 
✗ ERROR: Registro 9999 no existe en la base de datos
```

#### Paso 4: Análisis de Complejidad

Completa la siguiente tabla en un documento aparte:

| Métrica | Valor |
|---------|-------|
| **Tamaño del arreglo (n)** | 8 |
| **Iteraciones máximas esperadas** | ceil(log₂ 8) = 3 |
| **Iteraciones reales (peor caso)** | _(Tú contarás del test)_ |
| **Complejidad Big O** | O(log n) |
| **Comparaciones vs búsqueda lineal** | Binaria: ~3 vs Lineal: ~8 |

---

### 🎓 Preguntas de Reflexión

1. **¿Cuántas comparaciones se hacen al buscar 6081 en ambos algoritmos?**
   - Binaria: 4 comparaciones (3 → 5 → 6 → 7)
   - Lineal: 8 comparaciones (recorrer todo)

2. **¿Qué sucedería si el arreglo tuviera 1 millón de registros?**
   - Binaria: log₂(1,000,000) ≈ 20 comparaciones
   - Lineal: Hasta 1,000,000 comparaciones ⚠️

3. **¿Es obligatorio que el arreglo esté ordenado? ¿Por qué?**
   - **SÍ.** La búsqueda binaria divide por la mitad asumiendo valores menores a la izquierda y mayores a la derecha.

---

## 📊 Actividad 2: Análisis de Complejidad con Flowgorithm

### Objetivo Pedagógico
Modelar visualmente algoritmos iterativos y validar cálculos de complejidad mediante diagramas de flujo.

### ¿Por Qué Es Importante?
Los diagramas de flujo te permiten:
- Visualizar ramificaciones lógicas
- Contar iteraciones manualmente
- Validar condiciones de parada
- Documentar decisiones de diseño

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Crear el Diagrama de Búsqueda Lineal

1. Abre **Flowgorithm**
2. Crea un nuevo proyecto: `File → New`
3. Guarda como: `BusquedaLineal.fsg`

#### Paso 2: Construir el Flujo

**Estructura visual a crear:**

```text
     ╔═════════════╗
     ║   INICIO    ║
     ╚════╤════════╝
          │
          ▼
╔═════════════════════╗
║ Leer n, meta, array ║
╚════════╤════════════╝
         │
         ▼
╔═════════════════════╗
║ i = 0               ║
║ encontrado = false  ║
╚════════╤════════════╝
         │
         ▼
┌────────────────────┐
│ ¿i < 8 AND NOT     │
│ encontrado?        │
└─┬──────────────┬───┘
  │ SÍ           │ NO
  ▼              ▼
┌──────────────┐ ┌─────────────────┐ 
│ ¿array[i]    │ │ Escribir        │ 
│ = meta?      │ │ "No encontrado" │ 
└─┬────────┬───┘ └────────┬────────┘ 
  │ SÍ     │ NO           │ 
  ▼        ▼              ▼ 
┌──────┐ ┌──────────┐ ╔═══════════╗ 
│Escribir│ │ i = i+1│ ║   FIN     ║ 
│Position│ └────────┘ ╚═══════════╝ 
└──────┘
```

#### Paso 3: Implementar en Flowgorithm

**Estructura paso a paso:**

1. **Elemento INICIO:**
   - Clic derecho en pantalla → `Insert → Terminal`
   - Escribe: "BÚSQUEDA LINEAL"

2. **Elemento INPUT (Entrada):**
   - Clic derecho → `Insert → Input`
   - Configura 3 entradas: `n`, `meta`, `array`

3. **Elemento ASSIGNMENT (Asignación):**
   - Clic derecho → `Insert → Assignment`
   - Escribe: `i ← 0`, `encontrado ← false`

4. **Elemento LOOP (Bucle While):**
   - Clic derecho → `Insert → While`
   - Condición: `i < n AND encontrado = false`

5. **Dentro del Loop - DECISION (Decisión):**
   - Clic derecho → `Insert → Decision`
   - Condición: `array[i] = meta`

6. **Rama SÍ:**
   - Clic derecho → `Insert → Output`
   - Texto: `"Registro encontrado en posición: " & i`
   - Clic derecho → `Insert → Assignment`
   - `encontrado ← true`

7. **Rama NO:**
   - Clic derecho → `Insert → Assignment`
   - `i ← i + 1`

8. **Final de bucle:** Conecta de vuelta a la condición WHILE

9. **Elemento FIN:**
   - Después del bucle → `Insert → Terminal`
   - Escribe: "FIN"

#### Paso 4: Ejecutar y Simular

1. Haz clic en el botón **▶ Run/Play** (superior)
2. Ingresa valores:
   - `n = 5`
   - `meta = 3`
   - `array = [1, 2, 3, 4, 5]`
3. Observa cómo el programa ejecuta paso a paso

#### Paso 5: Captura y Análisis

- **Toma una captura de pantalla** del diagrama completo
- **Toma una captura** durante la ejecución (paso a paso)
- Incluye ambas en tu reporte

---

### 📈 Tabla de Complejidad a Completar

| Escenario | Iteraciones | Complejidad | Explicación |
|-----------|------------|-------------|-------------|
| Mejor caso (elemento en pos 1) | 1 | O(1) | Se encuentra inmediatamente |
| Caso promedio (elemento en mitad) | n/2 | O(n) | Recorre aprox. mitad del array |
| Peor caso (elemento al final o no existe) | n | O(n) | Recorre todo el array |

**Conclusión:** La búsqueda lineal siempre es **O(n)** en su análisis asintótico (peor caso garantizado).

---

## 🔄 Actividad 3: Simulador de Colas FIFO

### Objetivo Pedagógico
Implementar una estructura de datos **FIFO (First In, First Out)** validando los principios de entrada y salida ordenada.

### ¿Por Qué Es Importante?
Las colas son fundamentales en:
- **Sistemas de impresoras:** Las solicitudes se procesan en orden
- **Pools de conexiones:** Las transacciones se atienden secuencialmente
- **Simulación de eventos:** Las acciones se ejecutan en tiempo de llegada

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Conceptualización

Imagina una cola de banco:
```text
Cliente 1 → Cliente 2 → Cliente 3 → Cliente 4 (Entra) (Espera)

Después de atender a Cliente 1: 
Cliente 2 → Cliente 3 → Cliente 4 (Avanza)
```

#### Paso 2: Estructura de Datos en PSeInt

Abre PSeInt y crea: `ColaFIFO.psc`

```pseint
Algoritmo SimuladorColaFIFO
	Definir cola Como Cadena;
	Definir inicio, final, tamanio, operacion, i Como Entero;
	Definir solicitud Como Cadena;
	Definir continuar Como Caracter;

	Dimension cola[11];
	inicio <- 1;
	final <- 0;
	tamanio <- 0;
	continuar <- "S";

	Escribir "╔════════════════════════════════════╗";
	Escribir "║   SIMULADOR DE COLA FIFO - BANCO   ║";
	Escribir "║   First In, First Out              ║";
	Escribir "╚════════════════════════════════════╝";
	Escribir "";

	Mientras continuar = "S" O continuar = "s" Hacer
		Escribir "";
		Escribir "─── OPCIONES ───";
		Escribir "[1] Enqueue (Ingresar solicitud)";
		Escribir "[2] Dequeue (Atender solicitud)";
		Escribir "[3] Ver estado de la cola";
		Escribir "[4] Salir";
		Escribir "";
		Escribir "Selecciona una opción:";
		Leer operacion;
		
		Segun operacion Hacer
			Caso 1:
				Si tamanio < 10 Entonces
					final <- final + 1;
					Si final > 10 Entonces
						final <- 1;
					FinSi;
					Escribir "Ingresa descripción de la solicitud (ej: Depósito, Retiro):";
					Leer solicitud;
					cola[final] <- solicitud;
					tamanio <- tamanio + 1;
					Escribir "✓ Solicitud agregada a la cola";
					Escribir "  Posición: ", final;
					Escribir "  Total en cola: ", tamanio;
				Sino
					Escribir "✗ ERROR: Cola llena.";
				FinSi;
			Caso 2:
				Si tamanio > 0 Entonces
					Escribir "";
					Escribir "Atendiendo solicitud...";
					Escribir "► Tipo: ", cola[inicio];
					cola[inicio] <- "";
					inicio <- inicio + 1;
					Si inicio > 10 Entonces
						inicio <- 1;
					FinSi;
					tamanio <- tamanio - 1;
					Escribir "✓ Solicitud completada";
					Escribir "Total en cola: ", tamanio;
				Sino
					Escribir "✗ ERROR: Cola vacía.";
				FinSi;
			Caso 3:
				Escribir "";
				Si tamanio > 0 Entonces
					Escribir "Estado actual de la cola:";
					Escribir "───────────────────────";
					Escribir "Total de solicitudes: ", tamanio;
					Escribir "Próxima a atender: ", cola[inicio];
					Escribir "";
					Escribir "Orden de atención:";
					Para i <- inicio Hasta final Con Paso 1 Hacer
						Si cola[i] <> "" Entonces
							Escribir "  ", i, ". ", cola[i];
						FinSi;
					FinPara;
				Sino
					Escribir "La cola está vacía";
				FinSi;
			Caso 4:
				Escribir "";
				Escribir "Gracias por usar el simulador.";
				continuar <- "N";
			De Otro Modo:
				Escribir "✗ Opción inválida";
		FinSegun;
	FinMientras;
FinAlgoritmo
```

#### Paso 3: Ejecución y Pruebas

**Escenario de Prueba Completo:**

```text
Operación 1: Enqueue "Depósito" → Tamaño: 1 
Operación 2: Enqueue "Retiro" → Tamaño: 2 
Operación 3: Enqueue "Transferencia" → Tamaño: 3 
Operación 4: Ver Estado

Salida esperada: 
Total de solicitudes: 3 
Próxima a atender: Depósito 
Orden:
Depósito
Retiro
Transferencia

Operación 5: Dequeue → Atiende "Depósito", Tamaño: 2 
Operación 6: Dequeue → Atiende "Retiro", Tamaño: 1 
Operación 7: Ver Estado

Salida esperada: 
Total de solicitudes: 1 
Próxima a atender: Transferencia
```

#### Paso 4: Tabla de Validación FIFO

| Paso | Operación | Entrada | Cola Resultante | Tamaño | Verificación |
|------|-----------|---------|-----------------|--------|--------------|
| 1 | Enqueue | "A" | [A] | 1 | ✓ |
| 2 | Enqueue | "B" | [A, B] | 2 | ✓ |
| 3 | Enqueue | "C" | [A, B, C] | 3 | ✓ |
| 4 | Dequeue | - | [B, C] | 2 | ✓ (Salió A) |
| 5 | Dequeue | - | [C] | 1 | ✓ (Salió B) |

---

## ⚖️ Actividad 4: Comparativa Linear vs Binaria

### Objetivo Pedagógico
Ejecutar ambos algoritmos sobre el mismo dataset y medir diferencias reales de rendimiento y cantidad de operaciones.

---

### 📝 Instrucciones Paso a Paso

#### Paso 1: Crear Búsqueda Lineal en PSeInt

Archivo: `BusquedaLineal.psc`

```pseint
Algoritmo BusquedaLineal
	Definir registros Como Entero;
	Definir i, meta, comparaciones Como Entero;
	Definir encontrado Como Logico;

	Dimension registros[8];
	registros[0] <- 1002;
	registros[1] <- 1045;
	registros[2] <- 2098;
	registros[3] <- 3301;
	registros[4] <- 3311;
	registros[5] <- 4005;
	registros[6] <- 5020;
	registros[7] <- 6081;

	encontrado <- Falso;
	comparaciones <- 0;

	Escribir "=== BÚSQUEDA LINEAL - O(n) ===";
	Escribir "Ingresa el registro a buscar:";
	Leer meta;

	Para i <- 0 Hasta 7 Con Paso 1 Hacer
		comparaciones <- comparaciones + 1;
		Escribir "Comparación ", comparaciones, ": registros[", i, "] = ", registros[i];
		
		Si registros[i] = meta Entonces
			Escribir "";
			Escribir "✓ ENCONTRADO en posición ", i;
			Escribir "Total de comparaciones: ", comparaciones;
			encontrado <- Verdadero;
			i <- 8;
		FinSi;
	FinPara;

	Si encontrado = Falso Entonces
		Escribir "";
		Escribir "✗ NO ENCONTRADO";
		Escribir "Total de comparaciones: ", comparaciones;
	FinSi;
FinAlgoritmo
```

#### Paso 2: Ejecutar Ambos Algoritmos

**Test Comparativo: Buscar 5020**

**Búsqueda Lineal:**
```text
Comparación 1: registros[0] = 1002 
Comparación 2: registros[1] = 1045 
Comparación 3: registros[2] = 2098 
Comparación 4: registros[3] = 3301 
Comparación 5: registros[4] = 3311 
Comparación 6: registros[5] = 4005 
Comparación 7: registros[6] = 5020 
✓ ENCONTRADO en posición 6 
Total de comparaciones: 7
```

**Búsqueda Binaria (del código anterior):**
```text
Comparando con posición 3: 3301 → Buscando en mitad superior 
Comparando con posición 5: 4005 → Buscando en mitad superior 
Comparando con posición 6: 5020 
✓ ¡ÉXITO! Registro localizado 
Posición en el sistema: 6
```

#### Paso 3: Tabla Comparativa

Completa esta tabla con tus resultados reales:

| Elemento | Posición | Lineal (Comp.) | Binaria (Comp.) | Mejora |
|----------|----------|----------------|-----------------|--------|
| 1002 | 0 | 1 | 3 | Sin mejora |
| 3311 | 4 | 5 | 3 | 40% menos |
| 5020 | 6 | 7 | 4 | 42% menos |
| 6081 | 7 | 8 | 4 | 50% menos |
| 9999 | N/A | 8 | 4 | 50% menos |

**Fórmula de Mejora:** `(Lineal - Binaria) / Lineal × 100%`

#### Paso 4: Análisis Matemático

Completa el siguiente análisis:

**Para n = 8 elementos:**
- Búsqueda Lineal (peor caso): 8 comparaciones
- Búsqueda Binaria (peor caso): ⌈log₂(8)⌉ = 3 comparaciones
- **Mejora: 62.5%**

**Para n = 1,000 elementos:**
- Búsqueda Lineal (peor caso): 1,000 comparaciones
- Búsqueda Binaria (peor caso): ⌈log₂(1000)⌉ = 10 comparaciones
- **Mejora: 99%**

**Conclusión:** La mejora se amplifica exponencialmente con datasets más grandes.

---

## 📋 Rúbrica de Evaluación

### Criterios Generales (Todas las Actividades)

| Criterio | Excelente (5) | Bueno (4) | Aceptable (3) | Mejora Requerida (≤2) |
|----------|--------------|----------|--------------|----------------------|
| **Código Funciona** | Ejecuta sin errores en todos los casos | 1-2 errores menores | Funciona parcialmente | No ejecuta o falla |
| **Claridad de Código** | Variables bien nombradas, comentarios claros | Nombres descriptivos | Entiendible con esfuerzo | Confuso/sin documentar |
| **Análisis de Complejidad** | Cálculo correcto con justificación | Cálculo correcto | Intento de análisis | Ausente o incorrecto |
| **Pruebas Ejecutadas** | Todos los casos cubiertos | Mayoría de casos | Algunos casos | Sin pruebas |
| **Documentación** | Reporte completo y estructurado | Reporte con omisiones menores | Reporte básico | Falta documentación |

### Rúbrica Específica

| Aspecto | Puntuación |
|--------|-----------|
| Actividad 1 (Búsqueda Binaria) | 25 pts |
| Actividad 2 (Flowgorithm) | 25 pts |
| Actividad 3 (Colas FIFO) | 25 pts |
| Actividad 4 (Comparativa Lineal/Binaria) | 25 pts |
| **Total** | **100 pts** |

---

## 🎓 Preguntas de Reflexión Final

### Nivel 1: Comprensión
1. ¿Cuál es la diferencia fundamental entre búsqueda lineal y binaria?
2. ¿Por qué un vector debe estar ordenado para usar búsqueda binaria?
3. ¿Qué significa FIFO y cómo lo experimentas en tu vida cotidiana?

### Nivel 2: Aplicación
4. Si tuvieras una base de datos de 1 millón de registros, ¿cuál algoritmo recomendarías? ¿Por qué?
5. Diseña un escenario donde una cola FIFO sería inapropiada. ¿Qué estructura usarías?
6. ¿Puede fallar la búsqueda binaria en algún caso? Describe.

### Nivel 3: Síntesis
7. Compara el costo de **ordenamiento + búsqueda binaria** vs **búsqueda lineal directa** para:
   - Dataset pequeño (n=100)
   - Dataset mediano (n=100,000)
   - Dataset grande (n=1,000,000)

8. Propón un algoritmo híbrido que combine búsqueda lineal y binaria.

---

## 📦 Entregables Requeridos

Para cada estudiante o equipo:

### Carpeta de Entrega: `/TALLER_SOLUCION/`

```text
TALLER_SOLUCION/ 
├── Actividad1_BusquedaBinaria.psc 
├── Actividad2_Flowgorithm.fsg 
├── Actividad2_Capturas/ 
│   ├── diagrama_flujo.png 
│   └── ejecucion_paso_a_paso.png 
├── Actividad3_ColaFIFO.psc 
├── Actividad4_Comparativa.psc 
├── Actividad4_BusquedaLineal.psc 
├── REPORTE_FINAL.md 
└── REFLEXION_RESPUESTAS.txt
```

### Archivo: `REPORTE_FINAL.md`

```markdown
# Reporte Final - Taller de Algoritmos

## Resumen Ejecutivo
[Escribe 2-3 párrafos sintetizando lo aprendido]

## Actividad 1: Búsqueda Binaria
- Funcionamiento: [Explicación propia]
- Complejidad: O(log n)
- Test Cases: [Resultados]

## Actividad 2: Análisis con Flowgorithm
- Diagrama: [Descripción]
- Complejidad: O(n)

## Actividad 3: Colas FIFO
- Operaciones: [Descripción]
- Validación FIFO: [Tabla]

## Actividad 4: Comparativa
- Resultados: [Tabla]
- Recomendaciones: [Análisis]

## Conclusiones y Aprendizajes
[Síntesis personal del taller]
```