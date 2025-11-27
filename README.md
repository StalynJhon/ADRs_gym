# SmartLife App - Documentación de Arquitectura de Software

**Proyecto:** SmartLife (Aplicación Móvil de Gimnasio y Bienestar)  
**Fecha de Entrega:** 26 de Noviembre, 2025  

## 👥 Equipo de Arquitectura
* **Jonathan Chisaguano** 
* **Jofre Bedón** 

---

## 🏛️ Introducción
Este repositorio centraliza el **Registro de Decisiones de Arquitectura (ADR)** para el proyecto SmartLife. El objetivo es documentar las elecciones técnicas críticas, justificando por qué se seleccionó cada tecnología o patrón frente a sus alternativas.

El sistema ha sido diseñado priorizando la **disponibilidad offline** (cache-first), la **experiencia de usuario fluida** (Flutter) y la **integridad de datos** (PostgreSQL), adaptándose a las restricciones de un equipo de dos desarrolladores para un MVP robusto.

## 📂 Índice de Decisiones (ADRs)

| ID | Título de la Decisión | Estado | Categoría |
|:---:|:---|:---:|:---|
| [ADR-001](./docs/001-arquitectura-monolita.md) | Arquitectura Monolítica Modular | ✅ Aceptado | Arquitectura |
| [ADR-002](./docs/002-backend-node.md) | Selección del Entorno Backend (Node.js) | ✅ Aceptado | Backend |
| [ADR-003](./docs/003-postgres.md) | Sistema de Gestión de Base de Datos (PostgreSQL) | ✅ Aceptado | Datos |
| [ADR-004](./docs/004-flutter.md) | Selección del Framework Móvil (Flutter) | ✅ Aceptado | Frontend |
| [ADR-005](./docs/005-auth-jwt.md) | Estrategia de Autenticación (JWT) | ✅ Aceptado | Seguridad |
| [ADR-006](./docs/006-api-rest.md) | Estilo de Arquitectura de API (RESTful) | ✅ Aceptado | API |
| [ADR-007](./docs/007-orm-sequelize.md) | Mapeo Objeto-Relacional (ORM) | ✅ Aceptado | Backend |
| [ADR-008](./docs/008-git-branching.md) | Estrategia de Ramas (Feature Branch) | ✅ Aceptado | DevOps |
| [ADR-009](./docs/009-swagger.md) | Documentación de API (OpenAPI/Swagger) | ✅ Aceptado | Documentación |
| [ADR-010](./docs/010-docker.md) | Contenedorización de Entorno (Docker) | ✅ Aceptado | DevOps |
| [ADR-011](./docs/011-repository-pattern.md) | Patrón de Diseño de Acceso a Datos | ✅ Aceptado | Patrones |
| [ADR-012](./docs/012-firebase-fcm.md) | Sistema de Notificaciones Externo (FCM) | ✅ Aceptado | Integración |
| [ADR-013](./docs/013-cron-jobs.md) | Recordatorios Automáticos (Cron Jobs) | ✅ Aceptado | Backend |
| [ADR-014](./docs/014-state-provider.md) | Gestión de Estado Global (Provider) | ✅ Aceptado | Frontend |
| [ADR-015](./docs/015-http-dio.md) | Cliente HTTP Móvil (Dio) | ✅ Aceptado | Frontend |
| [ADR-016](./docs/016-video-chewie.md) | Reproductor de Video (Chewie) | ✅ Aceptado | UX/UI |
| [ADR-017](./docs/017-shared-prefs.md) | Almacenamiento Local Ligero | ✅ Aceptado | Datos |
| [ADR-018](./docs/018-calendar-lib.md) | Librería de Calendario | ✅ Aceptado | Frontend |
| [ADR-019](./docs/019-gorouter.md) | Enrutamiento Declarativo (GoRouter) | ✅ Aceptado | Navegación |
| [ADR-020](./docs/020-form-builder.md) | Validación de Formularios | ✅ Aceptado | UX/UI |
| [ADR-021](./docs/021-cached-image.md) | Optimización de Imágenes (Cache) | ✅ Aceptado | Performance |
| [ADR-022](./docs/022-zod-validation.md) | Validación de Esquemas Backend (Zod) | ✅ Aceptado | Seguridad |
| [ADR-023](./docs/023-bcrypt.md) | Seguridad de Contraseñas (Bcrypt) | ✅ Aceptado | Seguridad |
| [ADR-024](./docs/024-logging.md) | Sistema de Logging (Winston/Morgan) | ✅ Aceptado | DevOps |
| [ADR-025](./docs/025-offline-first.md) | Estrategia Offline-First | ✅ Aceptado | Arquitectura |
| [ADR-026](./docs/026-env-secrets.md) | Gestión de Secretos (.env) | ✅ Aceptado | Seguridad |
| [ADR-027](./docs/027-ci-github.md) | Integración Continua (GitHub Actions) | ✅ Aceptado | DevOps |
| [ADR-028](./docs/028-app-bundle.md) | Formato de Distribución (App Bundle) | ✅ Aceptado | Despliegue |
| [ADR-029](./docs/029-error-boundary.md) | Manejo Global de Errores UI | ✅ Aceptado | Calidad |
| [ADR-030](./docs/030-json-store.md) | Estructura de Datos Nutrición (JSONB) | ✅ Aceptado | Datos |
| [ADR-031](./docs/031-image-compress.md) | Compresión de Imágenes en Cliente | ✅ Aceptado | Performance |
| [ADR-032](./docs/032-permissions.md) | Gestión de Permisos bajo Demanda | ✅ Aceptado | UX/Seguridad |
| [ADR-033](./docs/033-sync-conflicts.md) | Resolución de Conflictos (Last Write Wins)| ✅ Aceptado | Lógica |
| [ADR-034](./docs/034-linter.md) | Análisis Estático (Flutter Lints) | ✅ Aceptado | Calidad |
| [ADR-035](./docs/035-material3.md) | Sistema de Diseño (Material 3) | ✅ Aceptado | UX/UI |
| [ADR-036](./docs/036-google-fonts.md) | Tipografía (Google Fonts) | ✅ Aceptado | UX/UI |
| [ADR-037](./docs/037-intl.md) | Formateo de Fechas y Monedas (Intl) | ✅ Aceptado | i18n |
| [ADR-038](./docs/038-uuid.md) | Identificadores Únicos (UUID) | ✅ Aceptado | Datos |
| [ADR-039](./docs/039-tags-filter.md) | Filtrado por Tags en Memoria | ✅ Aceptado | Performance |
| [ADR-040](./docs/040-api-versioning.md) | Versionado de API (v1) | ✅ Aceptado | API |
| [ADR-041](./docs/041-inkwell-ripple.md) | Feedback Visual Táctil | ✅ Aceptado | UX/UI |
| [ADR-042](./docs/042-infinite-scroll.md) | Estrategia de Paginación | ✅ Aceptado | Performance |
| [ADR-043](./docs/043-launcher-icons.md) | Generación de Iconos Adaptativos | ✅ Aceptado | Herramientas |
| [ADR-044](./docs/044-unit-testing.md) | Testing Unitario de Lógica | ✅ Aceptado | Calidad |
| [ADR-045](./docs/045-token-expire.md) | Control de Expiración de Sesión | ✅ Aceptado | Seguridad |
| [ADR-046](./docs/046-accessibility.md) | Accesibilidad Semántica | ✅ Aceptado | Calidad |
| [ADR-047](./docs/047-snackbars.md) | Feedback de Usuario (Snackbars) | ✅ Aceptado | UX/UI |
| [ADR-048](./docs/048-implicit-anim.md) | Estrategia de Animaciones | ✅ Aceptado | UX/UI |
| [ADR-049](./docs/049-snake-case.md) | Nomenclatura de Archivos | ✅ Aceptado | Estándares |
| [ADR-050](./docs/050-pull-refresh.md) | Actualización Manual (Pull-to-Refresh) | ✅ Aceptado | UX/UI |

---