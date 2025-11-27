# ADR-025: Arquitectura de Disponibilidad Offline (Offline-First)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La conectividad móvil es inherentemente inestable, especialmente en infraestructuras cerradas como gimnasios. La aplicación no debe degradar su funcionalidad principal (ver rutinas, marcar asistencia) ante la ausencia de red. El modelo tradicional "Online-Only" es inaceptable para la UX objetivo.

## 2. Decisión
Adoptar una arquitectura **Offline-First** con sincronización diferida.

## 3. Justificación
* **Fuente de Verdad Local:** La aplicación lee y escribe siempre en la base de datos local (SQLite). La interfaz responde inmediatamente (Optimistic UI) sin esperar latencia de red.
* **Sincronización en Segundo Plano:** Un proceso independiente se encarga de replicar los cambios locales al servidor y descargar actualizaciones cuando la conexión se restablece.
* **Resiliencia:** Garantiza que el usuario pueda completar su flujo de trabajo crítico independientemente del estado de la red.

## 4. Alternativas Consideradas
* **Network-First con Caché:** Descartada. Implica esperar un timeout de red antes de mostrar datos locales, creando una experiencia lenta y frustrante ("Loading spinners" infinitos).
* **Solo Online:** Descartada por incumplir los requisitos no funcionales de disponibilidad.

## 5. Consecuencias
* **Positivas:** Experiencia de usuario extremadamente rápida y confiable.
* **Negativas:** Aumenta significativamente la complejidad de la arquitectura. Requiere lógica para resolución de conflictos de datos y manejo de colas de sincronización.