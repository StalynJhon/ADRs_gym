# ADR-012: Sistema de Notificaciones Externo (FCM)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Es vital enviar recordatorios y alertas a los dispositivos móviles.

## 2. Decisión
Integrar **Firebase Cloud Messaging (FCM)**.

## 3. Justificación
Solución estándar, gratuita y confiable de Google que se integra nativamente con Android e iOS.

## 4. Alternativas Consideradas
* **WebSockets propios:** Descartado por alto consumo de batería y complejidad.
* **OneSignal:** Descartado por costos potenciales al escalar.

## 5. Consecuencias
* **Positivas:** Envío de notificaciones confiable sin costo inicial.
* **Negativas:** Dependencia de la infraestructura de Google.