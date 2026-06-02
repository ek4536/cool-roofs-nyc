# Urban Heat & Cool Roofs in NYC

**Team:** Eunji Kim, Gianna Campa, Nazira Cisse, Kelsey Knight

## Overview

Rooftops account for 20–25% of urban surface area and are among the largest drivers of the Urban Heat Island (UHI) effect. NYC has operated a cool roof program since 2009, but no systematic, data-driven framework exists for identifying which buildings should be prioritized.

This project closes that gap: characterizing Manhattan's rooftop landscape, measuring whether past cool roof installations have produced detectable temperature reductions, and developing an optimization framework for targeting future investments.

**Core finding:** The darkest rooftops are concentrated in Midtown and Lower Manhattan's commercial core — not in the most heat-vulnerable neighborhoods. This spatial mismatch between heat load and heat vulnerability is the central tension the optimization addresses.

## Methods

| Method | Purpose |
|---|---|
| PCA + K-Means Clustering | Classify buildings into roof typologies by optical characteristics |
| Time Series Analysis | Assess whether cool roof installations reduced land surface temperature over 2009–2024 |
| Optimization | Target highest-impact buildings for future installation under a fixed budget |

### Roof Typology Clustering
- Extracted per-building RGB brightness scores from 2024 Manhattan orthoimagery (158 tiles, ~40,000 buildings)
- Joined with PLUTO building attributes (17 features)
- Applied PCA (10 components, 85% variance explained), then K-Means (K=3) on RGB features only
- **3 clusters:** Bright (older low-rise residential, Upper Manhattan), Medium, Dark (commercial, Midtown/Lower Manhattan — 72% dark-roofed)

## Data Sources

| Dataset | Description |
|---|---|
| Manhattan Orthoimagery 2024 | 158 tiles, per-building RGB extraction |
| NYC PLUTO 2026 | Building footprint, land use, FAR |
| NYC CoolRoofs GIS Data | Program participation records |
| NASA MODIS LST | Land surface temperature 2009–2024 |

## Repository Structure

```
cool-roofs-nyc/
│
├── PCA_v2.ipynb           # PCA & K-Means roof typology clustering
├── Time Series.ipynb      # Land surface temperature trend analysis
└── Optimization_v2.ipynb  # Budget-constrained cool roof targeting
```

## Key Insight

Heat-vulnerable neighborhoods (Harlem, East Harlem, Washington Heights) have naturally lighter roofing materials and lower intervention urgency by reflectivity alone. The commercial core has the highest solar heat load per square foot but lower social vulnerability. An effective cool roof strategy must weigh both heat load and equity — prioritizing buildings that reduce temperatures in the neighborhoods that need it most.
