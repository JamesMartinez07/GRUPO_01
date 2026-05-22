# Capítulo 1 y 2: Diseño de Estructuras de Datos

## 3. Estructuras de datos propuestas

Para dar una solución integral al Sistema de Gestión de Procesos, se propusieron tres estructuras de datos dinámicas lineales implementadas desde cero, las cuales permiten gestionar de manera eficiente los procesos, la planificación del CPU y la administración de memoria.

- **Lista Enlazada Simple (Gestor de Procesos):**  
Se diseñó como una estructura compuesta por nodos enlazados mediante punteros, donde cada nodo almacena la información de un proceso (ID, nombre y prioridad) junto con un puntero (`siguiente`) que referencia al siguiente nodo en memoria.  
Esta estructura permite un crecimiento dinámico, evitando el uso de espacios de memoria innecesarios.

  **Operaciones principales:**
  - Inserción de procesos al final de la lista.  
  - Eliminación de procesos mediante búsqueda por ID.  
  - Búsqueda secuencial de procesos por ID o nombre.  

- **Cola de Prioridad (Planificador de CPU):**  
Se implementó tomando como base el principio FIFO (*First In, First Out*), pero adaptado para ordenar los procesos según su prioridad. Esto permite que los procesos más críticos se posicionen al inicio de la cola y sean ejecutados primero.

  **Operaciones principales:**
  - Encolamiento de procesos respetando el orden de prioridad.  
  - Desencolamiento del proceso con mayor prioridad.  
  - Visualización del estado actual de la cola.  

- **Pila / Stack (Gestor de Memoria):**  
Se desarrolló bajo el principio LIFO (*Last In, First Out*), permitiendo simular la gestión de memoria. En este caso, el último bloque de memoria asignado será el primero en liberarse.

  **Operaciones principales:**
  - Push: inserción de bloques de memoria en la cima.  
  - Pop: eliminación del último bloque agregado.  
  - Visualización del estado de la pila.  

---

## 4. Justificación de la elección

Se optó por el uso de estructuras dinámicas debido a que el sistema debe manejar una cantidad variable de procesos, lo cual hace que el uso de estructuras estáticas como arreglos no sea eficiente.

Las listas enlazadas permiten insertar y eliminar procesos en tiempo de ejecución sin necesidad de redefinir tamaños, lo cual optimiza el uso de memoria. Por otro lado, la cola de prioridad resulta adecuada para simular la planificación del CPU, ya que garantiza que los procesos más importantes sean atendidos primero.

Asimismo, la pila refleja correctamente el comportamiento de la memoria en sistemas reales, donde el último recurso utilizado es el primero en liberarse. En conjunto, estas estructuras permiten una solución flexible, eficiente y coherente con el problema planteado.

---

## 1. Descripción de estructuras de datos y operaciones

A nivel de implementación en Dev-C++, las estructuras fueron definidas utilizando `struct` y punteros, lo que permite manejar directamente la memoria y comprender el comportamiento interno de cada estructura.

### Estructura de un Proceso (Nodo de la Lista)

```cpp
struct Proceso {
    int id;
    char nombre[50];
    int prioridad;
    Proceso* siguiente;
};
