# ADR-011: Patrón de Diseño de Acceso a Datos (Repository Pattern)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La app usa SQLite local y API remota. La UI no debe conocer la fuente del dato.

## 2. Decisión
Implementar el **Patrón Repositorio**.

## 3. Justificación
Crea una capa de abstracción que decide si buscar datos en la BD local, caché o API, desacoplando la UI de la lógica de datos.

## 4. Alternativas Consideradas
* **Acceso directo en UI:** Descartado por alto acoplamiento y dificultad de testing.

## 5. Consecuencias
* **Positivas:** Código mantenible y facilita la lógica "Offline-first".
* **Negativas:** Añade una capa extra de clases (boilerplate).