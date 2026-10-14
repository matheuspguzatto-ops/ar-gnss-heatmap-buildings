# Blocos de prédios do AR GNSS Heatmap

Plantas e alturas de prédios em blocos de mapa, usados pelo app AR GNSS Heatmap para calcular a obstrução de satélites GNSS.

## Formato

- Um arquivo GeoJSON (EPSG:4326) por tile Web Mercator de zoom 16: `16/<x>/<y>.json`, com cerca de 540 m de lado.
- Cada feição é a planta de um prédio (`Polygon`). Ela traz o `id` do Overture Maps e a propriedade `height`, que é a altura acima do terreno, em metros.
- Prédios abaixo de 2 m são descartados.

## Regiões

| Região | Retângulo (oeste, sul, leste, norte) |
|---|---|
| São Sebastião e arredores, Palhoça (SC) | cerca de 6 × 6,6 km em torno de -27,64, -48,70 |
| Centro de Florianópolis (SC) | -48,566, -27,612, -48,533, -27,580 |

Os blocos são gerados com `scripts/build_building_blocks.py` do repositório do app.

## Fontes e licenças

Este conjunto é um banco de dados derivado das seguintes fontes:

- **Plantas:** [Overture Maps Foundation](https://overturemaps.org), tema `buildings`.
  - Feições derivadas do OpenStreetMap: © colaboradores do OpenStreetMap, sob a [Open Database License (ODbL) 1.0](https://opendatacommons.org/licenses/odbl/1-0/).
  - Demais feições: sob a [Community Data License Agreement – Permissive 2.0](https://cdla.dev/permissive-2-0/).
- **Alturas:** [Google Open Buildings 2.5D Temporal](https://sites.research.google/gr/open-buildings/temporal/), sob a [Creative Commons Attribution 4.0 (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Cada altura é o percentil 90 dos pixels do raster de 2023 que caem na planta.

Por conter dados derivados do OpenStreetMap, este banco é distribuído sob a **ODbL 1.0**, conforme o arquivo [LICENSE](LICENSE). Quem usar estes dados deve manter as atribuições acima.
