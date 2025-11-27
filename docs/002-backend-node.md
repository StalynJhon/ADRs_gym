# ADR-002: Selección del Entorno de Ejecución Backend (Node.js)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación móvil requiere una API REST robusta para manejar la lógica de negocio, autenticación y sincronización de datos. Se necesita una tecnología con alto rendimiento en operaciones de entrada/salida (I/O) y un ecosistema de librerías maduro.

## 2. Decisión
Utilizar **Node.js** con el framework **Express**.

## 3. Justificación
* **I/O No Bloqueante:** Su modelo orientado a eventos es ideal para manejar múltiples conexiones concurrentes de usuarios móviles con baja latencia.
* **Unificación del Lenguaje:** Permite utilizar JavaScript/TypeScript en todo el stack tecnológico, reduciendo el cambio de contexto mental del equipo.
* **Ecosistema NPM:** Acceso al repositorio de librerías más grande del mundo, facilitando integraciones rápidas.

## 4. Alternativas Consideradas
* **Java (Spring Boot):** Descartado por su verbosidad y alto consumo de memoria RAM para un MVP.
* **Python (Django):** Descartado aunque es excelente, Node.js ofrece mejor rendimiento bruto en manejo de peticiones concurrentes en tiempo real.

## 5. Consecuencias
* **Positivas:** Desarrollo veloz de APIs JSON y fácil integración con bases de datos.
* **Negativas:** No es óptimo para tareas de cálculo intensivo de CPU (procesamiento de video pesado).