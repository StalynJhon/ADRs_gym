# ADR-028: Formato de Distribución y Empaquetado (Android App Bundle)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La distribución de la aplicación en Android requiere generar un binario instalable. El uso de APKs tradicionales monolíticos resulta en archivos de gran tamaño que contienen recursos innecesarios para el dispositivo específico del usuario (ej: imágenes xxhdpi en un teléfono de baja resolución).

## 2. Decisión
Generar **Android App Bundles (.aab)** como formato de distribución.

## 3. Justificación
* **Dynamic Delivery:** Google Play utiliza el AAB para generar y firmar APKs optimizados al vuelo para la configuración específica de cada dispositivo (CPU, Idioma, Resolución).
* **Reducción de Tamaño:** Disminuye el tamaño de descarga final para el usuario en aproximadamente un 15-20%, mejorando la tasa de conversión de instalaciones.
* **Requisito de la Tienda:** Es el formato obligatorio actual para publicar nuevas aplicaciones en Google Play Store.

## 4. Alternativas Consideradas
* **APK Universal:** Descartada. Genera un archivo "gordo" con todas las librerías para todas las arquitecturas (ARM, x86), desperdiciando espacio y ancho de banda.
* **APKs por arquitectura (Splits):** Descartada por la complejidad de gestionar y versionar múltiples archivos manualmente.

## 5. Consecuencias
* **Positivas:** Optimización de recursos y cumplimiento de estándares modernos de Android.
* **Negativas:** Ligeramente mayor tiempo de compilación en CI y no se puede instalar directamente en un dispositivo sin una herramienta intermedia (bundletool) durante pruebas locales.