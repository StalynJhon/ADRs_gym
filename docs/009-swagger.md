# ADR-009: Documentación de API (OpenAPI/Swagger)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El equipo móvil necesita saber exactamente qué endpoints existen sin leer el código del servidor.

## 2. Decisión
Implementar **Swagger (OpenAPI 3.0)**.

## 3. Justificación
Provee una interfaz web interactiva para probar peticiones y sirve como contrato de verdad entre frontend y backend.

## 4. Alternativas Consideradas
* **Wiki/Word:** Descartado porque se desactualiza rápidamente.
* **Colecciones Postman:** Útil, pero Swagger se integra mejor en el código fuente.

## 5. Consecuencias
* **Positivas:** Reducción de errores de comunicación.
* **Negativas:** Requiere disciplina para mantener las anotaciones actualizadas.