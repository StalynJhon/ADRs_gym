# ADR-005: Estrategia de Autenticación (JWT)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La comunicación app-servidor debe ser segura y sin estado (stateless) para permitir escalabilidad. Se necesita validar la identidad del usuario en cada petición.

## 2. Decisión
Implementar **JSON Web Tokens (JWT)**.

## 3. Justificación
* **Stateless:** El servidor no necesita guardar la sesión en memoria, facilitando el escalado horizontal.
* **Estándar Móvil:** Los JWT son fáciles de almacenar en el dispositivo y enviar en los headers HTTP.

## 4. Alternativas Consideradas
* **Sesiones (Cookies):** Descartado por la complejidad de manejo en clientes móviles nativos.
* **OAuth2 Externo:** Considerado como complemento, pero se requiere un sistema propio de credenciales primero.

## 5. Consecuencias
* **Positivas:** Escalabilidad del backend y facilidad de implementación.
* **Negativas:** Dificultad para revocar tokens antes de su expiración sin listas negras.