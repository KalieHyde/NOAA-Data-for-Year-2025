# NOAA Data for Year 2025

# NOAA Storms Pipeline

A one-command pipeline that downloads a year of NOAA Storm Events data,
converts it to GeoJSON (and attempts GeoParquet), and lands it ready for 
analysis in DuckDB, GeoPandas, or QGIS.

## What it does

`pipeline.sh` takes a year (default: 2025), pulls the raw `details` file
from NOAA's public archive, decompresses it, and converts it to a GeoJSON
file at `data/processed/storms_{YEAR}.geojson`.

It also attempts to convert this to a GeoParquet file, though GeoJSON is 
used as the primary output for maximum reliability on Windows systems.

Total runtime: ~2 minutes for a typical year on a home internet connection.

## The data

- **Source:** NOAA Storm Events Database (https://www.ncei.noaa.gov/data/storm-events/)
- **License:** Public domain (US federal data)
- **What's in it:** every recorded storm event in the United States for the
  given year, including type, location, and damages

## How to run it

Requires GDAL (for `ogr2ogr`), `curl`, and `gunzip`.

```bash
git clone https://github.com/your-username/noaa-storms-pipeline.git
cd noaa-storms-pipeline
chmod +x pipeline.sh
./pipeline.sh
