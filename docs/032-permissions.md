# ADR-032: Gestión de Permisos de Sistema bajo Demanda

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación requiere acceso a capacidades sensibles del hardware (Cámara, Galería, Notificaciones). Solicitar todos los permisos al arrancar la aplicación (Onboarding) genera fricción, desconfianza y altas tasas de rechazo por parte del usuario.

## 2. Decisión
Implementar una estrategia de **Solicitud Just-in-Time (JIT)** mediante el paquete `permission_handler`.

## 3. Justificación
* **Contextualización:** El usuario entiende *por qué* se pide un permiso porque ocurre como respuesta directa a una acción suya (ej: al tocar "Subir Foto" se pide acceso a Galería).
* **Manejo de Estados Complejos:** El paquete abstrae la complejidad de gestionar los estados de permisos en diferentes versiones de Android/iOS (Granted, Denied, Permanently Denied, Restricted).
* **Compliance:** Alineación con las guías de diseño de privacidad de Google Play y Apple App Store.

## 4. Alternativas Consideradas
* **Solicitud al Inicio:** Descartada por ser un antipatrón de UX que reduce la retención de usuarios.
* **Manejo Nativo Manual:** Descartada. Requeriría escribir código de plataforma específico (Kotlin/Swift) para cada permiso, aumentando la deuda técnica.

## 5. Consecuencias
* **Positivas:** Mayor confianza del usuario y menor tasa de desinstalación.
* **Negativas:** Requiere lógica de UI adicional para manejar casos donde el usuario deniega el permiso permanentemente (ej: mostrar botón para ir a Ajustes).