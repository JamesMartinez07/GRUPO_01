# Estructuras de Datos que vamos a usar

Para este proyecto del gestor de procesos vamos a armar tres estructuras dinámicas desde cero usando punteros (nada de librerías raras):

1. **Lista Enlazada Simple:** La usaremos como la base de datos de todo el programa para guardar los procesos. Cada proceso va a ser un nodo conectado al que sigue por un puntero.
2. **Cola de Prioridad:** Servirá para el planificador del CPU. Los procesos entran en fila, pero si uno tiene prioridad alta se acomoda adelante para que el procesador lo atienda primero.
3. **Pila (Stack):** Con esto simulamos la memoria RAM. Funciona al revés: el último bloque de memoria que asignamos es el primero que tenemos que borrar (método LIFO).

*¿Por qué hacemos esto?* Porque en un sistema operativo real no sabes cuántas tareas va a abrir el usuario. Si usáramos arreglos fijos, limitaríamos el programa o desperdiciaríamos memoria RAM guardando espacio para nada. Con los punteros, la memoria crece y se achica sola según se necesite.

---

## El molde en código (El Struct)
En Dev-C++ la base de todo nuestro código va a ser este `struct` para crear cada proceso:

```cpp
struct Proceso {
    int id;               // El número del proceso
    char nombre[50];      // Su nombre (ej. "Navegador")
    int prioridad;        // Qué tan importante es (Alta, Media, Baja)
    Proceso* siguiente;   // El puntero para amarrarlo con el siguiente nodo
};
