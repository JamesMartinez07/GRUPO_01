# Lógica de los Algoritmos (Pseudocódigo)

Aquí dejamos lista la lógica en papel de cómo van a funcionar las dos tareas principales del sistema antes de pasarlas a Dev-C++.

## 1. Pseudocódigo para Registrar un Proceso
Este algoritmo sirve para meter un proceso nuevo a la Lista Enlazada y mandarlo de una vez a la Cola del CPU para que espere su turno.

Algoritmo RegistrarProceso
    // Pedimos los datos en la pantalla
    Escribir "Pon el ID del proceso:"
    Leer nuevo_id
    Escribir "Pon el Nombre del proceso:"
    Leer nuevo_nombre
    Escribir "Elige la Prioridad (1:Alta, 2:Media, 3:Baja):"
    Leer nueva_prioridad

    // Creamos el nodo en la memoria con sus datos
    Crear Nodo NuevoProceso
    NuevoProceso.id <- nuevo_id
    NuevoProceso.nombre <- nuevo_nombre
    NuevoProceso.prioridad <- nueva_prioridad
    NuevoProceso.siguiente <- NULL

    // Lo metemos al final de la Lista Enlazada
    Si Lista_Procesos == NULL Entonces
        Lista_Procesos <- NuevoProceso
    Sino
        Auxiliar <- Lista_Procesos
        Mientras Auxiliar.siguiente != NULL Hacer
            Auxiliar <- Auxiliar.siguiente
        FinMientras
        Auxiliar.siguiente <- NuevoProceso
    FinSi

    // Lo mandamos a la cola del procesador
    Llamar a EncolarPorPrioridad(NuevoProceso)
    Escribir "Proceso guardado y enviado a la cola del CPU."
FinAlgoritmo


## 2. Pseudocódigo para Cambiar la Prioridad
Esto sirve para buscar un proceso que ya existe usando su ID y cambiarle qué tan importante es. Al cambiar esto, se tiene que volver a ordenar la cola del CPU.

Algoritmo ModificarPrioridad
    Escribir "Escribe el ID del proceso que buscas:"
    Leer id_buscar

    Si Lista_Procesos == NULL Entonces
        Escribir "No hay procesos registrados todavía."
        Salir
    FinSi

    Auxiliar <- Lista_Procesos
    Encontrado <- Falso

    // Buscamos nodo por nodo con un WHILE
    Mientras Auxiliar != NULL Y Encontrado == Falso Hacer
        Si Auxiliar.id == id_buscar Entonces
            Escribir "Proceso encontrado: ", Auxiliar.nombre
            Escribir "Pon la nueva prioridad:"
            Leer nueva_prioridad
            
            Auxiliar.prioridad <- nueva_prioridad
            Encontrado <- Verdadero
            
            // Reordenamos la fila del CPU con el cambio
            Llamar a ReacomodarColaCPU()
        Sino
            Auxiliar <- Auxiliar.siguiente
        FinSi
    FinMientras


# Diagramas de Flujo

## 1. Diagrama de Flujo: Registrar Proceso

Inicio  
↓  
Solicitar ID, nombre y prioridad  
↓  
¿Datos válidos?  
→ No → Mostrar error → Volver a pedir datos  
→ Sí ↓  
Crear nuevo nodo (Proceso)  
↓  
¿Lista vacía?  
→ Sí → Nuevo nodo = inicio de lista  
→ No ↓  
Recorrer lista hasta el final  
↓  
Insertar nodo al final  
↓  
Llamar a EncolarPorPrioridad  
↓  
Mostrar "Proceso registrado correctamente"  
↓  
Fin  

---

## 2. Diagrama de Flujo: Modificar Prioridad

```text
Inicio
↓
Solicitar ID del proceso
↓
¿Lista vacía?
→ Sí → Mostrar "No hay procesos registrados" → Fin
→ No ↓
Recorrer lista enlazada
↓
¿Proceso encontrado?
→ No → Mostrar "Ese ID no existe en el sistema" → Fin
→ Sí ↓
Mostrar datos del proceso
↓
Solicitar nueva prioridad
↓
Actualizar prioridad del proceso
↓
Llamar a ReacomodarColaCPU
↓
Mostrar "Prioridad actualizada"
↓
Fin
```

## 2.1 Diagramas de Flujo

A continuación, se describen los diagramas de flujo correspondientes a los procesos principales del sistema:

### Diagrama de flujo: Registrar Proceso

Inicio  
↓  
Solicitar ID, nombre y prioridad  
↓  
Crear nuevo nodo (Proceso)  
↓  
¿Lista vacía?  
→ Sí: Insertar como primer nodo  
→ No: Recorrer hasta el último nodo e insertar  
↓  
Encolar proceso según prioridad  
↓  
Mostrar mensaje de confirmación  
↓  
Fin  

---

### Diagrama de flujo: Modificar Prioridad de Proceso

Inicio  
↓  
Solicitar ID del proceso  
↓  
¿Lista vacía?  
→ Sí: Mostrar mensaje "No hay procesos" y finalizar  
↓  
Recorrer lista enlazada  
↓  
¿Proceso encontrado?  
→ No: Mostrar mensaje "No encontrado"  
→ Sí:  
  Actualizar prioridad  
  Reordenar cola de CPU  
↓  
Mostrar confirmación  
↓  
Fin  

---

## 2.2 Justificación del diseño

El diseño del sistema se basa en el uso de estructuras de datos dinámicas, lo que permite una gestión flexible de los procesos sin depender de un tamaño fijo en memoria.

La lista enlazada facilita la inserción y eliminación de procesos en tiempo de ejecución, lo que optimiza el uso de memoria y evita limitaciones propias de estructuras estáticas.

Por otro lado, la cola de prioridad permite simular de manera eficiente la planificación del CPU, garantizando que los procesos más importantes sean atendidos primero, lo cual mejora el rendimiento general del sistema.

Asimismo, el uso de una pila para la gestión de memoria permite representar de forma sencilla el comportamiento de asignación y liberación de recursos, siguiendo un orden lógico y eficiente.

En conjunto, este diseño permite un flujo organizado del sistema, optimizando tanto el manejo de datos como la ejecución de procesos.

---

# Capítulo 4: Evidencias de Trabajo en Equipo

## 1. Plan de Trabajo

El desarrollo del proyecto se organizó en un cronograma de una semana para la primera entrega, distribuyendo tareas específicas a cada integrante del equipo.

- Día 1: Organización del equipo, asignación de roles y creación del repositorio en GitHub.  
- Día 2 - 3: Desarrollo del análisis del problema y diseño de estructuras de datos.  
- Día 4: Elaboración de pseudocódigo y diagramas de flujo.  
- Día 5: Integración de avances y revisión general.  
- Día 6: Correcciones finales.  
- Día 7: Entrega del trabajo.  

---

## 2. Acta de Reunión N° 01

Fecha: [21/05/20026]  
Hora: [7:00 pm a 0:00 am]  
Medio: [Virtual]  

Líder: Caleb
Integrantes: Gabriel, Angel, James, Caleb  

Objetivos:
- Analizar la consigna del proyecto  
- Definir roles del equipo  
- Planificar el desarrollo del trabajo  

Acuerdos:
- Gabriel será el líder del equipo  
- Se trabajará con GitHub utilizando ramas individuales  
- Cada integrante desarrollará su parte asignada  

Compromisos:
- Gabriel: coordinación, diagramas y revisión final  
- Angel: análisis del problema y requerimientos  
- James: estructuras de datos  
- Caleb: pseudocódigo  

Conclusión:
Se estableció una organización clara del equipo y se definieron las tareas para iniciar el desarrollo del proyecto.

---

## 3. Uso de GitHub

El equipo utilizó GitHub como herramienta de control de versiones, permitiendo organizar el trabajo de manera colaborativa.

Cada integrante trabajó en su propia rama, realizando commits que evidencian su participación. Posteriormente, el líder del equipo se encargó de integrar los cambios mediante merges hacia la rama principal.

Esto permitió mantener un historial claro de avances y asegurar la correcta integración del proyecto.
