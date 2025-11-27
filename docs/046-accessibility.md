# ADR-046: Accesibilidad Semántica (A11y)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación debe ser inclusiva y utilizable por personas con discapacidades visuales o motoras. Los lectores de pantalla (TalkBack/VoiceOver) no pueden interpretar interfaces gráficas complejas (como un botón que es solo un icono) sin metadatos adicionales.

## 2. Decisión
Implementar el widget **Semantics** en componentes interactivos clave.

## 3. Justificación
* **Árbol Semántico:** Construye una estructura paralela al árbol de widgets que describe la interfaz a los servicios de accesibilidad (ej: "Botón, etiquetado como 'Iniciar Rutina', doble toque para activar").
* **Responsabilidad Social:** Cumplimiento con principios éticos de desarrollo de software y estándares WCAG.
* **Navegabilidad:** Mejora la experiencia para usuarios que navegan por teclado o switch access.

## 4. Alternativas Consideradas
* **Ignorar Accesibilidad:** Descartada. Inaceptable en un proyecto de software moderno.

## 5. Consecuencias
* **Positivas:** Ampliación de la base de usuarios y calidad de producto superior.
* **Negativas:** Requiere auditoría y etiquetado manual de componentes visuales no estándar.