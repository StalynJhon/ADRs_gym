# ADR-042: Estrategia de Paginación de Datos (Offset-based)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Listados como el "Historial de Rutinas" o "Catálogo de Ejercicios" pueden crecer indefinidamente. Intentar descargar y renderizar todos los registros de una sola vez provocaría tiempos de carga inaceptables y desbordamiento de memoria (OOM) en el dispositivo móvil.

## 2. Decisión
Implementar **Paginación basada en Offset** con carga incremental ("Infinite Scroll").

## 3. Justificación
* **Eficiencia de Memoria:** Solo se mantienen en memoria y se renderizan los elementos visibles y un pequeño buffer, utilizando `ListView.builder` de Flutter.
* **Optimización de Red:** Se solicitan bloques de datos pequeños (ej: 20 items) bajo demanda.
* **UX Fluida:** El usuario percibe una lista infinita sin interrupciones explícitas de paginación (botones de "Siguiente página").

## 4. Alternativas Consideradas
* **Paginación Numerada:** Descartada. Es un patrón de UI web de escritorio, incómodo en pantallas táctiles móviles.
* **Carga Total:** Descartada por problemas de escalabilidad y rendimiento.

## 5. Consecuencias
* **Positivas:** Rendimiento estable independientemente del tamaño total del dataset.
* **Negativas:** Complejidad en la gestión de estado de la lista (loading, error, end-of-list) y dificultad para hacer "deep linking" a un item en la página 50.