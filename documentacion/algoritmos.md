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

    Si Encontrado == Falso Entonces
        Escribir "Ese ID no existe en el sistema."
    FinSi
FinAlgoritmo
