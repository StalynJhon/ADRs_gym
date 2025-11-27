# ADR-036: Gestión de Tipografía (Google Fonts)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La legibilidad es fundamental en una aplicación de seguimiento de actividad. Depender de las fuentes predeterminadas del sistema operativo resulta en inconsistencias visuales y problemas de maquetación entre diferentes fabricantes de Android.

## 2. Decisión
Utilizar el paquete **google_fonts** para la carga dinámica y caché de tipografías.

## 3. Justificación
* **Consistencia Cross-Platform:** Asegura que la aplicación se vea exactamente igual en un Samsung, un Pixel y un iPhone, utilizando fuentes de alta calidad (ej: Roboto, Poppins).
* **Gestión de Assets:** Evita inflar el tamaño del binario de la aplicación (.apk/.ipa) almacenando archivos `.ttf` manualmente. Las fuentes se descargan bajo demanda y se cachean.
* **Licenciamiento:** Acceso a una librería masiva de fuentes Open Source libres de problemas de derechos de autor.

## 4. Alternativas Consideradas
* **Fuentes Locales (Assets):** Descartada para fuentes secundarias por el impacto en el peso de la app.
* **Fuentes del Sistema:** Descartada por la imprevisibilidad del renderizado en dispositivos Android personalizados.

## 5. Consecuencias
* **Positivas:** Estética profesional y control tipográfico granular.
* **Negativas:** La primera carga de la fuente requiere conexión a internet (se mitiga empaquetando solo la fuente principal).