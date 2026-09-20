# Hugo Campground Site Screening

An ArcGIS Pro screening workflow for identifying areas near roads and lakes that may warrant further campground-site review near Hugo, Minnesota. The sequence moves from distance-based inputs to combined candidate areas and then to a mapped ownership review.

## Workflow

### 1. Build the road-and-lake buffers

![Road and lake buffer zones](images/road-and-lake-buffers.png)

I created **300-meter road buffers** and **100-meter lake buffers**. Overlapping road buffers were dissolved to create a clearer analysis zone. This first map shows the two proximity inputs; it does not identify campground candidates yet.

### 2. Screen for areas meeting both proximity criteria

![Road and lake candidate areas](images/road-and-lake-candidates.png)

I overlaid the buffers to isolate areas within **300 meters of a road and 100 meters of a lake**, then converted multipart results to singlepart features and calculated area. The combined proximity candidates total **334.07 hectares before ownership filtering**. This is a screening total for mapped proximity, not confirmed buildable or suitable campground land.

### 3. Review candidates by mapped ownership

![Candidates by mapped ownership](images/candidates-by-ownership.png)

I used the private-land layer to separate the candidate areas into a public-land selection and candidate areas overlapping private land. Public-land candidates are shown in green; candidate areas overlapping private land are shown in red. Red represents only candidate areas that overlap private land, not every private parcel in the study area. The source work did not recalculate the public-land candidate area.

## Screening versus suitability

This workflow narrows locations for further review; it does **not** determine that a site is suitable for a campground. It does not verify legal or practical road access, ownership, permissions, zoning, terrain, flood exposure, environmental constraints, utilities, or usable campground area. Small or narrow polygons may be unsuitable in practice. A next step would be to validate current ownership and access, calculate the remaining public-land area, and assess additional site constraints.

## Tools and sources

- **Software:** ArcGIS Pro
- **Techniques:** buffer, dissolve, overlay, erase, multipart-to-singlepart, and area calculation
- **Map credits shown on the original layouts:** Metropolitan Council; MetroGIS; Esri; TomTom; Garmin; FAO; NOAA; USGS; EPA; NPS; USFWS

The maps and description are based on the accompanying GIS report and project notes.
