# ADR-033: Resolución de Conflictos de Datos Distribuidos

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
En una arquitectura Offline-First, múltiples instancias de la aplicación (mismo usuario en dos dispositivos) pueden modificar el mismo recurso (ej: Rutina) simultáneamente sin conexión. Al sincronizar, el sistema debe decidir qué versión prevalece de manera determinista.

## 2. Decisión
Adoptar la estrategia **Last Write Wins (LWW)** basada en Timestamp UTC.

## 3. Justificación
* **Simplicidad Determinista:** Es el algoritmo más eficiente de implementar para sistemas donde la colisión de edición es poco frecuente (un usuario raramente edita su rutina en dos teléfonos al mismo tiempo). El registro con la fecha de modificación más reciente sobrescribe al anterior.
* **Bajo Overhead:** No requiere almacenar el historial completo de cambios (Deltas) ni intervención manual del usuario.

## 4. Alternativas Consideradas
* **Tipos de Datos Replicados Libres de Conflicto (CRDTs):** Evaluada. Aunque es la solución matemáticamente "correcta" para sistemas distribuidos, su complejidad de implementación excede los recursos del MVP.
* **Resolución Manual:** Descartada. Presentar diálogos de "Conflicto de fusión" al usuario final degrada la experiencia de uso.

## 5. Consecuencias
* **Positivas:** Lógica de sincronización predecible y fácil de depurar.
* **Negativas:** Posible pérdida de datos ("Lost Update Problem") si dos cambios ocurren en milisegundos o si el reloj del dispositivo está severamente desincronizado (mitigable usando tiempo del servidor).