# ADR-022: Validación de Esquemas y Tipado en Runtime (Zod)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La API Backend recibe datos arbitrarios desde clientes móviles y web. Confiar ciegamente en la estructura de estos datos es una vulnerabilidad de seguridad. Se requiere una capa de validación estricta que garantice la integridad de los datos antes de que lleguen a la lógica de negocio o la base de datos.

## 2. Decisión
Utilizar la librería **Zod** para la definición y validación de esquemas.

## 3. Justificación
* **Validación en Tiempo de Ejecución:** A diferencia de las interfaces de TypeScript que desaparecen al compilar, Zod valida los datos reales entrantes (Runtime Validation), lanzando errores descriptivos si no cumplen el esquema.
* **Inferencia de Tipos:** Permite derivar los tipos estáticos de TypeScript directamente de los esquemas de validación, garantizando una única fuente de verdad (SSOT) y evitando discrepancias entre la validación y el tipado.
* **Composibilidad:** Facilita la creación de esquemas complejos reutilizando piezas más pequeñas (ej: esquema de `Address` reutilizado en `User` y `Gym`).

## 4. Alternativas Consideradas
* **Joi:** Descartada. Aunque madura, su integración con la inferencia de tipos de TypeScript es menos fluida y moderna que la de Zod.
* **Express-validator:** Descartada por su sintaxis basada en cadenas de middleware, que tiende a dispersar la lógica de validación dificultando su lectura centralizada.

## 5. Consecuencias
* **Positivas:** Seguridad por diseño ("Fail Fast"), código autodocumentado y eliminación de errores de tipo `undefined` en tiempo de ejecución.
* **Negativas:** Introduce una pequeña sobrecarga de procesamiento (CPU) al parsear cada petición, despreciable comparada con la seguridad ganada.