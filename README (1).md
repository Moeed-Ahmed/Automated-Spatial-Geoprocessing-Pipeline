# GIE-471 GIS Programming - Open Ended Lab
## Automated Spatial Geoprocessing Pipeline
Study Area: Vehari District, Punjab, Pakistan
Data: HLS Sentinel-2 (HLSS30 VI v2.0) - March 2021 & March 2023
Source: NASA AppEEARS

## Pipeline Steps
1. Mount Google Drive & configure paths
2. Inventory HLS raster files (NDVI, SAVI, EVI)
3. Inspect raster metadata (CRS, dtype, scale factor, nodata)
4. Confirm scale factor: int16 x 0.0001 -> float [-1, 1]
5. Mosaic tiles per index per year with CRS harmonization to EPSG:32642
6. Save 6 GeoTIFF mosaics (3 indices x 2 years)
7. Load & reproject district boundary shapefile to EPSG:32642
8. Clip rasters to Vehari district boundary
9. Compute change rasters (2023 minus 2021) for all three indices
10. Run zonal statistics (mean, min, max, std, count)
11. Export enriched GeoJSON + Shapefile + CSV
12. Generate analytical maps (individual + comparison chart)
13. Package outputs for GitHub

## CRS
All rasters: EPSG:32642 (WGS84 / UTM Zone 42N)
Vector output: EPSG:4326 (GeoJSON) + EPSG:32642 (Shapefile)

## Scale Factor
HLS VI product stores indices as int16.
Applied: value x 0.0001 | Nodata: -28672

## References
- NASA AppEEARS: https://appeears.earthdatacloud.nasa.gov/
- HLS V2.0 User Guide: https://lpdaac.usgs.gov/documents/1326/HLS_User_Guide_V2.pdf
- Rouse et al. (1974) - NDVI
- Huete (1988) - SAVI
- Huete et al. (2002) - EVI
- GADM v4.1: https://gadm.org
- rasterstats: https://pythonhosted.org/rasterstats/
