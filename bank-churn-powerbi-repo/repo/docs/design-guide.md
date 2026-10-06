# Design guide

## Canvas
16:9, 1280x720. Background: `assets/dashboard_background_2560x1440.png` (Canvas background -> Image -> Fit, transparency 0%).

## Palette
| Role | Hex |
|---|---|
| Page / ink | #0F1B2E |
| Panel | #1D2D47 |
| Churned (coral) | #FF8A6B |
| Stayed (teal) | #1FA6B8 |
| Highlight | #FFD166 |
| Neutral / gridlines | #8FA3BF |
| Text | #E8EEF5 |

Sequential heatmap: teal #D6F1F5 -> #8ED3DE -> #1FA6B8 -> #0E6F80 -> #08414C; churn #FFE1D6 -> #FFB59E -> #FF8A6B -> #D9532F -> #8F2A12.

Rules: max 3 main colors per page; coral always = churn, teal always = retained; mute normal bars (#3A5073) and color only the one that matters; lines white or yellow; faint gridlines (white 8%).

## Layout (px) - set in Format -> General -> Properties
| Visual | X | Y | W | H |
|---|---|---|---|---|
| Title textbox | 24 | 20 | 680 | 80 |
| Customers KPI | 720 | 20 | 160 | 80 |
| Churn rate gauge | 896 | 20 | 160 | 80 |
| Churn status slicer | 1072 | 20 | 184 | 80 |
| Donuts 1-4 | 24 / 336 / 648 / 960 | 120 | 296 | 210 |
| Combo: Age | 24 | 350 | 400 | 346 |
| Combo: Credit score | 440 | 350 | 400 | 346 |
| Combo: Balance | 856 | 350 | 400 | 346 |

## Figma workflow
Import `assets/dashboard_background.svg` (or build a 1280x720 frame with radius-14 rounded rectangles), adjust panels, export PNG @2x.
