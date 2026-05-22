# Capítulo 1: Análisis del Problema

## 1. Descripción del problema

El proyecto consiste en desarrollar un **Sistema de Gestión de Procesos** que simula de forma simplificada la administración de tareas y recursos dentro de un sistema operativo. El problema central es coordinar eficientemente tres componentes críticos sin usar librerías predefinidas: un Gestor de Procesos, un Planificador de CPU y un Gestor de Memoria. El sistema busca resolver la concurrencia, la organización por prioridades y la liberación controlada de bloques de memoria, garantizando estabilidad y un flujo lógico de datos a través de consola.

---

## 2. Requerimientos del sistema

### Requerimientos Funcionales

| ID | Nombre | Descripción |
|----|--------|-------------|
| RF-01 | Registro de Procesos | Inserción de nuevos procesos con ID único, nombre y nivel de prioridad. |
| RF-02 | Eliminación de Procesos | Eliminación de procesos específicos buscándolos por su ID. |
| RF-03 | Búsqueda por Atributos | Localización de un proceso usando su ID o nombre. |
| RF-04 | Planificación de CPU | Encolamiento ordenado por prioridad y simulación de ejecución del proceso más prioritario. |
| RF-05 | Asignación de Memoria | Simulación de reserva (Push) y liberación (Pop) de bloques de memoria en orden inverso. |

### Requerimientos No Funcionales

| ID | Nombre | Descripción |
|----|--------|-------------|
| RNF-01 | Estructuras Nativas | Todo construido desde cero con listas enlazadas, pilas y colas en Dev-C++, sin librerías externas. |
| RNF-02 | Interfaz de Usuario | Consola clara, intuitiva y con validación contra ingresos erróneos. |
