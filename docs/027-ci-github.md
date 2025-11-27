# ADR-027: Integración Continua (GitHub Actions)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Con múltiples desarrolladores integrando código, el riesgo de introducir errores de compilación o regresiones lógicas es alto. Detectar estos errores manualmente en la máquina de cada desarrollador es ineficiente y propenso a olvidos.

## 2. Decisión
Establecer un pipeline de Integración Continua (CI) básico usando **GitHub Actions**.

## 3. Justificación
* **Automatización del Quality Gate:** Configuración de workflows que ejecutan automáticamente el linter (`flutter analyze`) y las pruebas unitarias en cada Pull Request.
* **Integración Nativa:** Al estar el código en GitHub, Actions ofrece una integración sin fricción, sin necesidad de configurar webhooks o servidores externos.
* **Feedback Temprano:** Notifica a los desarrolladores sobre errores inmediatamente después de subir código (Push), reduciendo el costo de corrección.

## 4. Alternativas Consideradas
* **Jenkins:** Descartada. Requiere aprovisionar, configurar y mantener un servidor dedicado, lo cual consume recursos valiosos del equipo.
* **GitLab CI:** Descartada dado que el repositorio principal se aloja en GitHub.

## 5. Consecuencias
* **Positivas:** Mantenimiento de la calidad del código y prevención de ramas rotas ("Broken builds").
* **Negativas:** Consumo de la cuota de minutos gratuitos de los Runners de GitHub (aunque suficiente para el alcance académico).