# Hugo Campground Site Screening

This ArcGIS Pro project uses proximity and overlay analysis to identify land near Hugo, Minnesota, that may warrant further review for public recreational use. The analysis first locates areas close to both roads and lakes, then compares those candidate areas with a supplied public-land layer to distinguish likely public-land opportunities from overlaps with mapped private land.

The project is a preliminary screening exercise designed to strengthen my GIS and spatial-analysis skills. It does not determine whether any location is legally available, buildable, or suitable for campground development.

## Project goals

- Identify land suitable for recreational campgrounds (within **300 meters of a road**, **100 meters of a lake**, and on **public land**).
- Calculate the total area meeting both proximity criteria.
- Compare the candidate areas with mapped public land.
- Present the analysis as a clear sequence of maps that explains how the final screening result was produced.

## Tools and methods

I completed the analysis in **ArcGIS Pro** using the following geoprocessing and cartographic techniques:

- Fixed-distance buffering
- Dissolving overlapping buffers
- Union overlay
- Attribute queries and feature selection
- Multipart-to-singlepart conversion
- Geometry calculation in hectares
- Erase analysis for the ownership comparison
- Layer symbology and map-layout design

## Analysis workflow

### 1. Create road and lake buffers

I created a **300-meter buffer around roads** to represent basic drive-in access and a **100-meter buffer around lakes** to represent proximity to water. The road buffers were dissolved into a single feature to remove overlapping boundaries and create a cleaner analysis layer. The lake buffers exclude the lake surfaces, so the analysis measures nearby land rather than water.

![Road and lake buffers in Hugo, Minnesota](images/road-and-lake-buffers.png)

### 2. Identify areas that meet both proximity criteria

I used a **Union** overlay to combine the road and lake buffer layers, then selected polygons classified as inside both buffers. This produced the initial campground candidate areas: land located within 300 meters of a road and 100 meters of a lake.

I converted the selected output from multipart to singlepart features so that each separate polygon had its own record. I then calculated each polygon's area in hectares and summarized the results.

![Campground candidate areas near roads and lakes](images/road-and-lake-candidates.png)

### 3. Review candidates by mapped ownership

Finally, I compared the candidate areas with the supplied public-land layer. An **Erase** operation isolated the portions outside the mapped public lands, allowing the final map to distinguish candidate areas that overlap public land from those that appear to fall on private land.

This step narrows the screening toward the project's main purpose: identifying preliminary opportunities for recreational use on public land. The ownership layer is appropriate for this analytical exercise, but it should not be treated as a current or authoritative record of title, access, or development rights.

![Candidate campground areas by mapped land ownership](images/candidates-by-ownership.png)

## Results

The proximity analysis identified **334.07 hectares** of land meeting both distance criteria before ownership was considered. These polygons represent the combined road-and-lake screening result, not 334.07 hectares of confirmed public or developable land.

The ownership comparison shows that many candidate polygons overlap the supplied public-land layer, while a smaller number include areas mapped as private. A separate total for the remaining public-land candidates was not calculated in the original analysis, so the final map should be interpreted as a visual ownership screening rather than a final site inventory.

## Interpretation and limitations

Proximity to roads and lakes provides a useful starting point, but it is not enough to establish campground suitability. A more complete site-selection analysis would also evaluate:

- Current ownership, legal access, and land-use permissions
- Parcel boundaries, zoning, and nearby development
- Terrain, slope, soils, and drainage
- Wetlands, flood risk, habitat, and other environmental constraints
- Utilities, road conditions, and emergency access
- Minimum usable area and campground design requirements

Some mapped candidates are narrow or fragmented and may not contain enough usable land for development. Before any planning decision, the ownership data should be verified and the remaining public-land area should be recalculated using current, authoritative sources.

## Data

The analysis uses `roads`, `Lakes`, and `Public_Hugo` layers supplied with the original ArcGIS Pro project. The source datasets and geodatabase are not included in this repository because their original provenance and redistribution permissions were not fully documented.

Basemap and map credits shown on the layouts include Metropolitan Council, MetroGIS, Esri, TomTom, Garmin, FAO, NOAA, USGS, EPA, NPS, and USFWS.

## Repository contents

```text
images/
  candidates-by-ownership.png
  road-and-lake-buffers.png
  road-and-lake-candidates.png
README.md
```

The repository contains the final map exports and project documentation. Reproducing the analysis requires authorized copies of the source layers and ArcGIS Pro.
