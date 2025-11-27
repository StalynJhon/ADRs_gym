# ADR-047: Mecanismo de Feedback Transitorio (Snackbars)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El sistema debe comunicar el resultado de acciones asíncronas (ej: "Guardando...", "Error de conexión", "Rutina completada") sin interrumpir el flujo de trabajo del usuario ni bloquear la pantalla.

## 2. Decisión
Utilizar **Snackbars** (mensajes emergentes inferiores) gestionados por `ScaffoldMessenger`.

## 3. Justificación
* **No Intrusivo:** Informa al usuario manteniendo el contexto visual actual, a diferencia de los Diálogos Modales que requieren una acción explícita de cierre.
* **Contextual:** Permite acciones rápidas relacionadas (ej: botón "Deshacer" al eliminar un item).
* **Gestión de Colas:** `ScaffoldMessenger` administra automáticamente la visualización secuencial de mensajes si ocurren varios eventos rápidos.

## 4. Alternativas Consideradas
* **Toasts (Android Legacy):** Descartada. Ya no son parte de las guías modernas de Material Design y tienen problemas de visualización en versiones recientes de Android.
* **Alert Dialogs:** Descartada para mensajes informativos por ser disruptivos. Solo se usan para confirmaciones críticas.

## 5. Consecuencias
* **Positivas:** Comunicación fluida de estado del sistema.
* **Negativas:** El usuario puede perderse el mensaje si no está prestando atención visual en ese momento exacto.