# ADR-034: Análisis Estático de Código y Calidad (Linting)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
En un entorno de desarrollo colaborativo, la falta de estándares de codificación estrictos conduce a una base de código heterogénea, difícil de leer y propensa a errores sutiles (anti-patrones). Se requiere un mecanismo automatizado para imponer disciplina.

## 2. Decisión
Implementar el paquete **flutter_lints** con reglas estrictas en el archivo `analysis_options.yaml`.

## 3. Justificación
* **Detección Preventiva:** Identifica problemas potenciales (variables no usadas, tipos inseguros, imports cíclicos) en tiempo de escritura, antes de la compilación.
* **Estandarización:** Forza el cumplimiento de las guías de estilo oficiales de Dart (Effective Dart), asegurando que el código escrito por Jonathan se vea idéntico al escrito por Jofre.
* **Optimización:** Sugiere el uso de constructores `const` donde es posible, lo que mejora el rendimiento de reconstrucción de widgets en Flutter.

## 4. Alternativas Consideradas
* **Sin Linter:** Descartada. Conduce inevitablemente a deuda técnica acumulada.
* **Very Good Analysis:** Una opción más rigurosa, pero `flutter_lints` es el estándar oficial recomendado por Google para proyectos nuevos.

## 5. Consecuencias
* **Positivas:** Código mantenible, educativo y reducción de bugs triviales.
* **Negativas:** Puede generar fricción inicial al obligar a corregir advertencias de estilo antes de avanzar.