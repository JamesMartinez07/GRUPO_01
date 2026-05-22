# Capítulo 1: Análisis del Problema

## 1. Descripción del problema

El presente proyecto consiste en el desarrollo de un Sistema de Gestión de Procesos que simula de manera simplificada el funcionamiento de un sistema operativo. Este sistema tiene como finalidad administrar procesos, organizar su ejecución en el CPU según niveles de prioridad y controlar la asignación de memoria.

El problema principal radica en la necesidad de gestionar múltiples procesos de forma eficiente, considerando que cada uno puede tener distinta prioridad y requerimientos de memoria. Para ello, se busca implementar una solución que permita registrar, modificar, eliminar y ejecutar procesos, manteniendo un flujo ordenado y coherente dentro del sistema.

Asimismo, el sistema debe representar la interacción entre tres componentes fundamentales: el gestor de procesos, el planificador de CPU y el gestor de memoria. Todo esto se realizará utilizando estructuras de datos dinámicas lineales, sin el uso de librerías predefinidas, lo cual implica un mayor control sobre la lógica de implementación.

---

## 2. Requerimientos del sistema

### 2.1 Requerimientos Funcionales

**RF-01: Registro de procesos**  
El sistema debe permitir ingresar nuevos procesos solicitando un identificador único (ID), nombre y nivel de prioridad.

**RF-02: Eliminación de procesos**  
El sistema debe permitir eliminar procesos existentes mediante la búsqueda por su ID.

**RF-03: Búsqueda de procesos**  
El sistema debe permitir localizar procesos utilizando su ID o nombre.

**RF-04: Planificación de CPU**  
El sistema debe gestionar la ejecución de procesos mediante una cola de prioridad, garantizando que los procesos con mayor prioridad sean atendidos primero.

**RF-05: Modificación de prioridad**  
El sistema debe permitir modificar la prioridad de un proceso existente y reordenar la cola de CPU según corresponda.

**RF-06: Asignación de memoria**  
El sistema debe simular la asignación de memoria utilizando una estructura tipo pila, permitiendo registrar bloques asignados a procesos.

**RF-07: Liberación de memoria**  
El sistema debe permitir liberar memoria siguiendo el principio LIFO (último en entrar, primero en salir).

---

### 2.2 Requerimientos No Funcionales

**RNF-01: Uso de estructuras nativas**  
El sistema debe ser implementado utilizando exclusivamente estructuras de datos dinámicas lineales (listas enlazadas, pilas y colas), sin el uso de librerías externas.

**RNF-02: Interfaz de usuario**  
La interacción con el sistema debe realizarse mediante una interfaz de consola clara, mostrando instrucciones y resultados comprensibles.

**RNF-03: Validación de datos**  
El sistema debe validar los datos ingresados por el usuario, evitando errores como IDs duplicados, campos vacíos o valores fuera de rango.

**RNF-04: Rendimiento**  
El sistema debe ejecutar las operaciones básicas de manera eficiente, garantizando tiempos de respuesta adecuados incluso con múltiples procesos.

**RNF-05: Mantenibilidad**  
El código debe estar organizado, estructurado y comentado de forma clara, facilitando su comprensión y futuras modificaciones.

**RNF-06: Consistencia de datos**  
El sistema debe mantener la integridad de la información en todo momento, evitando pérdidas o inconsistencias durante las operaciones.
