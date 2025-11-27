# ADR-018: Motor de Visualización de Calendario (TableCalendar)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El módulo de "Seguimiento de Asistencia" requiere visualizar datos temporales complejos en una cuadrícula mensual interactiva. Calcular manualmente la lógica de fechas (años bisiestos, inicio de semana, días por mes) y dibujar la UI correspondiente es propenso a errores matemáticos y consume un tiempo de desarrollo excesivo.

## 2. Decisión
Integrar el paquete **table_calendar** para la gestión visual de fechas.

## 3. Justificación
* **Robustez Lógica:** La librería maneja internamente toda la complejidad aritmética de fechas y localización, asegurando precisión en el renderizado del calendario.
* **Personalización Extensible:** Ofrece una API de "Builders" que permite inyectar widgets personalizados en días específicos (ej: marcar un día con un icono de "Check" verde si se cumplió la rutina), cumpliendo con los requisitos de UI del proyecto.
* **Interactividad:** Soporta gestos nativos (swipe horizontal/vertical) para cambio de meses y selección de rangos de fechas "out-of-the-box".

## 4. Alternativas Consideradas
* **Syncfusion Flutter Calendar:** Descartada a pesar de su potencia, debido a su modelo de licenciamiento dual que podría complicar el cumplimiento legal del proyecto académico/comercial.
* **Grid View Custom:** Descartada por la alta complejidad de mantenimiento. Un error en el cálculo de días desalinearía visualmente toda la semana, afectando la credibilidad de la app.

## 5. Consecuencias
* **Positivas:** Ahorro estimado de 40 horas de desarrollo. Interfaz rica y libre de bugs lógicos de fechas.
* **Negativas:** Aumenta el tamaño del bundle de la aplicación. Requiere aprendizaje de la API específica del paquete para personalizaciones avanzadas.