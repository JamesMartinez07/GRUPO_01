# CAPÍTULO 1: Análisis del Problema

## 1. Descripción del problema
El presente proyecto propone el desarrollo de un "Sistema de Gestión de Procesos" que simula de manera simplificada la administración de tareas y recursos dentro de un Sistema Operativo. El problema principal radica en coordinar eficientemente tres componentes críticos sin la utilización de librerías de estructuras predefinidas: un Gestor de Procesos (control general), un Planificador de CPU (orden de ejecución) y un Gestor de Memoria (asignación de recursos). El sistema busca resolver la concurrencia, la organización por prioridades y la liberación controlada de bloques de memoria, garantizando estabilidad y un flujo lógico de datos a través de consola.

## 2. Requerimientos del sistema

### Requerimientos Funcionales (RF)
* **RF-01 (Registro de Procesos):** El sistema debe permitir la inserción de nuevos procesos con un ID único, un nombre representativo y un nivel de prioridad asignado.
* **RF-02 (Eliminación de Procesos):** El sistema debe permitir remover procesos específicos de la estructura principal mediante la búsqueda de su ID.
* **RF-03 (Búsqueda por Atributos):** El sistema debe permitir localizar un proceso específico utilizando su ID o su nombre.
* **RF-04 (Planificación de CPU):** El sistema debe encolar los procesos y ordenarlos según su prioridad, permitiendo la simulación de ejecución ("desencolamiento") del proceso más prioritario.
* **RF-05 (Asignación de Memoria):** El sistema debe simular la reserva de memoria para los procesos usando una estructura apilable (Push) y liberar los bloques en orden inverso (Pop).

### Requerimientos No Funcionales (RNF)
* **RNF-01 (Estructuras Nativas):** El software debe ser construido utilizando exclusivamente estructuras de datos dinámicas lineales (listas enlazadas, pilas y colas) programadas desde cero en Dev-C++.
* **RNF-02 (Interfaz de Usuario):** El sistema interactivo debe ejecutarse fluidamente mediante una interfaz de consola clara, intuitiva y validada contra ingresos de datos erróneos.
