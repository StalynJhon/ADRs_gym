# ADR-006: Estilo de Arquitectura de API (RESTful)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Se debe definir el contrato de comunicación entre el móvil y el servidor. Se busca un estándar conocido y fácil de documentar.

## 2. Decisión
Diseñar la interfaz bajo el estándar **REST**.

## 3. Justificación
* **Madurez:** Es el protocolo universal de la web con herramientas robustas (Postman).
* **Cacheabilidad:** Permite el uso eficiente de caché HTTP.

## 4. Alternativas Consideradas
* **GraphQL:** Descartado para el MVP por añadir complejidad innecesaria en el backend y gestión de caché en el cliente.
* **gRPC:** Descartado por ser excesivamente complejo para una app pública.

## 5. Consecuencias
* **Positivas:** Simplicidad de implementación y depuración.
* **Negativas:** Posible "over-fetching" de datos en pantallas complejas.