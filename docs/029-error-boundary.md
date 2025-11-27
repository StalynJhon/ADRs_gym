# ADR-029: Captura Global de Excepciones de UI (Error Boundary)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
En Flutter, una excepción no controlada durante la fase de construcción de widgets resulta en la temida "Pantalla Roja" (en debug) o una pantalla gris vacía (en release), rompiendo totalmente la experiencia de usuario y dando sensación de baja calidad.

## 2. Decisión
Implementar un **Custom Error Widget** global interceptando `FlutterError.onError` y `PlatformDispatcher`.

## 3. Justificación
* **Degradación Elegante:** Permite sustituir la pantalla gris de la muerte por una interfaz amigable ("Algo salió mal") que permite al usuario intentar recuperar la acción o volver al inicio, en lugar de bloquear la app.
* **Centralización:** Provee un punto único para capturar el stack trace del error y enviarlo al servicio de logging (definido en ADR-024), facilitando la depuración.
* **Resiliencia:** Evita que un error en un widget secundario (ej: un icono mal cargado) inutilice toda la pantalla.

## 4. Alternativas Consideradas
* **Try/Catch en cada Widget:** Descartada. Técnicamente inviable y resultaría en un código ilegible y sobrecargado.
* **Ignorar errores:** Descartada. Inaceptable para una aplicación de producción.

## 5. Consecuencias
* **Positivas:** Robustez percibida por el usuario y capacidad de diagnóstico remoto.
* **Negativas:** Puede ocultar errores visuales leves durante el desarrollo si no se configura para mostrar la alerta completa en modo debug.