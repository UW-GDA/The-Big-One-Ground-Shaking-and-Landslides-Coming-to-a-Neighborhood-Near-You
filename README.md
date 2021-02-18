# Examining A Global Model for Rapid Assessment of Seismic Landslide Instability
**by: Ryan Rasanen & Brek Chiles, Winter 2021**
## Summary
The first part of the project will be computing a probability of landslide raster using widely available geospatial parameters and utilizing the USGS ground motions from the 2001 Nisqually earthquake.  The second part of our project consists of examining the probability of landslide results and determining: (1) how much of the Puget Lowland is at high risk of landslides for an earthquake similar to the Nisqually event, (2) calculating the areal percentage of each raster cell expected to have landslide occurrence, (3) analyze a major roadways shapefile and see which roadways intersect with high probability areas, (4) calculating a pseudo landslide susceptibility map for the Puget Lowland by assigning a constant PGV to the Nowicki et al. (2018) model
## Background
The Nowicki et al. (2018) model was created to offer near real time assessment of the probability of landslides following an earthquake event. The model can be used by emergency crews to determine the best routes and modes of transportation to reach communities impacted by landslides events. The model can also be useful in determining a general idea of areas at higher risk of landslides. The downside to this model is that you’re using geospatial information to determine landslide probability and do not realize the benefits of using actual geotechnical data. However, the use of global geospatial parameters allows the model to be used anywhere in the world (not limited to the areas where geotechnical information is available).

## Problem Statement & Objectives
With several known crustal faults and the looming Cascadia Subduction Zone, the Pacific Northwest (PNW) is known for its potential to have large earthquakes. The PNW is also prone to non-seismically induced landslides events, several of which have occurred in the past. The potential for large earthquakes combined with the highly susceptible landslide environment compounds the risk of landslides in the PNW. The Nowicki et al. (2018) model offers a offers a unique opportunity to explore landslide susceptibility and the potential effects of landslides in the PNW. The objectives of this research project are:
1. calculating how much of the Puget Lowland is at high risk of landslides given an earthquake event
2. calculating the areal percentage of each raster cell expected to have landslide occurrence given an earthquake event
3. generate a pseudo landslide susceptibility map of the PNW using a constant peak ground velocity (PGV) input to the Nowicki et al. (2018) model. To the authors knowledge, calculating landslide susceptibility has not been performed using the Nowicki et al. (2018) model.
4. analyze which major roadways have the highest susceptibility to landslides and are most likely to experience a landslide during a given earthquake event.

## Datasets
Elevation data (GMTED2010) to compute slope
*	https://topotools.cr.usgs.gov/gmted_viewer/viewer.htm
PGV data depends on earthquake event chosen
*	Link to chosen earthquake events shakemap
Lithology data (GLIM – Global Lithological Map Database)
*	https://www.geo.uni-hamburg.de/de/geologie/forschung/geochemie/glim.html
Landcover data (GlobCover 2009 dataset)
*	World Land Cover ESA 2009 (Mature Support) (arcgis.com)
Compound Topographic Index (CTI) HDMA database
*	https://www.sciencebase.gov/catalog/item/591b53bae4b0a7fdb43c8d1d

## Tools & Packages
1. Rasterio
   -https://rasterio.readthedocs.io/en/latest/api/rasterio.html
2. Numpy
   -https://numpy.org/
3. Pandas
   -https://pandas.pydata.org/
4. GeoPandas
   -https://geopandas.org/
5. Shapely
   -https://pypi.org/project/Shapely/
6. Fiona
   -https://pypi.org/project/Fiona/

## Planned Methodology
The anticipated steps for this project include:
1. Download and obtain the five rasters needed to compute the probability of landslides
   - If the raster is not available convert the feature or shapefile to a raster
2. Load each of the 5 rasters into python
3. Project each of the rasters into the desired crs (e.g., if Nisqually EQ then UTM Zone 10N)
4. Compute the probability of landslide raster from the five input rasters and model coefficients over the extent of the input ground motion raster in python
5. Create subplots of each input raster and the computed probability of landslide raster in python
6. Compute the landslide susceptibility by rerunning the model with a constant PGV input
7. Study the impacts of the probability of landslides to a given earthquake event and the landslide susceptibility to answer project objectives

## Expected Outcomes
1. Identification of areas of high and low probability of landslide for a given earthquake event
2. Creation of a landslide susceptibility map of the PNW
3. Identification of major road networks that are most likely to be impacted by landslides

## Other Relevant Information
N/A yet

## References
Nowicki Jessee, M. A., Hamburger, M. W., Allstadt, K., Wald, D. J., Robeson, S. M., Tanyas, H., et al. (2018). A global empirical model for near-real-time assessment of seismically induced landslides. Journal of Geophysical Research: Earth Surface, 123, 1835–1859. https://doi.org/10.1029/2017JF004494 \
Global multi-resolution terrain elevation data 2010 (GMTED2010); 2011; OFR; 2011-1073; Danielson, Jeffrey J.; Gesch, Dean B. \
Worden, C.B., E. M. Thompson, M. Hearne, and D.J. Wald (2020). ShakeMap Manual Online: technical manual, user’s guide, and software guide, U. S. Geological Survey. http://usgs.github.io/shakemap/. DOI: https://doi.org/10.5066/F7D21VPQ. \
Hartmann, Jörg; Moosdorf, Nils (2012): Global Lithological Map Database v1.0 (gridded to 0.5° spatial resolution). PANGAEA, https://doi.org/10.1594/PANGAEA.788537, Supplement to: Hartmann, Jens; Moosdorf, Nils (2012): The new global lithological map database GLiM: A representation of rock properties at the Earth surface. Geochemistry, Geophysics, Geosystems, 13, Q12004, https://doi.org/10.1029/2012GC004370 \
**Look in properties of downloaded raster file for globcover!**
Esri. "World Land Cover ESA 2009". Retrieved from https://www.arcgis.com/home/item.html?id=77864b7ae87a49e7984998e63d768c77  (February 16, 2021). \
Verdin, K.L., 2017, Hydrologic Derivatives for Modeling and Applications (HDMA) database: U.S. Geological Survey data release, https://doi.org/10.5066/F7S180ZP. \

