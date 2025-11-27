# ADR-031: Estrategia de Compresión de Imágenes en Cliente

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Los usuarios generan contenido visual (fotos de perfil, evidencia de progreso) utilizando cámaras de dispositivos modernos que producen imágenes de alta resolución (>5MB). Transferir estos archivos "crudos" (RAW/Full JPEG) impacta negativamente en el ancho de banda del usuario, la latencia de subida y los costos de almacenamiento en la nube del backend.

## 2. Decisión
Implementar compresión y redimensionado en el cliente (Edge Compression) utilizando **flutter_image_compress**.

## 3. Justificación
* **Optimización de Ancho de Banda:** Reduce el tamaño del payload en un 90-95% antes de iniciar la transmisión de red, convirtiendo imágenes de 5MB en archivos JPEG de ~200KB sin pérdida visual perceptible en pantallas móviles.
* **Offloading de CPU:** Delega el procesamiento de imagen a la GPU/CPU del dispositivo del usuario, liberando al servidor backend de tareas computacionalmente costosas.
* **Experiencia de Usuario:** Acelera drásticamente el tiempo de subida, proporcionando feedback de "tarea completada" casi instantáneo.

## 4. Alternativas Consideradas
* **Compresión en Servidor:** Descartada. Obliga a transferir el archivo pesado primero, consumiendo datos innecesarios y creando cuellos de botella en la entrada del servidor.
* **Subida sin procesar:** Descartada por ser insostenible económicamente (storage) y técnicamente (timeouts de red).

## 5. Consecuencias
* **Positivas:** Eficiencia operativa y ahorro de costos de infraestructura.
* **Negativas:** Pérdida irreversible de la calidad original de la fotografía (Lossy Compression), aceptable para el contexto de la aplicación.