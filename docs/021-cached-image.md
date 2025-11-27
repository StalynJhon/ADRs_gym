# ADR-021: Optimización de Red y Caché de Imágenes

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Los módulos de Nutrición y Ejercicios dependen fuertemente de recursos visuales remotos. Cargar estas imágenes vía HTTP en cada renderizado generaría un consumo excesivo de ancho de banda móvil, lentitud en el scroll (jank) y una experiencia de usuario deficiente en condiciones de red inestable.

## 2. Decisión
Implementar **cached_network_image** con política de caché LRU (Least Recently Used).

## 3. Justificación
* **Persistencia Local:** Almacena automáticamente los binarios de las imágenes en el sistema de archivos del dispositivo, permitiendo su carga instantánea en sesiones futuras sin uso de red.
* **Gestión de Memoria:** Maneja eficientemente la decodificación y desalojo de imágenes en memoria para evitar desbordamientos (OOM - Out Of Memory).
* **Feedback Visual:** Provee constructores para mostrar "Placeholders" (mientras carga) y widgets de error (si falla), mejorando la UX percibida.

## 4. Alternativas Consideradas
* **Image.network (Nativo):** Descartada categóricamente. No ofrece persistencia en disco; las imágenes se pierden al cerrar la app, obligando a re-descargarlas siempre.
* **Pre-caching manual:** Descartada por la complejidad de escribir un gestor de descargas y caché propio que maneje concurrencia y limpieza de disco.

## 5. Consecuencias
* **Positivas:** Drástica reducción de latencia y consumo de datos. Soporte visual offline.
* **Negativas:** Ocupación variable del almacenamiento interno del usuario, requiriendo configuración de límites máximos de caché (Stale time).