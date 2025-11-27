# ADR-004: Selección del Framework de Desarrollo Móvil (Flutter)

* **Estado:** Aceptado
* **Fecha:** 2025-10-25
* **Autores:** Jonathan Chisaguano, Jofre Bedón

## 1. Contexto
Se requiere desarrollar la aplicación cliente para Android e iOS. La UX debe ser fluida (60fps), especialmente en videos y calendario. El equipo necesita maximizar la reutilización de código.

## 2. Decisión
Utilizar **Flutter** (Dart) para el desarrollo de la aplicación.

## 3. Justificación
* **Compilación Nativa:** Flutter compila a código máquina ARM, garantizando rendimiento superior en animaciones.
* **Independencia de Plataforma:** Su motor de renderizado propio asegura que la UI se vea idéntica en todos los dispositivos.
* **Productividad:** El "Hot Reload" acelera drásticamente el ciclo de desarrollo.

## 4. Alternativas Consideradas
* **React Native:** Descartado debido a problemas de rendimiento en listas largas y animaciones complejas por el puente JS.
* **Nativo Puro (Kotlin/Swift):** Descartado por la inviabilidad de mantener dos bases de código con un equipo pequeño.

## 5. Consecuencias
* **Positivas:** Una única base de código y UI expresiva.
* **Negativas:** El tamaño del binario de la app es ligeramente mayor que una nativa pura.