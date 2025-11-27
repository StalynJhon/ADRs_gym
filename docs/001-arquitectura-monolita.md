# ADR-001: Adopción de Arquitectura Monolítica Modular

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El sistema SmartLife se encuentra en su fase fundacional. El objetivo es lanzar un Producto Mínimo Viable (MVP) que integra gestión de usuarios, rutinas de ejercicio, módulos de nutrición y calendario. El equipo de desarrollo cuenta con dos integrantes y el tiempo de entrega es crítico. Se requiere una arquitectura que minimice la complejidad operativa inicial pero que no impida el crecimiento futuro.

## 2. Decisión
Se establece el uso de una **Arquitectura Monolítica Modular**.

## 3. Justificación
* **Eficiencia Operativa:** Al ser un equipo pequeño, gestionar múltiples despliegues (microservicios) introduciría una sobrecarga cognitiva y de infraestructura inmanejable ("Overhead").
* **Coherencia Transaccional:** Simplifica drásticamente el manejo de transacciones de base de datos y la integridad referencial entre usuarios y sus rutinas.
* **Modularidad Interna:** Al separar el código en módulos lógicos (Auth, Rutinas, Nutrición) dentro del mismo repositorio, mantenemos el código ordenado y listo para ser extraído a microservicios solo si la escalabilidad lo exige en el futuro.

## 4. Alternativas Consideradas
* **Arquitectura de Microservicios:** Descartada categóricamente para esta etapa. Requiere orquestación compleja (Kubernetes) y comunicación distribuida, triplicando el tiempo de desarrollo.
* **Arquitectura Serverless:** Descartada debido a la latencia de arranque en frío ("cold starts") y la dependencia de un proveedor específico ("Vendor Lock-in").

## 5. Consecuencias
* **Positivas:** Despliegue atómico, simplificación de pruebas y velocidad de desarrollo maximizada.
* **Negativas:** Riesgo de acoplamiento alto si no se mantienen límites estrictos entre módulos.