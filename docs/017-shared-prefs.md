# ADR-017: Persistencia de Datos Primitivos (SharedPreferences)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
La aplicación requiere persistir configuraciones de usuario ligeras y no relacionales (Banderas de estado, Tokens de sesión, Preferencias de tema) que deben sobrevivir al cierre del proceso de la aplicación. Usar una base de datos completa para estos datos simples introduciría una sobrecarga (overhead) innecesaria en operaciones de I/O.

## 2. Decisión
Utilizar **SharedPreferences** como mecanismo de almacenamiento clave-valor.

## 3. Justificación
* **Eficiencia en Recursos:** Interactúa directamente con los mecanismos nativos del sistema operativo (`NSUserDefaults` en iOS y `SharedPreferences` en Android) sin la sobrecarga de un motor SQL.
* **Acceso Asíncrono:** Permite lectura y escritura rápida sin bloquear el hilo principal (UI Thread), ideal para configuraciones que se cargan al iniciar la app (`SplashScreen`).
* **Simplicidad:** API directa para tipos de datos primitivos (`bool`, `int`, `String`), eliminando la necesidad de serialización compleja.

## 4. Alternativas Consideradas
* **SQLite (sqflite):** Descartada para este caso de uso específico. Configurar tablas, esquemas y conexiones SQL para guardar una variable booleana (`isFirstTime`) es un antipatrón de sobre-ingeniería.
* **Hive:** Evaluada positivamente por su velocidad, pero descartada para evitar añadir dependencias de compilación de código binario adicionales en esta etapa del MVP.

## 5. Consecuencias
* **Positivas:** Implementación inmediata y rendimiento óptimo para lectura de configuraciones.
* **Negativas:** No es adecuado para grandes volúmenes de datos. Los datos no están encriptados por defecto, por lo que no se debe usar para información sensible sin una capa de cifrado adicional.