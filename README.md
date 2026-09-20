# Hugo Campground Site Screening

An ArcGIS Pro screening workflow for identifying areas near roads and lakes that may warrant further campground-site review near Hugo, Minnesota. The analysis is deliberately a **screening exercise**, not a suitability or development decision.

## Contents

- [Purpose and questions](#purpose-and-questions)
- [Data and source boundary](#data-and-source-boundary)
- [Workflow and map sequence](#workflow-and-map-sequence)
- [Findings](#findings)
- [Screening versus suitability](#screening-versus-suitability)
- [Limitations](#limitations)
- [Reproducibility and attribution](#reproducibility-and-attribution)
- [Repository contents](#repository-contents)

## Purpose and questions

The workflow asks: **Where do mapped road and lake proximity criteria overlap, and which of those preliminary areas overlap mapped private land?** It is intended to narrow a study area for later review, not to identify a confirmed campground site.

## Data and source boundary

The source work used mapped road, lake, and land-ownership layers in an ArcGIS Pro project near Hugo, Minnesota. The published repository contains the three exported maps and this explanation; it does not contain the original geodatabase or project package. The ownership result is limited to the supplied private-land layer and should not be treated as current title or permission information.

## Workflow and map sequence

### 1. Build proximity inputs

![Road and lake buffer zones](images/road-and-lake-buffers.png)

I created **300-meter road buffers** and **100-meter lake buffers**. Overlapping road buffers were dissolved to create a clearer analysis zone. This map shows the two inputs; it does not identify campground candidates yet.

### 2. Screen for areas meeting both criteria

![Road and lake candidate areas](images/road-and-lake-candidates.png)

I overlaid the buffers to isolate areas within **300 meters of a road and 100 meters of a lake**, converted multipart results to singlepart features, and calculated polygon area.

### 3. Review candidates by mapped ownership

![Candidates by mapped ownership](images/candidates-by-ownership.png)

I used the private-land layer to separate the candidate areas into a public-land selection and candidate areas overlapping private land. Public-land candidates are green; red shows only candidate areas overlapping private land, not every private parcel in the study area.

## Findings

The combined proximity candidates total **334.07 hectares before ownership filtering**. This is an area of mapped proximity overlap, not 334.07 hectares of confirmed buildable, accessible, or suitable campground land. The source work did not recalculate the public-land candidate area, so no public-land total is reported here.

## Screening versus suitability

The workflow does not verify legal or practical road access, current ownership, permissions, zoning, terrain, flood exposure, environmental constraints, utilities, or usable campground area. Small or narrow polygons may be unsuitable in practice. A next step would be to validate ownership and access, calculate the remaining public-land area, and assess additional site constraints.

## Limitations

Results depend on the dates, scale, definitions, and positional accuracy of the source layers. Distance thresholds are analytical choices rather than standards for campground development. The maps show candidate geometry and a mapped ownership overlay, not feasibility, environmental review, or a recommendation.

## Reproducibility and attribution

The methods can be reproduced in ArcGIS Pro with the source layers, the stated buffer distances, dissolved road buffers, overlay, multipart-to-singlepart processing, area calculation, and private-land erase/selection steps. The original geodatabase and ArcGIS project are not published, so exact regeneration is bounded by access to those source files. Map credits shown on the original layouts include Metropolitan Council, MetroGIS, Esri, TomTom, Garmin, FAO, NOAA, USGS, EPA, NPS, and USFWS. Verify current source terms before reuse.

## Repository contents

- `images/road-and-lake-buffers.png` — proximity inputs
- `images/road-and-lake-candidates.png` — combined proximity candidates
- `images/candidates-by-ownership.png` — ownership review
- `README.md` — methods, interpretation, and reuse boundary
