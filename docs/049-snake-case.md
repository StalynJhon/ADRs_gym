# ADR-049: Convención de Nomenclatura de Archivos (Snake Case)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
En sistemas operativos mixtos (Windows, macOS, Linux), el manejo de mayúsculas y minúsculas en nombres de archivos varía (Case-sensitive vs Case-insensitive). Nombres inconsistentes causan errores de compilación y control de versiones (Git) difíciles de rastrear.

## 2. Decisión
Adoptar estrictamente **snake_case** (minúsculas con guiones bajos) para todos los archivos y carpetas del proyecto (`user_profile_screen.dart`).

## 3. Justificación
* **Estándar de Dart:** Es la convención oficial recomendada por el equipo de Dart/Flutter.
* **Compatibilidad:** Garantiza que los nombres de archivos sean seguros y consistentes en cualquier sistema de archivos y servidor de CI/CD (Linux).
* **Legibilidad:** Facilita la lectura de nombres largos y la identificación visual rápida en el explorador de proyectos.

## 4. Alternativas Consideradas
* **camelCase / PascalCase:** Comunes en otros lenguajes (Java/C#), pero violan las guías de estilo de Dart y pueden causar conflictos en Git en Windows.

## 5. Consecuencias
* **Positivas:** Prevención de errores de infraestructura y adherencia a estándares de la comunidad.
* **Negativas:** Ninguna.