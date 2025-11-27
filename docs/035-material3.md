# ADR-035: Sistema de Diseño Visual (Material 3)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Diseñar componentes de UI desde cero consume recursos críticos. La aplicación necesita una identidad visual moderna, coherente y adaptable a diferentes tamaños de pantalla y preferencias de usuario (Modo Oscuro).

## 2. Decisión
Adoptar la especificación **Material Design 3 (Material You)**.

## 3. Justificación
* **Soporte Nativo:** Flutter implementa Material 3 de primera clase (`useMaterial3: true`), ofreciendo componentes accesibles y táctiles listos para usar.
* **Accesibilidad y Color:** El sistema de color dinámico garantiza contraste suficiente y adaptabilidad visual, mejorando la legibilidad.
* **Multiplataforma:** Aunque es originario de Android, Material 3 se ha adaptado para sentirse natural también en iOS mediante ajustes de física y transición, evitando el "Uncanny Valley" de interfaces ajenas.

## 4. Alternativas Consideradas
* **Cupertino (iOS Design):** Descartada como sistema principal único. Implementar lógica para renderizar Cupertino en iOS y Material en Android duplica el esfuerzo de UI.
* **Diseño Ad-Hoc (Custom):** Descartada por falta de un equipo de diseño dedicado.

## 5. Consecuencias
* **Positivas:** Velocidad de prototipado y desarrollo. UI moderna y accesible por defecto.
* **Negativas:** La estética de la aplicación se vincula fuertemente al ecosistema Google, reduciendo la diferenciación de marca única.