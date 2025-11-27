# ADR-008: Estrategia de Ramas (Feature Branch Workflow)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Múltiples desarrolladores trabajan en paralelo. Modificar `main` directamente es riesgoso.

## 2. Decisión
Adoptar **Feature Branch Workflow**.

## 3. Justificación
Cada funcionalidad se desarrolla en una rama aislada (`feature/login`) y se fusiona a `main` mediante Pull Requests, garantizando estabilidad.

## 4. Alternativas Consideradas
* **Gitflow:** Descartado por ser excesivamente complejo para dos personas.
* **Trunk-based:** Descartado por requerir un pipeline de CI/CD muy maduro que aún no tenemos.

## 5. Consecuencias
* **Positivas:** Aislamiento de errores y revisión de código obligatoria.
* **Negativas:** Posibles conflictos de fusión si las ramas viven mucho tiempo.