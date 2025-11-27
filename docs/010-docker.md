# ADR-010: Contenedorización (Docker)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Se debe eliminar el problema "en mi máquina funciona" y unificar entornos de desarrollo y producción.

## 2. Decisión
Utilizar **Docker** y **Docker Compose**.

## 3. Justificación
Empaqueta la aplicación y base de datos con todas sus dependencias, asegurando paridad absoluta entre entornos.

## 4. Alternativas Consideradas
* **Instalación Manual:** Descartado por ser propensa a errores de configuración.
* **Máquinas Virtuales:** Descartado por alto consumo de recursos.

## 5. Consecuencias
* **Positivas:** Despliegue predecible y onboarding rápido.
* **Negativas:** Curva de aprendizaje inicial de Docker.