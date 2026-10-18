# Reglas de Negocio para Detección de Ofertas Reales (`REGLAS_DETECCION`)

> Entregable oficial de **[API-F0-T1]**: Definición matemática de "oferta real", detección de trampas de marketing y parámetros del Score de Confianza en `api-sido`.

---

## 1. Las 8 Reglas del Motor de Detección

| # | Regla | Qué detecta | Fórmula / Lógica | Nota |
| :-: | :--- | :--- | :--- | :--- |
| **1** | **Precio de referencia real** | El "precio normal" verdadero, no el tachado de la tienda. | `mediana_90d` (últimos 90 días) y `minimo_180d` (últimos 180 días), excluyendo la ventana previa a eventos comerciales. | Sin historial suficiente → `"sin_veredicto"` (no notificar). |
| **2** | **Descuento real** | Cuánto bajó de verdad el precio respecto a su comportamiento histórico. | `descuento_real = (mediana_90d - precio_actual) / mediana_90d`<br>`descuento_anunciado = (precio_tachado - precio_actual) / precio_tachado`<br>`brecha = descuento_anunciado - descuento_real` | Una brecha grande indica que el precio tachado fue inflado. |
| **3** | **Alza previa al evento** | La tienda sube el precio días antes de Buen Fin, Hot Sale o Black Friday y luego lo "baja". | Si `precio_2_semanas_previas > mediana_90d * (1 + margen_inflado)`, la oferta se marca como **Falsa (Alza previa)**. | Requiere captura continua antes del evento. |
| **4** | **Tachado inexistente** | Precio "anterior" que nunca existió realmente en el historial. | `es_tachado_inflado = precio_tachado > mediana_90d * (1 + margen_tachado_inflado)` | Margen inicial: `10%` (`0.10`). |
| **5** | **Oferta permanente** | Productos que viven eternamente "en descuento". | Si el producto lleva más de $N$ días consecutivos con descuento anunciado, ese precio es su precio normal. | No notificar como oferta extraordinaria. |
| **6** | **Cercanía al mínimo histórico** | Qué tan cerca está hoy del mejor precio en 6 meses. | `cercania_minimo = (precio_actual - minimo_180d) / minimo_180d` | `0%` significa que igualó o mejoró el mínimo histórico. |
| **7** | **Competitividad multi-tienda** | Si otra tienda vende el mismo producto más barato sin "oferta". | Comparar `precio_actual` contra `mejor_precio_otra_tienda` del mismo `Product`. | Fase 3 (requiere emparejamiento de productos). |
| **8** | **Reputación del vendedor** | Confianza en quien vende el producto. | Semáforo separado del score de descuento (`VERIFIED_OFFICIAL`, `TRUSTED_SELLER`, `LOW_RATING_WARNING`). | No mezcla "oferta real" con "vendedor dudoso". |

---

## 2. Parámetros Calibrables Iniciales

| Parámetro | Clave en Código | Valor Inicial | Descripción |
| :--- | :--- | :---: | :--- |
| Ventana de mediana | `MEDIAN_WINDOW_DAYS` | `90` | Días de historial para calcular la mediana de referencia. |
| Ventana de mínimo | `MIN_WINDOW_DAYS` | `180` | Días de historial para obtener el mínimo histórico. |
| Descuento real mínimo | `MIN_REAL_DISCOUNT` | `0.15` (15%) | Por debajo de este porcentaje no se considera oferta. |
| Descuento real de referencia | `TARGET_REAL_DISCOUNT` | `0.30` (30%) | Descuento que obtiene el puntaje máximo (`1.0`). |
| Tolerancia al mínimo | `MIN_PRICE_TOLERANCE` | `0.05` (5%) | Dentro de +5% del mínimo histórico obtiene puntaje `1.0`. |
| Margen para tachado inflado | `FAKE_STRIKETHROUGH_MARGIN` | `0.10` (10%) | Cuánto puede superar el tachado a la mediana antes de marcarse inflado. |
| Peso: Descuento real | `WEIGHT_REAL_DISCOUNT` | `0.40` (40%) | Peso en el Score Final. |
| Peso: Cercanía al mínimo | `WEIGHT_MIN_PROXIMITY` | `0.40` (40%) | Peso en el Score Final. |
| Peso: Competitividad | `WEIGHT_COMPETITIVENESS` | `0.20` (20%) | Peso en el Score Final (suma de pesos = `1.00`). |
| **Umbral de notificación** | `NOTIFICATION_THRESHOLD` | **`0.70`** | Score mínimo requerido para disparar alerta. |
