# `api-sido` — Plan de Issues y Ramas (Repositorio Backend Django)

Este documento contiene **exclusivamente los Issues y Ramas del repositorio `api-sido`** (Django 6 + DRF + Celery + Redis + PostgreSQL + Scrapers + Motor de Detección + Bot de Telegram).

---

## Tabla Resumen de Issues para el Repo `api-sido` (37 Issues)

| ID | Título del Issue en `api-sido` | Rama Git (`git checkout -b ...`) | Fase / Milestone | Etapa | Tam. | Depende de | Estado Actual |
| :--- | :--- | :--- | :--- | :---: | :---: | :---: | :--- |
| **API-F0-T1** | `[F0-T1] Definir reglas matemáticas de "oferta real" y parámetros del motor` | `docs/F0-T1-reglas-oferta-real` | Fase 0: Definición | MVP | S | — | **Listo para subir (100%)** |
| **API-F0-T2** | `[F0-T2] Elegir 2 tiendas iniciales y documentar método de acceso (API/Scraping)` | `docs/F0-T2-tiendas-iniciales` | Fase 0: Definición | MVP | S | — | Pendiente |
| **API-F0-T3** | `[F0-T3] Definir categorías iniciales y archivo semilla de productos` | `docs/F0-T3-catalogo-semilla` | Fase 0: Definición | MVP | S | — | Pendiente |
| **API-F1-T1** | `[F1-T1] Estructura Senior Django, settings por entorno, Docker Compose y CI` | `chore/F1-T1-setup-django-docker-ci` | Fase 1: Captura | MVP | M | F0-T3 | **Listo para subir (100%)** |
| **API-F1-T2** | `[F1-T2] Diseñar modelos ORM (Store, Product, Listing, PriceSnapshot, Offer, DetectionResult, Alert)` | `feat/F1-T2-modelos-dominio` | Fase 1: Captura | MVP | M | F1-T1 | Pendiente |
| **API-F1-T3** | `[F1-T3] Conector de Tienda 1 y persistencia transaccional de PriceSnapshot` | `feat/F1-T3-conector-tienda-1` | Fase 1: Captura | MVP | L | F1-T2 | Pendiente |
| **API-F1-T4** | `[F1-T4] Programar corridas diarias con Celery + Celery Beat + Redis y backoff exponencial` | `feat/F1-T4-celery-corridas-diarias` | Fase 1: Captura | MVP | M | F1-T3 | Pendiente |
| **API-F1-T5** | `[F1-T5] Desplegar captura continua en VPS Linux con Docker Compose` | `chore/F1-T5-deploy-vps-captura` | Fase 1: Captura | MVP | M | F1-T4 | Pendiente |
| **API-F1-T6** | `[F1-T6] Conector de Tienda 2 usando contrato común BaseStoreConnector` | `feat/F1-T6-conector-tienda-2` | Fase 1: Captura | MVP | M | F1-T3 | Pendiente |
| **API-F1-T7** | `[F1-T7] Pruebas de regresión de scrapers con fixtures HTML/JSON y alerta de caída (<90%)` | `test/F1-T7-regresion-scrapers` | Fase 1: Captura | MVP | M | F1-T6 | Pendiente |
| **API-F1-T8** | `[F1-T8] Configurar Django Admin para explorar productos, historial y gráficas simples` | `feat/F1-T8-django-admin-precios` | Fase 1: Captura | MVP | S | F1-T3 | Pendiente |
| **API-F2-T1** | `[F2-T1] Calcular precio de referencia real (mediana 90d y mínimo 180d sin ventanas de evento)` | `feat/F2-T1-precio-referencia` | Fase 2: Detección v1 | MVP | M | F1-T3, F0-T1 | Pendiente |
| **API-F2-T2** | `[F2-T2] Calcular descuento real vs descuento anunciado y brecha de inflación` | `feat/F2-T2-descuento-real-vs-anunciado` | Fase 2: Detección v1 | MVP | S | F2-T1 | Pendiente |
| **API-F2-T3** | `[F2-T3] Detector de patrones de trampa (alza previa, tachado falso, oferta permanente)` | `feat/F2-T3-detector-trampas` | Fase 2: Detección v1 | MVP | M | F2-T2 | Pendiente |
| **API-F2-T4** | `[F2-T4] Algoritmo de Score de Confianza ponderado y filtro por umbral (>= 0.70)` | `feat/F2-T4-score-confianza` | Fase 2: Detección v1 | MVP | M | F2-T3 | Pendiente |
| **API-F2-T5** | `[F2-T5] Etiquetado manual de ofertas (Real / Falsa) en Django Admin` | `feat/F2-T5-etiquetado-manual-admin` | Fase 2: Detección v1 | MVP | S | F2-T4 | Pendiente |
| **API-F2-T6** | `[F2-T6] Bot de alertas en Telegram para ofertas que superan el umbral` | `feat/F2-T6-alertas-telegram` | Fase 2: Detección v1 | MVP | S | F2-T4 | Pendiente |
| **API-F2-T7** | `[F2-T7] Medición de precisión (>85%), falsos positivos (<15%) y calibración de umbrales` | `feat/F2-T7-metricas-precision-umbrales` | Fase 2: Detección v1 | MVP | M | F2-T5 | Pendiente |
| **API-F3-T1** | `[F3-T1] Conectores de Tiendas 3 a 5 reutilizando BaseStoreConnector` | `feat/F3-T1-conectores-tiendas-3-a-5` | Fase 3: Comparación | v2 | L | F1-T7 | Pendiente |
| **API-F3-T2** | `[F3-T2] Manejo de anti-bot bajo demanda (Playwright, esperas aleatorias y rotación de IP)` | `feat/F3-T2-mitigacion-antibot` | Fase 3: Comparación | v2 | M | F3-T1 | Pendiente |
| **API-F3-T3** | `[F3-T3] Emparejamiento exacto de productos entre tiendas por código (GTIN/EAN/UPC)` | `feat/F3-T3-matching-gtin-exacto` | Fase 3: Comparación | v2 | M | F3-T1 | Pendiente |
| **API-F3-T4** | `[F3-T4] Emparejamiento difuso y por embeddings (rapidfuzz + sentence-transformers + pgvector)` | `feat/F3-T4-matching-fuzzy-embeddings` | Fase 3: Comparación | v2 | L | F3-T3 | Pendiente |
| **API-F3-T5** | `[F3-T5] Comparación entre tiendas e integración de competitividad en el Score` | `feat/F3-T5-competitividad-multitienda` | Fase 3: Comparación | v2 | M | F3-T4 | Pendiente |
| **API-F3-T6** | `[F3-T6] Cálculo de Precio Total Real (envío, MSI, cupones y vendedor)` | `feat/F3-T6-precio-total-real` | Fase 3: Comparación | v2 | M | F3-T5 | Pendiente |
| **API-F3-T7** | `[F3-T7] Factor de reputación del vendedor separado del descuento real` | `feat/F3-T7-reputacion-vendedor` | Fase 3: Comparación | v2 | S | F3-T5 | Pendiente |
| **API-F4-T1** | `[F4-T1] Endpoints API REST v1 de productos, historial, ofertas, auth JWT y Swagger` | `feat/F4-T1-api-rest-ofertas` | Fase 4: API | v2 | L | F2-T7 | **En progreso (Base 35%)** |
| **API-F4-T2** | `[F4-T2] Modelos y endpoints de preferencias de categoría, watchlist y umbral por usuario` | `feat/F4-T2-preferencias-watchlist-api` | Fase 4: API | v2 | M | F4-T1 | Pendiente |
| **API-F4-T3** | `[F4-T3] Servicio de envío de notificaciones Push con Firebase Admin SDK (FCM)` | `feat/F4-T3-fcm-push-backend` | Fase 4: API | v2 | M | F4-T2 | Pendiente |
| **API-F4-T6** | `[F4-T6] Endpoint de "Ofertas rechazadas y por qué" (/api/v1/deals/rejected/)` | `feat/F4-T6-endpoint-ofertas-rechazadas` | Fase 4: API | v2 | S | F4-T1 | Pendiente |
| **API-F5-T1** | `[F5-T1] Pruebas de integración backend E2E (Captura → Detección → Alerta → API)` | `test/F5-T1-pruebas-e2e-backend` | Fase 5: Calidad | v2 | M | F4-T1 | Pendiente |
| **API-F5-T2** | `[F5-T2] Monitoreo de errores y disponibilidad (Sentry SDK en Django/Celery + Uptime Kuma)` | `chore/F5-T2-monitoreo-sentry-uptime` | Fase 5: Calidad | v2 | M | F1-T5 | Pendiente |
| **API-F5-T3** | `[F5-T3] Respaldos automáticos de PostgreSQL (pg_dump) y endurecimiento de servidor` | `chore/F5-T3-backups-hardening` | Fase 5: Calidad | v2 | M | F1-T5 | Pendiente |
| **API-F5-T4** | `[F5-T4] Documentación de operación: cómo agregar tienda nueva y reparar scrapers` | `docs/F5-T4-runbook-scrapers` | Fase 5: Calidad | v2 | S | F5-T1 | Pendiente |
| **API-F6-T1** | `[F6-T1] API y modelos para registrar preferencias implícitas (búsquedas y clics)` | `feat/F6-T1-preferencias-implicitas-api` | Fase 6: Opcional | Opcional | M | F4-T2 | Pendiente |
| **API-F6-T2** | `[F6-T2] Motor de recomendaciones por contenido (sentence-transformers + pgvector)` | `feat/F6-T2-recomendacion-contenido` | Fase 6: Opcional | Opcional | M | F6-T1 | Pendiente |
| **API-F6-T3** | `[F6-T3] Motor de filtrado colaborativo (implicit / LightFM)` | `feat/F6-T3-filtrado-colaborativo` | Fase 6: Opcional | Opcional | L | F6-T1 | Pendiente |
| **API-F6-T4** | `[F6-T4] Detección de ciclos de recompra de consumibles y alertas programadas` | `feat/F6-T4-ciclos-recompra` | Fase 6: Opcional | Opcional | M | F6-T1 | Pendiente |
| **API-F6-T5** | `[F6-T5] Optimización para alto volumen (TimescaleDB hypertables + caché Redis)` | `perf/F6-T5-optimizacion-timescaledb` | Fase 6: Opcional | Opcional | M | F2-T7 | Pendiente |

---

## Criterios de Aceptación Detallados por Fase (`api-sido`)

### Fase 0: Definición (MVP)
- **`API-F0-T1` (`docs/F0-T1-reglas-oferta-real`)**:
  - [x] Documentar las 8 reglas de detección, pesos (`0.4 / 0.4 / 0.2`), umbral (`0.70`) y caso de prueba oficial en `docs/REGLAS_DETECCION.md`.
- **`API-F0-T2` (`docs/F0-T2-tiendas-iniciales`)**:
  - [ ] Documentar en `docs/TIENDAS_MVP.md` las 2 tiendas elegidas, endpoints/selectores y revisión de términos de uso.
- **`API-F0-T3` (`docs/F0-T3-catalogo-semilla`)**:
  - [ ] Crear fixture/semilla `apps/catalog/seeds/initial_products.json` con las categorías y productos iniciales.

### Fase 1: Base y Captura de Datos (MVP)
- **`API-F1-T1` (`chore/F1-T1-setup-django-docker-ci`) — LISTO PARA SUBIR**:
  - [x] Estructura `config/settings/` (`base.py`, `local.py`, `production.py`, `test.py`).
  - [x] Apps `apps/core` (`BaseModel`, `ApplicationError`, `custom_exception_handler`, `/api/v1/health/`, `DevCorsMiddleware`) y `apps/users`.
  - [x] `Dockerfile`, `docker-compose.yml` (PostgreSQL 16 + Redis 7 + API) y `.github/workflows/ci.yml`.
- **`API-F1-T2` (`feat/F1-T2-modelos-dominio`)**:
  - [ ] Crear apps `apps/catalog` (`Store`, `Category`, `Product`, `Listing`), `apps/pricing` (`PriceSnapshot`), `apps/deals` (`Offer`, `DetectionResult`) y `apps/alerts` (`Alert`).
  - [ ] Incluir en `PriceSnapshot`: precio actual, precio tachado, envío, vendedor, cupones, disponibilidad y timestamp indexado.
- **`API-F1-T3` (`feat/F1-T3-conector-tienda-1`)**:
  - [ ] Crear `BaseStoreConnector` y el conector de la Tienda 1 guardando `PriceSnapshot` en cada corrida.
- **`API-F1-T4` (`feat/F1-T4-celery-corridas-diarias`)**:
  - [ ] Configurar Celery + Celery Beat + Redis con reintentos (`retry_backoff=True`) y registro de éxitos/fallos por tienda.
- **`API-F1-T5` (`chore/F1-T5-deploy-vps-captura`)**:
  - [ ] Desplegar contenedores en VPS para captura ininterrumpida diaria.
- **`API-F1-T6` (`feat/F1-T6-conector-tienda-2`)**:
  - [ ] Implementar conector de Tienda 2 normalizado al mismo DTO de Tienda 1.
- **`API-F1-T7` (`test/F1-T7-regresion-scrapers`)**:
  - [ ] Guardar fixtures HTML/JSON reales y tests en `pytest` + alerta si la tasa de captura cae de `90%`.
- **`API-F1-T8` (`feat/F1-T8-django-admin-precios`)**:
  - [ ] Configurar `ModelAdmin` para explorar productos, snapshots e historial.

### Fase 2: Detección de Ofertas v1 (MVP)
- **`API-F2-T1` (`feat/F2-T1-precio-referencia`)**:
  - [ ] Calcular mediana de 90d y mínimo de 180d excluyendo ventanas pre-evento; marcar `"sin_veredicto"` si falta historial.
- **`API-F2-T2` (`feat/F2-T2-descuento-real-vs-anunciado`)**:
  - [ ] Calcular `descuento_real`, `descuento_anunciado` y `brecha`.
- **`API-F2-T3` (`feat/F2-T3-detector-trampas`)**:
  - [ ] Reglas: alza previa al evento, precio tachado inflado, oferta permanente y precio >= mínimo reciente.
- **`API-F2-T4` (`feat/F2-T4-score-confianza`)**:
  - [ ] Calcular `score` ponderado (`0.4 * desc_real + 0.4 * cercania_min + 0.2 * competitividad`) y filtrar por umbral `0.70`.
- **`API-F2-T5` (`feat/F2-T5-etiquetado-manual-admin`)**:
  - [ ] Acciones en Django Admin para etiquetar ofertas como reales o falsas.
- **`API-F2-T6` (`feat/F2-T6-alertas-telegram`)**:
  - [ ] Integrar bot de Telegram que envíe alertas con precio actual, referencia, ahorro real y link.
- **`API-F2-T7` (`feat/F2-T7-metricas-precision-umbrales`)**:
  - [ ] Script/comando de evaluación contra ofertas etiquetadas buscando precisión `> 85%`.

### Fase 3: Más Tiendas y Comparación (v2)
- **`API-F3-T1` a `API-F3-T7`**:
  - [ ] Conectores de tiendas 3 a 5 (`F3-T1`), anti-bot con Playwright (`F3-T2`), matching por GTIN (`F3-T3`), matching difuso/embeddings con `rapidfuzz` y `pgvector` (`F3-T4`), competitividad entre tiendas (`F3-T5`), precio total con envío/cupones (`F3-T6`) y reputación del vendedor (`F3-T7`).

### Fase 4: Endpoints API para la App (v2)
- **`API-F4-T1` (`feat/F4-T1-api-rest-ofertas`)**:
  - [ ] Endpoints de ofertas validadas, detalle de producto, serie de tiempo de precios y autenticación JWT.
- **`API-F4-T2` (`feat/F4-T2-preferencias-watchlist-api`)**:
  - [ ] Endpoints de categorías favoritas, lista de seguimiento (`watchlist`) y umbral por usuario.
- **`API-F4-T3` (`feat/F4-T3-fcm-push-backend`)**:
  - [ ] Registro de tokens FCM y disparo de notificaciones push desde Celery.
- **`API-F4-T6` (`feat/F4-T6-endpoint-ofertas-rechazadas`)**:
  - [ ] Endpoint `/api/v1/deals/rejected/` devolviendo ofertas descartadas y la regla de trampa que se activó.

### Fases 5 y 6: Calidad, Producción y Recomendaciones
- **`API-F5-T1` a `API-F5-T4`**: Pruebas E2E de backend, Sentry + Uptime Kuma, respaldos `pg_dump` y runbook de operación.
- **`API-F6-T1` a `API-F6-T5`**: Telemetría de clics/búsquedas, recomendador por embeddings, filtrado colaborativo, ciclos de consumibles y migración a TimescaleDB.
