# ADR-030: Almacenamiento de Datos Semi-Estructurados (JSONB)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El módulo de Nutrición incluye dietas y recetas cuya estructura es altamente variable y polimórfica (algunas tienen lista de ingredientes, otras pasos de preparación, otras solo info calórica). Modelar esto en un esquema relacional rígido (Tablas SQL) resultaría en una explosión de tablas pequeñas y Joins complejos.

## 2. Decisión
Utilizar el tipo de dato **JSONB** de PostgreSQL para almacenar el contenido detallado de las guías nutricionales.

## 3. Justificación
* **Flexibilidad de Esquema:** Permite evolucionar la estructura de las dietas (agregar nuevos campos) sin realizar migraciones de base de datos costosas ("Schemaless" dentro de SQL).
* **Rendimiento de Consulta:** A diferencia del texto plano, `JSONB` es un formato binario que permite indexación y consultas eficientes sobre campos internos del documento JSON directamente desde SQL.
* **Hibridación:** Combina lo mejor de dos mundos: integridad referencial relacional (Usuario <-> Dieta) con la flexibilidad documental (Contenido de la Dieta).

## 4. Alternativas Consideradas
* **Modelo EAV (Entity-Attribute-Value):** Descartada. Es un antipatrón conocido que degrada severamente el rendimiento y complica las consultas SQL.
* **Base de Datos NoSQL Separada (MongoDB):** Descartada para evitar la complejidad operativa de mantener dos motores de base de datos distintos (Polyglot Persistence) para este volumen de datos.

## 5. Consecuencias
* **Positivas:** Agilidad en el desarrollo de nuevas features de nutrición. Consultas rápidas.
* **Negativas:** Se pierde la validación de tipos estricta a nivel de base de datos para el contenido del JSON (la validación se delega al código de aplicación con Zod).