# ADR-044: Aseguramiento de Calidad de Lógica (Unit Testing)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación contiene lógica de negocio pura crítica, como cálculos de IMC, validación de formularios y transformación de datos de API. Probar estas funciones manualmente tras cada cambio es ineficiente y no garantiza la ausencia de regresiones.

## 2. Decisión
Implementar **Pruebas Unitarias** utilizando el paquete `flutter_test`.

## 3. Justificación
* **Aislamiento:** Permite verificar la corrección de funciones individuales de manera determinista, sin dependencias de UI, base de datos o red (usando Mocks).
* **Prevención de Regresiones:** Actúa como una red de seguridad que alerta inmediatamente si un cambio de código rompe una funcionalidad existente.
* **Documentación Viva:** Los tests sirven como ejemplos de uso y documentación del comportamiento esperado del código.

## 4. Alternativas Consideradas
* **Testing Manual Exclusivo:** Descartada. No escala y es susceptible al error humano.
* **Integration Testing:** Se usará, pero el Unit Testing es la base de la pirámide de pruebas por su velocidad de ejecución.

## 5. Consecuencias
* **Positivas:** Alta confiabilidad en la lógica core y refactorización segura.
* **Negativas:** Requiere inversión de tiempo en escribir y mantener los tests (aprox. 20-30% extra de tiempo de desarrollo).