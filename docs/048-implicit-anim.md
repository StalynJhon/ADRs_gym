# ADR-048: Estrategia de Animaciones Implícitas

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Los cambios bruscos de estado en la interfaz (ej: aparecer/desaparecer elementos, cambios de tamaño) aumentan la carga cognitiva y se sienten "toscos". Se requiere suavizar las transiciones para mejorar la percepción de calidad.

## 2. Decisión
Priorizar el uso de **Implicit Animations** (`AnimatedContainer`, `AnimatedOpacity`, `AnimatedSwitcher`).

## 3. Justificación
* **Abstracción:** Flutter gestiona automáticamente la interpolación de valores (Tweening) y el ciclo de vida de la animación. El desarrollador solo define el estado final y la duración.
* **Rendimiento:** Estas animaciones están optimizadas internamente por el framework para ejecutarse eficientemente sin bloquear el hilo de UI.
* **Mantenibilidad:** Reduce drásticamente el código necesario comparado con el uso de `AnimationController` y `Listeners` explícitos.

## 4. Alternativas Consideradas
* **Animaciones Explícitas:** Reservada solo para coreografías complejas o animaciones en bucle infinito que las implícitas no pueden cubrir.
* **Lottie/Rive:** Reservadas para micro-interacciones de ilustraciones complejas, no para transiciones de UI estándar.

## 5. Consecuencias
* **Positivas:** UI moderna y fluida con bajo costo de implementación.
* **Negativas:** Menor control granular sobre las curvas de física (Physics curves) en escenarios muy específicos.