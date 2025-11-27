# ADR-038: Generación Descentralizada de Identificadores (UUID)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
En un sistema Offline-First, los clientes móviles crean entidades (Rutinas, Registros) desconectados del servidor. Utilizar IDs autoincrementales de base de datos (`1, 2, 3`) causaría colisiones inmediatas al intentar sincronizar datos de múltiples dispositivos (dos usuarios creando el registro #50).

## 2. Decisión
Utilizar **UUID v4 (Universally Unique Identifier)** generados en el cliente.

## 3. Justificación
* **Unicidad Global sin Coordinación:** Permite generar IDs definitivos en el dispositivo móvil sin necesidad de consultar una secuencia central en el servidor. La probabilidad de colisión es matemáticamente despreciable.
* **Integridad Referencial Offline:** Permite relacionar entidades (ej: crear una Rutina y sus Ejercicios hijos) localmente y mantener esas relaciones intactas al sincronizar con PostgreSQL.

## 4. Alternativas Consideradas
* **IDs Autoincrementales:** Descartada. Rompe el modelo offline, ya que el cliente tendría que esperar a tener conexión para obtener un ID válido.
* **IDs Temporales:** Descartada. Complejiza la arquitectura al tener que reemplazar IDs temporales por definitivos tras la sincronización.

## 5. Consecuencias
* **Positivas:** Independencia total del cliente para operaciones de escritura.
* **Negativas:** Mayor consumo de almacenamiento (128 bits vs 32/64 bits) y fragmentación de índices en la base de datos comparado con enteros secuenciales.