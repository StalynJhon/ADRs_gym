# ADR-015: Cliente HTTP Móvil (Dio)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Se requiere realizar peticiones HTTP con manejo avanzado de interceptores y errores.

## 2. Decisión
Utilizar el paquete **Dio**.

## 3. Justificación
Permite interceptar peticiones para inyectar tokens JWT automáticamente y maneja errores globales de forma robusta.

## 4. Alternativas Consideradas
* **http (oficial):** Descartado por ser demasiado básico y requerir mucho código manual.

## 5. Consecuencias
* **Positivas:** Código de red limpio y fácil de depurar.
* **Negativas:** Agrega una dependencia externa al proyecto.