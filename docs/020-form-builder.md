# ADR-020: Gestión y Validación de Formularios (FormBuilder)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación maneja múltiples formularios críticos (Login, Registro, Perfil, Creación de Rutinas). La gestión manual de `TextEditingControllers`, `FocusNodes` y lógica de validación campo por campo genera una gran cantidad de código repetitivo (boilerplate) y dificulta la recolección de datos finales.

## 2. Decisión
Utilizar el ecosistema **flutter_form_builder**.

## 3. Justificación
* **Reducción de Boilerplate:** Elimina la necesidad de instanciar controladores manualmente. Los campos se conectan automáticamente a un mapa de datos global del formulario.
* **Validación Compuesta:** Permite encadenar reglas de validación (ej: `required`, `email`, `minLength`) de manera declarativa y reutilizable.
* **Tipado de Datos:** Facilita la extracción de los datos del formulario como un objeto JSON limpio listo para enviar a la API, evitando errores de conversión manual.

## 4. Alternativas Consideradas
* **Formularios Nativos (Vanilla):** Descartada. El manejo manual de estados de error y foco en formularios largos es propenso a bugs y fugas de memoria si no se desechan (dispose) correctamente los controladores.
* **Reactive Forms:** Descartada por su alta complejidad inspirada en Angular, excesiva para los requisitos actuales.

## 5. Consecuencias
* **Positivas:** Código de UI más limpio, validación robusta y experiencia de usuario mejorada (validación en tiempo real).
* **Negativas:** Fuerte acoplamiento con la librería; personalizar widgets de entrada (inputs) muy específicos puede requerir wrappers adicionales.