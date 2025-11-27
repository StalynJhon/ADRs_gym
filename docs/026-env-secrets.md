# ADR-026: Gestión de Configuración y Secretos (.env)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación depende de credenciales sensibles (claves de API, cadenas de conexión a BD, secretos JWT) que varían entre entornos (Desarrollo, Test, Producción). Incluir estas credenciales en el código fuente (Hardcoding) viola principios de seguridad y dificulta el despliegue continuo.

## 2. Decisión
Implementar la carga de variables de entorno mediante archivos **.env** y la librería `dotenv` / `flutter_dotenv`.

## 3. Justificación
* **Metodología 12-Factor App:** Cumple con el principio de separación estricta entre configuración y código.
* **Seguridad:** Los archivos `.env` se excluyen del control de versiones (`.gitignore`), previniendo la exposición accidental de secretos en repositorios públicos.
* **Flexibilidad:** Permite cambiar el comportamiento de la aplicación (ej: apuntar a una BD distinta) simplemente modificando el entorno de ejecución, sin recompilar el código.

## 4. Alternativas Consideradas
* **Archivos de Configuración JSON/XML:** Descartada. A menudo terminan siendo versionados por error y no se integran nativamente con las variables de entorno del sistema operativo del servidor.
* **Servicios de Gestión de Secretos (Vault):** Descartada por ser una sobre-ingeniería para el tamaño actual del proyecto.

## 5. Consecuencias
* **Positivas:** Infraestructura segura y portable.
* **Negativas:** Requiere un proceso manual seguro para distribuir el archivo `.env` inicial a los nuevos desarrolladores del equipo.