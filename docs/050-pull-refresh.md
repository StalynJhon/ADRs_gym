# ADR-050: Mecanismo de Actualización Manual de Datos (Pull-to-Refresh)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Aunque la aplicación intenta sincronizar datos automáticamente, pueden existir situaciones donde el usuario perciba que la información está desactualizada (Stale Data) o desee forzar una comprobación de servidor inmediata.

## 2. Decisión
Implementar el patrón gestual **Pull-to-Refresh** (Deslizar para actualizar).

## 3. Justificación
* **Modelo Mental:** Es un gesto universalmente aprendido en aplicaciones móviles para "recargar contenido".
* **Control de Usuario:** Otorga agencia al usuario para resolver estados de incertidumbre sobre la frescura de los datos.
* **Implementación Nativa:** Utiliza el widget `RefreshIndicator` que se integra naturalmente con las listas desplazables.

## 4. Alternativas Consideradas
* **Botón de Actualizar Explícito:** Descartada. Ocupa espacio valioso en la AppBar y es menos ergonómico.
* **Auto-Polling agresivo:** Descartada. Consultar al servidor cada pocos segundos consume batería y datos innecesariamente.

## 5. Consecuencias
* **Positivas:** Mejora la usabilidad y reduce reportes de soporte relacionados con "no veo mis datos".
* **Negativas:** Requiere gestionar correctamente el estado de carga visual para evitar conflictos con otras animaciones.