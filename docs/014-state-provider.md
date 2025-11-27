# ADR-014: Gestión de Estado Global (Provider)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La app necesita compartir datos (usuario, tema) entre pantallas sin "prop-drilling".

## 2. Decisión
Utilizar el paquete **Provider**.

## 3. Justificación
Recomendado oficialmente por Google. Es ligero, simple y suficiente para la complejidad del MVP.

## 4. Alternativas Consideradas
* **BLoC:** Descartado por alta verbosidad y complejidad inicial.
* **GetX:** Descartado por uso de patrones no estándar ("magia").

## 5. Consecuencias
* **Positivas:** Separación clara entre lógica y UI.
* **Negativas:** Puede requerir refactorización si la complejidad crece exponencialmente.