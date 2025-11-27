# ADR-007: Mapeo Objeto-Relacional (ORM Sequelize)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Interactuar con la base de datos mediante SQL crudo es inseguro y difícil de mantener.

## 2. Decisión
Utilizar el ORM **Sequelize**.

## 3. Justificación
Abstrae la complejidad de SQL, permitiendo manipular datos usando clases de JavaScript. Facilita las migraciones de esquema y validaciones.

## 4. Alternativas Consideradas
* **SQL Puro:** Descartado por riesgo de inyección SQL y lentitud de desarrollo.
* **Query Builders:** Descartado en favor de un ORM completo para acelerar el MVP.

## 5. Consecuencias
* **Positivas:** Desarrollo acelerado y código agnóstico al motor de BD.
* **Negativas:** Ligera pérdida de rendimiento en consultas muy complejas.