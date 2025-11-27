# ADR-039: Algoritmo de Filtrado de Contenido en Memoria

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El módulo de "Ayuda a la Recuperación" debe permitir filtrar consejos basándose en zonas del cuerpo o tipo de dolor. Dado que el catálogo de consejos es finito y cabe en la memoria del dispositivo, realizar consultas al servidor por cada filtro introduce latencia innecesaria.

## 2. Decisión
Implementar un sistema de filtrado basado en **Tags (Etiquetas)** ejecutado en el cliente.

## 3. Justificación
* **Latencia Cero:** El filtrado ocurre instantáneamente (O(n)) en el dispositivo, ofreciendo una UX fluida y reactiva.
* **Simplicidad:** Se utiliza programación funcional (`List.where()`) sobre los datos cacheados, evitando la complejidad de construir queries SQL dinámicas en el backend para esta funcionalidad específica.
* **Disponibilidad:** Funciona perfectamente sin conexión a internet.

## 4. Alternativas Consideradas
* **Búsqueda en Servidor (Full-Text Search):** Descartada. Excesiva para un dataset pequeño (<500 items) y dependiente de la red.
* **Indexación Local Compleja:** Descartada. Un filtrado simple de arrays es suficiente.

## 5. Consecuencias
* **Positivas:** Rendimiento percibido instantáneo y reducción de carga en el servidor API.
* **Negativas:** Si el dataset crece exponencialmente en el futuro (miles de consejos), habrá que migrar a paginación y filtrado en servidor.