# ADR-045: Política de Seguridad de Sesiones (Token Rotation)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Mantener sesiones abiertas indefinidamente (tokens infinitos) es un riesgo de seguridad mayor si el dispositivo es comprometido. Sin embargo, cerrar la sesión frecuentemente degrada la experiencia del usuario (UX).

## 2. Decisión
Implementar **JWT de corta duración** (Access Token) con mecanismo de **Refresh Token**.

## 3. Justificación
* **Balance Seguridad/UX:** El Access Token (vida corta, ej: 15 min) se usa para peticiones. Si es robado, su utilidad es limitada. El Refresh Token (vida larga, ej: 7 días) permite renovar el acceso sin pedir credenciales al usuario, siempre que no haya sido revocado en el servidor.
* **Revocación:** Permite invalidar el acceso de un usuario específico (ej: "Cerrar sesión en todos los dispositivos") simplemente invalidando el Refresh Token en la base de datos.

## 4. Alternativas Consideradas
* **Sesión Eterna:** Descartada por insegura.
* **Logout forzado por tiempo:** Descartada por ser molesta para el usuario diario.

## 5. Consecuencias
* **Positivas:** Arquitectura de seguridad robusta y estándar en la industria (OAuth2 style).
* **Negativas:** Aumenta la complejidad del cliente HTTP (Interceptor) para manejar el flujo de renovación automática (401 -> Refresh -> Retry).