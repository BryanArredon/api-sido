# SIDO API (`api-sido`)

Backend del **Sistema Inteligente de Detección de Ofertas (SIDO v2.0)**.

## Propósito
- Capturar y almacenar el historial propio de precios por tienda (`PriceSnapshot`).
- Calcular precios de referencia reales (mediana de 90 días y mínimo de 180 días) y detectar trampas de marketing (alza previa a eventos, precio tachado inflado, oferta permanente).
- Enviar alertas de ofertas reales por Telegram y exponer la API REST (`/api/v1/`) para `app_sido`.

## Documentación del Proyecto
- [`docs/REGLAS_DETECCION.md`](./docs/REGLAS_DETECCION.md): Reglas matemáticas de detección y parámetros del Score de Confianza.
- [`ISSUES_API_SIDO.md`](./ISSUES_API_SIDO.md): Plan de trabajo, Issues y convención de ramas del repositorio.
