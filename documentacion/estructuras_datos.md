# Estructuras de Datos Propuestas

Para el desarrollo del Sistema de Gestión de Procesos, se decidió implementar tres estructuras de datos dinámicas lineales: lista enlazada, cola de prioridad y pila. Estas fueron construidas desde cero en C++, sin utilizar librerías predefinidas, con el objetivo de comprender su funcionamiento interno y aplicarlas a un problema real.

---

## Lista Enlazada Simple (Gestor de Procesos)

La lista enlazada se implementa como una estructura formada por nodos conectados entre sí mediante punteros. Cada nodo contiene la información de un proceso (ID, nombre y prioridad), además de un puntero llamado `siguiente`, que permite enlazar un nodo con otro.

A diferencia de los arreglos, esta estructura no tiene un tamaño fijo, lo que permite agregar o eliminar procesos dinámicamente durante la ejecución del programa sin desperdiciar memoria.

Ejemplo de representación:

[P1] -> [P2] -> [P3] -> NULL

Operaciones principales:

- Inserción: Para insertar un proceso, se crea un nuevo nodo y se recorre la lista hasta llegar al último elemento, donde se enlaza el nuevo nodo.
- Eliminación: Se busca el nodo por su ID y se ajustan los punteros para retirarlo de la lista sin afectar los demás nodos.
- Búsqueda: Se recorre la lista nodo por nodo hasta encontrar el proceso deseado, ya sea por ID o nombre.

---

## Cola de Prioridad (Planificador de CPU)

La cola de prioridad se basa en el principio FIFO (First In, First Out), pero se adapta para ordenar los procesos según su nivel de prioridad. Esto significa que los procesos más importantes no necesariamente esperan su turno, sino que se colocan en posiciones más adelantadas.

Esta estructura permite simular el comportamiento del CPU, donde los procesos con mayor prioridad son ejecutados primero.

Ejemplo de representación:

[Alta] -> [Media] -> [Baja]

Operaciones principales:

- Encolar: Inserta un proceso en la cola respetando su prioridad, ubicándolo en la posición correcta.
- Desencolar: Elimina el proceso que se encuentra al inicio de la cola, el cual tiene mayor prioridad.
- Visualización: Permite mostrar el estado actual de la cola y el orden en que se ejecutarán los procesos.

---

## Pila / Stack (Gestor de Memoria)

La pila se implementa bajo el principio LIFO (Last In, First Out), lo que significa que el último elemento en ingresar es el primero en salir. Esta estructura se utiliza para simular la gestión de memoria del sistema.

Cada vez que un proceso solicita memoria, se agrega un bloque a la pila (push), y cuando se libera memoria, se elimina el último bloque ingresado (pop).

Ejemplo de representación:

[P3]  
[P2]  
[P1]  

Operaciones principales:

- Push: Inserta un nuevo elemento en la cima de la pila.
- Pop: Elimina el elemento que se encuentra en la cima.
- Estado: Permite visualizar los elementos actuales almacenados en la pila.

---

## Relación entre las estructuras

Cada una de las estructuras cumple un rol específico dentro del sistema:

- La lista enlazada se encarga de almacenar todos los procesos registrados.
- La cola de prioridad organiza la ejecución de los procesos en el CPU según su importancia.
- La pila gestiona la memoria asignada a los procesos.

Estas tres estructuras trabajan de manera conjunta para simular el funcionamiento básico de un sistema operativo, permitiendo una correcta organización y control de los recursos.

---

## Justificación de la elección

Se eligieron estructuras de datos dinámicas debido a que el sistema debe manejar una cantidad variable de procesos, lo cual no sería eficiente con estructuras estáticas como los arreglos.

La lista enlazada permite una inserción y eliminación flexible de elementos en tiempo de ejecución. La cola de prioridad resulta adecuada para representar la planificación del CPU, ya que prioriza automáticamente los procesos más importantes. Por último, la pila refleja de forma adecuada la forma en que se gestiona la memoria en muchos sistemas, siguiendo un orden inverso de uso.

En conjunto, estas estructuras permiten desarrollar una solución eficiente, organizada y coherente con el problema planteado.

---

## Definición en código

```cpp
struct Proceso {
    int id;
    char nombre[50];
    int prioridad;
    Proceso* siguiente;
};
