# ADR-040: Estrategia de Versionado de API (URI Path)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Las aplicaciones móviles instaladas en los dispositivos de los usuarios no se actualizan instantáneamente. Es inevitable que coexistan versiones antiguas del cliente con versiones nuevas. Cambios en el contrato de la API (Breaking Changes) podrían romper la funcionalidad para usuarios no actualizados.

## 2. Decisión
Implementar versionado explícito en la ruta de la URI (ej: `/api/v1/users`).

## 3. Justificación
* **Explícitud:** Hace evidente qué versión del contrato está consumiendo cada cliente.
* **Evolución Segura:** Permite desplegar una `/api/v2/` con cambios estructurales drásticos sin afectar a los usuarios que siguen consumiendo `/api/v1/`, facilitando una migración gradual.
* **Facilidad de Enrutamiento:** Simplifica la configuración de balanceadores de carga o proxies inversos (Nginx) para dirigir tráfico a diferentes servicios backend si fuera necesario.

## 4. Alternativas Consideradas
* **Versionado por Headers:** Descartada. Más complejo de probar y cachear en herramientas estándar.
* **Sin Versionado:** Descartada. Riesgo inaceptable de interrupción de servicio (Downtime) ante cualquier refactorización del backend.

## 5. Consecuencias
* **Positivas:** Garantía de compatibilidad hacia atrás y estabilidad operativa.
* **Negativas:** Requiere mantener código duplicado temporalmente (controladores V1 y V2) durante periodos de transición.