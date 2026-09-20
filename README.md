# Hugo Campground Site Screening

An ArcGIS Pro workflow for screening areas near roads and lakes that may warrant further campground-site review near Hugo, Minnesota. This is a **screening exercise**, not a suitability or development decision.

## Purpose

I created this workflow to identify areas within **300 meters of a road** and **100 meters of a lake**, then review which preliminary areas overlap the supplied mapped ownership layer. The three maps show the progression from proximity inputs to candidate areas to an ownership overlay.

## Data and attribution

The analysis uses `Lakes`, `roads`, and `Public_Hugo` layers from the supplied ArcGIS Pro project. The source geodatabase and project package are not included because the original provenance and redistribution terms for these campground layers are not documented. Obtain authorized copies and confirm current permissions before reuse. The ownership result reflects only the supplied layer and is not current title or permission information.

Map credits identify Metropolitan Council, MetroGIS, Esri, TomTom, Garmin, FAO, NOAA, USGS, EPA, NPS, and USFWS; verify the applicable provider terms before reuse.

## Workflow and map sequence

### 1. Proximity inputs

![Road and lake buffer zones](images/road-and-lake-buffers.png)

I created 300-meter road buffers and 100-meter lake buffers, dissolving overlapping road buffers for a clearer analysis zone.

### 2. Candidate areas

![Road and lake candidate areas](images/road-and-lake-candidates.png)

I overlaid the buffers, retained areas meeting both distance criteria, converted multipart results to singlepart features, and calculated polygon area.

### 3. Ownership review

![Candidates by mapped ownership](images/candidates-by-ownership.png)

I used the supplied ownership layer to distinguish public-land candidates from candidates overlapping mapped private land. Red polygons show candidate overlap, not every private parcel.

## Findings

The proximity candidates total **334.07 hectares before ownership filtering**. This is mapped overlap area, not confirmed buildable, accessible, or suitable campground land. The source work did not recalculate a public-land total.

## Screening versus suitability

The workflow does not verify legal access, current ownership, permissions, zoning, terrain, flood exposure, environmental constraints, utilities, or usable campground area. Small or narrow polygons may be unsuitable. Further review should validate ownership and access, calculate remaining public-land area, and assess site constraints.

## Reproducibility

With authorized source layers, the workflow can be recreated in ArcGIS Pro using the stated buffers, dissolved road zones, overlay, multipart-to-singlepart processing, area calculation, and ownership selection/erase steps. Exact regeneration requires confirmed source-data provenance and permissions.

## Repository contents

- `images/road-and-lake-buffers.png`
- `images/road-and-lake-candidates.png`
- `images/candidates-by-ownership.png`
- `README.md`
