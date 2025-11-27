# ADR-019: Estrategia de Enrutamiento Declarativo (GoRouter)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La navegación en la aplicación moderna requiere capacidades avanzadas como rutas anidadas, parámetros en la URL (Deep Linking para compartir rutinas), y lógica de redirección condicional (Guards) para proteger rutas autenticadas. El sistema imperativo `Navigator 1.0` de Flutter se vuelve inmanejable y propenso a errores ("Spaghetti code") en flujos complejos.

## 2. Decisión
Adoptar **GoRouter** como solución de enrutamiento.

## 3. Justificación
* **API Declarativa:** Permite definir la estructura de navegación de toda la app en un solo lugar, mejorando la legibilidad y mantenibilidad.
* **Gestión de Deep Links:** Soporte nativo para abrir la aplicación en pantallas específicas desde enlaces web o notificaciones push, vital para la retención de usuarios.
* **Lógica de Redirección Centralizada:** Facilita la implementación de reglas de seguridad (ej: "Si no hay token, redirigir a /login") sin repetir código en cada pantalla.

## 4. Alternativas Consideradas
* **Navigator 2.0 (Nativo):** Descartada por su extrema verbosidad y complejidad conceptual, que elevaría innecesariamente la curva de aprendizaje del equipo.
* **AutoRoute:** Considerada, pero GoRouter fue seleccionada por ser mantenida oficialmente por el equipo de Google/Flutter, garantizando soporte a largo plazo.

## 5. Consecuencias
* **Positivas:** Arquitectura de navegación robusta, segura y preparada para la web.
* **Negativas:** Requiere migrar la mentalidad de "Push/Pop" imperativo a una gestión de estado de rutas declarativa.