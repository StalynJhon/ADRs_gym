# ADR-003: Sistema de Gestión de Base de Datos Relacional (PostgreSQL)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La naturaleza de los datos de SmartLife (Usuarios, Rutinas, Historial) es altamente relacional y estructurada. Se requiere integridad ACID para garantizar que no se pierdan registros de progreso.

## 2. Decisión
Implementar **PostgreSQL** como motor de base de datos principal.

## 3. Justificación
* **Robustez:** Es la base de datos Open Source más avanzada, con soporte nativo para JSON (útil para guardar configuraciones flexibles).
* **Integridad:** Garantiza mediante llaves foráneas que no existan datos huérfanos, vital para la consistencia del sistema.

## 4. Alternativas Consideradas
* **MongoDB (NoSQL):** Descartado porque la estructura de datos es predecible. Usar NoSQL complicaría las consultas de reportes relacionales.
* **MySQL:** Descartado en favor de PostgreSQL por su mejor manejo de concurrencia y tipos de datos avanzados.

## 5. Consecuencias
* **Positivas:** Garantía total de consistencia de datos y capacidad de consultas complejas.
* **Negativas:** Requiere definir esquemas estrictos (migraciones) para cambios en el modelo de datos.