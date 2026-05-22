# Capítulo 1 y 2: Diseño de Estructuras de Datos

## 3. Estructuras de datos propuestas

Para dar una solución integral al Sistema de Gestión de Procesos, propuse tres estructuras lineales dinámicas que construí desde cero:

- **Lista Enlazada Simple (Gestor de Procesos):** La diseñé como una secuencia de nodos dispersos en memoria donde cada nodo almacena la información del proceso — ID, nombre y prioridad — junto con un puntero (`siguiente`) que dirige al próximo elemento. Opté por esta estructura porque su naturaleza dinámica evita el desperdicio de memoria física.

- **Cola de Prioridad (Planificador de CPU):** La construí sobre el principio FIFO (*First In, First Out*), pero la modifiqué para que cada inserción se realice de forma ordenada según el nivel de prioridad del proceso. De esta manera, los procesos más críticos se posicionan automáticamente al inicio y son atendidos primero.

- **Pila / Stack (Gestor de Memoria):** La implementé bajo el principio LIFO (*Last In, First Out*) para administrar los bloques lógicos de memoria asignados a las tareas en ejecución. Con este enfoque, el último bloque en ser reservado mediante un *Push* será siempre el primero en liberarse con un *Pop*.

---

## 4. Justificación de la elección

Me decidí por estructuras dinámicas porque, al estudiar cómo funcionan los sistemas operativos reales, comprendí que manejan cargas de trabajo completamente impredecibles. Usar arreglos estáticos no solo limitaría el número máximo de procesos que podría gestionar, sino que también desperdiciaría memoria de forma innecesaria.

En cambio, las listas enlazadas me permiten insertar y eliminar elementos en tiempo de ejecución de manera eficiente. La cola de prioridad me pareció el modelo perfecto para simular la planificación de la CPU, ya que antepone las tareas críticas de forma natural, mientras que la pila refleja con fidelidad el comportamiento de los segmentos de memoria volátil en sistemas clásicos.

---

## 1. Descripción de estructuras de datos y operaciones

A nivel de código en Dev-C++, definí las estructuras utilizando `struct` y punteros nativos de la siguiente forma:

### Estructura de un Proceso (Nodo de la Lista)

```cpp
struct Proceso {
    int id;
    char nombre[50];
    int prioridad;
    Proceso* siguiente;
};
```
