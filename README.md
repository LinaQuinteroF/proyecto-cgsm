# Pipeline multilenguaje (Python, R, Julia) para el monitoreo de manglar en la CGSM (2013-2025)

Proyecto final - Programacion en SIG: Python, R y Julia
Maestria en Geomatica, Universidad Nacional de Colombia
Docente: Alexys H. Rodriguez-Avellaneda PhD.
Estudiante: Lina Maria Quintero Fonseca - Marzo 2026

## Descripcion

Pipeline GeoAI multilenguaje para el monitoreo de la dinamica espaciotemporal de la cobertura de manglar en la Cienaga Grande de Santa Marta (CGSM), Colombia.

## Resultados principales

- Serie temporal 2013-2025 (929 registros): Landsat 8 + Sentinel-2
- Quiebre estructural en 2016 detectado por bfast en 7/8 estaciones (El Nino 2015-2016)
- 18 anomalias NDVI significativas (z < -2), septiembre 2020 como evento mas severo
- Recuperacion del manglar: de 4.938 ha (2020) a 8.444 ha (2024-2025), +76 km2 cambio neto
- Inundacion SAR: 1.507 km2 afectados en sept-oct 2020 (29.7% del AOI)
- Validacion contra GMW v4.0: F1=0.442, OA=0.899
- Dashboard interactivo con 15 capas tematicas

## Notebooks

- 01_gee_acquisition.ipynb - Fase 1: datacube S2 + Landsat
- 02_time_series.ipynb - Fase 2: z-scores (Python)
- 02b_bfast_ndvi.R.ipynb - Fase 2: bfast (R)
- 03_segmentation.ipynb - Fase 3: SamGeo + validacion GMW
- 04_fragmentation.ipynb - Fase 4: metricas (Julia)
- 05_flooding_nasa.ipynb - Validacion NASA SAR + GFD + JRC
- 06_dashboard.ipynb - Fase 5: dashboard interactivo

## Requisitos

Docker: alexyshr/sig_unal:v1.11
Python: earthengine-api geemap segment-geospatial leafmap rasterio geopandas
R: bfast terra sf ggplot2
Julia: GeoJSON DataFrames CSV Statistics
GEE: earthengine authenticate --auth_mode=notebook

## Como reproducir

1. git clone https://github.com/LinaQuinteroF/proyecto-cgsm.git
2. Iniciar contenedor Docker
3. Autenticar GEE
4. Ejecutar notebooks en orden (01 a 06)
5. Resultados en outputs/

## Fuentes de datos

Sentinel-2 L2A: COPERNICUS/S2_SR_HARMONIZED
Landsat 8 C2 L2: LANDSAT/LC08/C02/T1_L2
Sentinel-1 SAR: COPERNICUS/S1_GRD
Global Flood Database: GLOBAL_FLOOD_DB
JRC Surface Water: JRC/GSW1_4
GMW v4.0: sat-io/GMW/annual-extent
SRTM v3: USGS/SRTMGL1_003
INVEMAR: GBIF DOI 10.15472/0fqdp4

## Licencia

MIT
