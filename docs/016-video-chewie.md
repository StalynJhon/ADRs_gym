# ADR-016: Abstracción de Reproductor de Video (Chewie)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El Requisito Funcional de "Rutinas Guiadas" exige la reproducción de contenido multimedia (video) con controles avanzados (Play, Pause, Seek, Fullscreen) y soporte para diferentes relaciones de aspecto. El componente nativo base de Flutter (`video_player`) carece de una capa de interfaz de usuario (UI), lo que obligaría a desarrollar controles visuales desde cero, aumentando el tiempo de desarrollo y el riesgo de inconsistencias visuales entre iOS y Android.

## 2. Decisión
Implementar la librería **Chewie** como capa de controlador de interfaz sobre el plugin `video_player`.

## 3. Justificación
* **Abstracción de UI:** Chewie encapsula la complejidad de gestionar el estado del video y dibuja automáticamente controles nativos (Material en Android, Cupertino en iOS), garantizando una experiencia de usuario familiar.
* **Manejo de Contexto:** Resuelve automáticamente problemas complejos como el manejo de la orientación del dispositivo al entrar/salir de pantalla completa y la gestión de recursos al navegar fuera de la pantalla.
* **Velocidad de Implementación:** Reduce el tiempo de desarrollo del módulo de videos de días a horas.

## 4. Alternativas Consideradas
* **Implementación Custom sobre video_player:** Descartada. Requeriría manejar manualmente `Streams` de posición, buffering y errores, desviando el foco del equipo de la lógica de negocio principal.
* **WebView (YouTube/Vimeo Embed):** Descartada por la pobre integración con el ciclo de vida de la app, presencia de publicidad de terceros y la imposibilidad de funcionamiento offline (caché).

## 5. Consecuencias
* **Positivas:** Interfaz profesional inmediata, soporte robusto de pantalla completa y reducción drástica de código "boilerplate".
* **Negativas:** Dependencia de actualizaciones de terceros para mantener compatibilidad con versiones nuevas del SDK de Flutter.