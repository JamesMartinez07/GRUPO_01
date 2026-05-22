# CAPÍTULO 1 Y 2: Diseño de Estructuras de Datos

## 3. Estructuras de datos propuestas (Capítulo 1)
Para dar solución integral al Sistema de Gestión de Procesos, se han planteado tres estructuras lineales dinámicas construidas desde cero:

* **Lista Enlazada Simple (Gestor de Procesos):** Consiste en una secuencia de nodos dispersos en memoria donde cada nodo almacena la información del proceso (ID, Nombre, Prioridad) y un puntero (`siguiente`) que direcciona al próximo elemento. Su naturaleza dinámica evita el desperdicio de memoria física.
* **Cola de Prioridad (Planificador de CPU):** Estructura basada en el principio FIFO (First In, First Out), modificada de modo que la inserción de un elemento se realiza de manera ordenada según su nivel de prioridad. Los procesos con mayor prioridad se posicionan al inicio para ser "ejecutados" (desencolados) primero.
* **Pila / Stack (Gestor de Memoria):** Estructura lineal fundamentada en el principio LIFO (Last In, First Out). Administra bloques lógicos de memoria asignados a las tareas en ejecución; el último bloque de memoria en ser reservado (Push) será obligatoriamente el primero en ser liberado (Pop).

## 4. Justificación de la elección (Capítulo 1)
La elección de estructuras dinámicas se fundamenta en que los sistemas operativos reales manejan cargas de trabajo impredecibles. El uso de arreglos estáticos limitaría el número máximo de procesos y desperdiciaría memoria preciada. Las listas enlazadas permiten insertar y eliminar en tiempo de ejecución de forma eficiente. La cola de prioridad modela a la perfección la planificación de la CPU (anteponiendo tareas críticas), y la pila simula fielmente los segmentos de memoria volátil clásicos.

---

## 1. Descripción de estructuras de datos y operaciones (Capítulo 2)
A nivel de código en Dev-C++, las estructuras se definirán mediante `struct` y punteros nativos de la siguiente manera:

### Estructura de un Proceso (Nodo de la Lista)
```cpp
struct Proceso {
    int id;
    char nombre[50];
    int prioridad;
    Proceso* siguiente;
};
