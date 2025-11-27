# ADR-024: Estrategia de Observabilidad y Logging (Winston/Morgan)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
En un entorno de producción, la invisibilidad del comportamiento interno del servidor impide el diagnóstico de errores. Se requiere un sistema que registre tanto el tráfico HTTP entrante como los eventos internos de la aplicación de manera estructurada y persistente.

## 2. Decisión
Implementar un sistema híbrido con **Morgan** (Logging HTTP) y **Winston** (Logging de Aplicación).

## 3. Justificación
* **Separación de Responsabilidades:** Morgan intercepta automáticamente todas las peticiones (método, URL, status, tiempo de respuesta), proveyendo métricas de tráfico. Winston permite al desarrollador instrumentar el código para registrar lógica de negocio y errores con niveles de severidad (Info, Warn, Error).
* **Transportes Múltiples:** Winston permite configurar múltiples salidas ("transports"), permitiendo escribir en consola durante desarrollo y rotar archivos de log en producción simultáneamente.
* **Formato Estructurado:** Configuración de salida en formato JSON para facilitar la futura ingestión de logs por herramientas de análisis.

## 4. Alternativas Consideradas
* **Console.log:** Descartada. Es síncrona (bloqueante en ciertos entornos), no estructurada y efímera.
* **Bunyan:** Alternativa válida, pero Winston fue elegida por su comunidad más amplia y flexibilidad de configuración de formatos.

## 5. Consecuencias
* **Positivas:** Capacidad de auditoría, depuración post-mortem y monitoreo de salud del sistema.
* **Negativas:** Requiere gestión de espacio en disco (Log Rotation) para evitar saturación del servidor.