# Power Plant Catchment Area Service Model

**Country:** Ghana
**CRS:** EPSG:25000 - Leigon / Ghana Metre Grid
**Project file:** `Power_Plant_Catchment_Service_Model.qgz`

---

## Overview

This project models the service catchment area of each power plant in Ghana using Voronoi tessellation. Each Voronoi zone represents the geographic area that is spatially closest to a given power plant, providing an approximate service territory model. Solar stations within each Voronoi zone are tagged to characterise the energy mix within each plant's catchment, supporting planning for hybrid and distributed energy integration.

---

## Objectives

- Generate Voronoi polygons from power plant point locations to define service catchment territories.
- Clip Voronoi polygons to the Ghana national boundary.
- Tag solar stations by the power plant Voronoi zone they fall within.
- Summarise the energy mix (conventional plant vs solar) within each catchment zone.

## Methodology

1. Power plant point features reprojected to EPSG:25000: `power_plants.gpkg`.
2. Voronoi tessellation generated from power plant locations and clipped to the Ghana boundary: `power_plant_voronoi_zones.gpkg`.
3. Ghana national boundary and administrative regions loaded as reference context: `ghana_boundary.gpkg`, `admin_regions.gpkg`.
4. Solar stations reprojected and spatially joined to Voronoi zones: `solar_stations_tagged.gpkg`.
5. Energy mix (plant type vs solar presence) summarised per zone.

## Output Layers

| File | Description |
|------|-------------|
| `power_plants.gpkg` | Power plant locations reprojected to EPSG:25000 |
| `power_plant_voronoi_zones.gpkg` | Voronoi polygons representing each plant's service territory |
| `ghana_boundary.gpkg` | National boundary used to clip Voronoi polygons |
| `admin_regions.gpkg` | Administrative region boundaries for regional context |
| `solar_stations.gpkg` | Solar station locations (input layer) |
| `solar_stations_tagged.gpkg` | Solar stations tagged with the Voronoi zone they fall within |

## Key Findings

- Voronoi zones for southern power plants are compact due to the density of generation assets near load centres, while northern zones are expansive, reflecting sparse plant coverage.
- Several Voronoi zones in the north contain multiple solar stations, indicating that solar is already the de facto generation source within those territories.
- The model highlights regions where no conventional power plant has a dominant catchment presence, pointing to areas where distributed generation investment is structurally justified.

## Deliverables

| File | Type |
|------|------|
| `Power_Plant_Catchment_Service_Model.qgz` | QGIS project |

## Notes

- No `reference_layout.png` or PDF export is present in this folder.
- All layers use EPSG:25000 (Leigon / Ghana Metre Grid).
- Voronoi-based catchment modelling is a proximity approximation; actual grid service territories depend on transmission routing and distribution infrastructure.
