# TP Final — Manejo y Visualización de Datos

Trabajo final de la materia Manejo y Visualización de Datos (UdeSA, 2026).

## Pregunta de investigación

¿Los países con mayor dependencia económica de China tienen menos
probabilidad de condenar violaciones de DDHH en votaciones de la ONU?

## Integrantes

- Sol Avalos
- Paloma Azuaga
- Clara Montalto
- Ines Paulucci

## Fuentes de datos

- **Banco Mundial** — Indicadores macroeconómicos (PBI, PBI per cápita,
  población, exportaciones totales) vía API REST con `wbstats` / `httr2`.
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

- `data/raw/` — datos crudos descargados (no se sube al repo).
- `data/processed/` — dataset final ya limpio.
- `qmd/` — notebooks de Quarto, uno por etapa.
- `output/figures/` — gráficos exportados.

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
4. Corré los `.qmd` de la carpeta `qmd/` en orden numérico.

> Ninguna fuente requiere API key. El archivo `.Renviron` está
> preparado por si en el futuro se agregan fuentes autenticadas.
