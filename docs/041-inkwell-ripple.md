# ADR-041: Feedback Visual de Interacción (Material Ripple)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
En interfaces táctiles, la falta de respuesta visual inmediata al tocar un elemento genera incertidumbre ("¿Registró mi toque?"). Esto lleva a toques repetidos y frustración.

## 2. Decisión
Implementar el efecto **InkWell / Ripple** (Onda de tinta) en todos los elementos interactivos.

## 3. Justificación
* **Affordance:** Comunica claramente qué elementos son interactivos y cuáles son estáticos.
* **Feedback Inmediato:** Proporciona confirmación visual en el instante del contacto (touchstart), mejorando la percepción de velocidad y responsividad de la aplicación.
* **Consistencia:** Es el comportamiento estándar esperado en el ecosistema Android y Material Design.

## 4. Alternativas Consideradas
* **Cambio de Estado (Color/Opacidad):** Usado como complemento, pero por sí solo es menos "orgánico" y moderno que la animación de onda.
* **Sin Feedback:** Descartada. Genera una experiencia de usuario "muerta" y de baja calidad.

## 5. Consecuencias
* **Positivas:** Mejora sustancial en la usabilidad y la sensación de calidad del software.
* **Negativas:** Costo de rendimiento despreciable en dispositivos modernos.