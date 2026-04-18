# Análisis de Complejidad y Búsqueda Avanzada

Esta sesión aborda los métodos formales para medir la eficiencia algorítmica y las estructuras de búsqueda. Como analista o futuro ingeniero, optimizar recursos computacionales no es opcional: es un requisito estricto en el desarrollo de software moderno.

## 2.1 Notación Asintótica y Análisis Big O

Constantemente te preguntarás: "¿Es rápido mi código?". La eficiencia de un algoritmo no se cuantifica en segundos, dado que tu computadora puede ser más potente que un servidor externo. Por ende, empleamos la **Notación Asintótica**. Esta notación define matemáticamente el comportamiento de tu código cuando la cantidad de datos de entrada (a la que llamamos **$n$**) aumenta indiscriminadamente.

*   **Límite Superior (Big O - $O$):** Expresa el escenario del **peor caso**. Te garantiza matemáticamente que el algoritmo nunca excederá este costo computacional. Si programas bajo Big O, aseguras estabilidad.
*   **Límite Inferior (Big Omega - $\Omega$):** Representa el **mejor caso** (ej: buscar a un usuario y que resulte ser el primero de la lista).
*   **Límite Ajustado (Big Theta - $\Theta$):** Se alcanza cuando el peor caso y el mejor caso poseen la misma tasa de crecimiento matemático.

### Análisis y Cálculo de Complejidad (Pseudocódigo en PSeInt)
A continuación, observa cómo impacta un bloque en tu código:

```text
Algoritmo CalcularComplejidad
    Definir n, i, j Como Entero
    n <- 1000
    
    // Bloque 1: Orden O(n) - Tiempo Secuencial Lineal
    // Si 'n' vale 1000, esto da 1000 vueltas exactas.
    Para i <- 1 Hasta n Con Paso 1 Hacer
        Escribir "Registro Procesado N: ", i
    FinPara
    
    // Bloque 2: Orden O(n^2) - Bucles Anidados (Tiempo Cuadrático)
    // El ciclo interno da 1000 vueltas POR CADA vuelta del externo. 
    // Total de vueltas: 1000 * 1000 = 1,000,000 de operaciones.
    Para i <- 1 Hasta n Con Paso 1 Hacer
        Para j <- 1 Hasta n Con Paso 1 Hacer
            Escribir "Cruce correlacional: ", i, " con ", j
        FinPara
    FinPara
FinAlgoritmo
```
**Conclusión Analítica:** En industrias, el compilador evalúa tu sistema por la parte más pesada. Aquí, el sistema global es evaluado como **$O(n^2)$**. Esto sería letal en grandes bancos de datos. Debes evitar utilizar ciclos anidados siempre que sea posible.

---

## 2.2 Búsqueda Lineal vs. Búsqueda Binaria

Supón que debes localizar información en un directorio bancario extenso. 

### Búsqueda Lineal
Recorres cada registro matemáticamente, uno por uno, hasta topártelo. Su complejidad es **$O(n)$**. En bases de datos de dos millones de personas, esta búsqueda paralizaría los servidores de tiempo crítico.

### Búsqueda Binaria
La técnica dorada. Otorga una inmensa optimización con complejidad logarítmica **$O(\log n)$**. 
*Condición excluyente:* Debes aplicar obligatoriamente un proceso previo de ordenamiento en el arreglo para que funcione.

¿Cómo funciona fundamentalmente?
1. Vas a ubicar el punto medio exacto de tu lista.
2. Si lo que buscas es numéricamente menor al punto central, puedes descartar y desechar toda la mitad superior completa; sabes por lógica que ahí no estará.
3. Este subproceso se repite hasta aislar tu valor instantáneamente.

**Esquema Funcional (Pseudocódigo PSeInt):**
```text
Algoritmo BusquedaBinaria
    // 1. Declaras variables y el objetivo
    Definir inicio, fin, mitad, meta, arreglo Como Entero
    Dimension arreglo[5]
    arreglo[1] <- 102; arreglo[2] <- 205; arreglo[3] <- 380; arreglo[4] <- 410; arreglo[5] <- 500
    meta <- 380

    // 2. Apuntas a los extremos
    inicio <- 1
    fin <- 5
    
    // 3. Recortas recursivamente a la mitad
    Mientras inicio <= fin Hacer
        mitad <- TRUNC((inicio + fin) / 2)
        Si arreglo[mitad] = meta Entonces
            Escribir "Registro localizado en el índice ", mitad
            // Aquí el sistema hace una pausa e interrumpe (Break/Retorno)
        Sino
            Si arreglo[mitad] < meta Entonces
                inicio <- mitad + 1 // Aisla descartando la cuota Izquierda
            Sino
                fin <- mitad - 1 // Aisla descartando la cuota Derecha
            FinSi
        FinSi
    FinMientras
FinAlgoritmo
```

---

## 2.3 Principios de Recursividad

Lograrás la recursividad cuando en tus sistemas abstraigas un problema gigante dividiéndolo mediante subprocesos idénticos mas pequeños. En otras palabras, diseñar que tu código o método **se invoque a sí mismo**.

**Regla Categórica de la Condición Base:**
No basta con llamarse a sí mismo. Todo algoritmo recursivo exige estrictamente un límite resolutivo de tope (Condición o Caso Base). De fallar u omitirse este límite, tu código colapsará instantáneamente la memoria estática de ciclo del procesador, disparando el temido error estructural *Stack Overflow*. 

---

## 2.4 Fundamentos de Listas Enlazadas

Las bases históricas te guiaron sobre los *Arreglos* o Arrays; los cuales dictaminan exigir campos estáticos de memoria pegados unos contiguos a otros. Esto restringe al software a recalcular toda la memoria del sistema si deseamos meter un valor extra por la mitad de la formación.
Para contrarrestar la limitante, utilizarás arreglos en estructura de **Listas Enlazadas**.

Constan de Nodos: Cada ubicación no es solo un valor estático; contiene ahora el "Dato Base" y adicionalmente aloja el **"Puntero"** abstracto el cual dictamina las coordenadas del siguiente registro en el sistema disperso o en red, ganando así agilidad monumental al cruzar, saltar e insertar datos inmediatos (Resolviendo este proceso aislado rápido de nivel **$O(1)$**).

---

## 2.5 Modelos de Pilas (Stack) y Colas (Queue)

Finalmente, debes incorporar al glosario de arquitectura los perfiles de entrada restrictivos de lectura matricial:

### Estructura Pila (Stack)
Tú ingresas o eliminas datos gobernando el modelo **LIFO (Last In, First Out / El último en entrar es el primero que sacas)**. 
- *A nivel conceptual interno de tu Operativo de Consola:* Procesadores de retroceso ("Deshacer" en hojas de cálculo).

### Estructura Cola (Queue)
Dictaminas asincronismo mediante **FIFO (First In, First Out / Aquel que entra primero es el primer procesado)**.
- *Ejemplo local en infraestructura:* Las llamadas api o el pool impresor enviando solicitudes a espera de proceso consecutivo uno al instante exacto posterior tras otro en la base.
