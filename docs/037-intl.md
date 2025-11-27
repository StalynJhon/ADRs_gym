# ADR-037: Internacionalización y Localización (Intl)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación maneja datos sensibles al formato cultural, como fechas de calendario, monedas y unidades de medida. Mostrar una fecha como "MM/DD/AAAA" a un usuario que espera "DD/MM/AAAA" causa confusión y errores.

## 2. Decisión
Implementar el paquete **intl** y la lógica de delegados de localización.

## 3. Justificación
* **Formateo Automático:** Adapta la representación de fechas y números basándose en el `Locale` del dispositivo del usuario en tiempo de ejecución.
* **Escalabilidad:** Prepara la arquitectura para soportar múltiples idiomas en el futuro (i18n) sin tener que refactorizar todo el código de UI (Strings hardcodeados).
* **Estándar:** Es la librería oficial mantenida por el equipo de Dart, garantizando compatibilidad con el estándar CLDR (Common Locale Data Repository).

## 4. Alternativas Consideradas
* **Formateo Manual de Strings:** Descartada categóricamente. Es propenso a errores, difícil de mantener y no cubre casos borde (pluralización, género).
* **Moment.js (Port):** Descartada por ser innecesariamente pesada comparada con `intl` nativo.

## 5. Consecuencias
* **Positivas:** Experiencia de usuario nativa y profesional. Código preparado para expansión global.
* **Negativas:** Requiere un paso de inicialización de datos de localización al arranque de la app.