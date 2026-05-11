# TP Final — Manejo y Visualización de Datos

Trabajo final de la materia Manejo y Visualización de Datos (UdeSA, 2026).

## Pregunta de investigación

Entre 1995 y 2016, ¿cómo se relacionó la dependencia comercial con China
con la disposición de los países a apoyar, rechazar o abstenerse en
resoluciones de derechos humanos en la Asamblea General de la ONU?

## Integrantes

- Sol Avalos
- Paloma Azuaga
- Clara Montalto
- Ines Paulucci

## Fuentes de datos

La ventana temporal del análisis (1995-2016) está determinada por la
intersección de las tres fuentes: el Atlas of Economic Complexity arranca
en 1995 y los datos de votaciones de la ONU vía `unvotes` llegan hasta
2015-2016.

- **Banco Mundial** — Indicadores macroeconómicos (PBI, PBI per cápita,
  población, exportaciones totales) vía API REST con `wbstats` 
- **UN Voting Data (Voeten et al.)** — Vía paquete `unvotes` de R.
  Trae tres tibbles: `un_votes` (votos), `un_roll_calls` (metadata y
  texto de las resoluciones) y `un_roll_call_issues` (clasificación
  temática, incluye "Human rights"). El texto del campo `descr` se usa
  además para el componente NLP.
- **Atlas of Economic Complexity (Harvard Growth Lab)** — Comercio
  bilateral entre todos los países, año por año. Descarga directa de
  `country_partner_hsproductsection_year.zip` desde el bucket S3
  público del Atlas. Usado para construir el índice de dependencia
  comercial con China.


## Estructura del repositorio

- `data/raw/` — datos crudos descargados. El contenido se ignora en
  `.gitignore` (los archivos pesan ~100 MB en total y son reproducibles
  vía `01_importacion.qmd`); solo se versiona la carpeta con un
  `.gitkeep`.
- `data/processed/` — dataset final ya limpio (`dataset_final.rds`).
- `qmd/` — notebooks de Quarto, uno por etapa (`.qmd` + `.html`
  renderizado).
- `.gitignore`, `README.md`, `TP-Final-MVD-Avalos-Azuaga-Montalto-Paulucci.Rproj`
  en la raíz.

## Cómo correr el código

1. Cloná el repo.
2. Abrí `tp-final-mvd.Rproj` en RStudio.
3. Instalá los paquetes necesarios:
```r
   install.packages(c(
     "tidyverse", "here", "httr2", "wbstats", "unvotes",
     "haven", "skimr", "naniar", "countrycode",
     "tidytext", "udpipe", "tidylo"
   ))
```
4. Corré los `.qmd` de la carpeta `qmd/` en orden numérico (`01` → `04`).

> Ninguna fuente requiere API key. El archivo `.Renviron` está
> preparado por si en el futuro se agregan fuentes autenticadas.
