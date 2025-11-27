# ADR-023: Algoritmo de Hashing de Credenciales (Bcrypt)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
El almacenamiento de contraseñas de usuarios conlleva una responsabilidad crítica de seguridad. Almacenarlas en texto plano o con algoritmos de hash rápidos (MD5, SHA) las hace vulnerables a ataques de fuerza bruta y tablas Rainbow en caso de una filtración de la base de datos.

## 2. Decisión
Adoptar el algoritmo **Bcrypt** con un factor de trabajo (work factor) configurable.

## 3. Justificación
* **Lentitud Intencional:** Bcrypt está diseñado para ser computacionalmente costoso, lo que ralentiza exponencialmente los ataques de fuerza bruta masivos sin afectar perceptiblemente la experiencia de login de un usuario individual.
* **Salting Automático:** Incorpora una "sal" (salt) aleatoria única por registro, protegiendo contra ataques de tablas pre-calculadas (Rainbow Tables).
* **Estándar de Industria:** Es el algoritmo más probado y recomendado para hashing de contraseñas en el ecosistema Node.js.

## 4. Alternativas Consideradas
* **Argon2:** Evaluada como una opción superior teóricamente (ganadora de PHC), pero descartada en favor de Bcrypt por la mayor estabilidad y documentación disponible para la infraestructura actual.
* **SHA-256:** Descartada por ser diseñada para velocidad (verificación de firmas), lo cual es una desventaja crítica para almacenamiento de contraseñas.

## 5. Consecuencias
* **Positivas:** Máxima protección de la identidad del usuario. Cumplimiento de normativas básicas de seguridad de datos.
* **Negativas:** Consume ciclos de CPU significativos en el servidor durante picos de inicio de sesión concurrentes.