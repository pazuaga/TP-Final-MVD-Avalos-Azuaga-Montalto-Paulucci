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

- **UN Voting Data (Voeten et al.)** — Harvard Dataverse. Votos en la
  Asamblea General de la ONU desde 1946.
- **Banco Mundial** — Indicadores macroeconómicos (PBI, PBI per cápita,
  población, exportaciones totales) vía API REST con `wbstats` / `httr2`.
- **Atlas of Economic Complexity (Harvard Growth Lab)** — Comercio
  bilateral entre todos los países, año por año. Lo usamos para construir
  el índice de dependencia comercial con China.
- **UN General Debate Corpus** — Discursos anuales de cada país en la
  Asamblea General. Lo usamos para el componente NLP.

## Estructura del repositorio

- `data/raw/` — datos crudos descargados (no se sube al repo).
- `data/processed/` — dataset final ya limpio.
- `qmd/` — notebooks de Quarto, uno por etapa.
- `output/figures/` — gráficos exportados.

## Cómo correr el código

> Para esta primera entrega ninguna fuente requiere API key. El archivo
> `.Renviron` está preparado por si en el futuro se agregan fuentes
> autenticadas.