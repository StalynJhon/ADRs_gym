# ADR-043: Generación Automatizada de Iconografía Adaptativa

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Android e iOS requieren múltiples variantes del icono de la aplicación (distintas resoluciones, formas, máscaras, notificaciones). Generar y configurar estos assets manualmente en los proyectos nativos es propenso a errores y consume tiempo de diseño valioso.

## 2. Decisión
Utilizar la herramienta **flutter_launcher_icons** en el pipeline de desarrollo.

## 3. Justificación
* **Automatización:** Genera automáticamente todas las densidades de píxeles requeridas (mdpi, hdpi, xxhdpi, etc.) a partir de un único archivo fuente vectorial o de alta resolución.
* **Adaptive Icons:** Soporta el estándar de iconos adaptativos de Android (capa de fondo + capa de frente), asegurando que el icono se integre visualmente con el tema del dispositivo del usuario (círculo, cuadrado redondeado, gota).
* **Mantenibilidad:** Permite actualizar la imagen de marca de la app en minutos modificando una sola configuración.

## 4. Alternativas Consideradas
* **Generación Manual:** Descartada. Tediosa y propensa a errores de nombrado o dimensión.
* **Servicios Web:** Válida, pero requiere pasos manuales de copia de archivos a las carpetas de estructura nativa.

## 5. Consecuencias
* **Positivas:** Consistencia profesional de marca y ahorro de tiempo.
* **Negativas:** Ninguna relevante.