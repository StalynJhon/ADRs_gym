# ADR-013: Envío de Recordatorios Automáticos (Cron Jobs)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Los recordatorios no deben depender de que el usuario tenga la app abierta.

## 2. Decisión
Utilizar **Cron Jobs** en el servidor backend.

## 3. Justificación
Centraliza la programación de tareas. El servidor verifica periódicamente eventos y dispara notificaciones vía FCM.

## 4. Alternativas Consideradas
* **Alarmas locales:** Viable, pero se pierden si el usuario cambia de dispositivo.

## 5. Consecuencias
* **Positivas:** Control centralizado y consistencia.
* **Negativas:** Carga adicional en el servidor.