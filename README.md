# The Big One - Ground Shaking & Landslides Coming to a Neighborhood Near You
**by: Ryan Rasanen & Brek Chiles, Winter 2021**

## Summary
The first part of the project will be computing a probability of landslide raster using widely available geospatial parameters and utilizing simulated ground motions for a Cascadia Subduction Zone (CSZ) earthquake.  The second part of our project consists of examining the probability of landslide results and determining: (1) how much of the Puget Lowland is at high risk of landslides for a CSZ earthquake, (2) calculating the areal percentage of each raster cell expected to have landslide occurrence, (3) calculating a pseudo landslide susceptibility map for the Puget Lowland by assigning a constant PGV to the Nowicki et al. (2018) model, and (4) developing an emergency response scenario where a major roadways shapefile is analyzed to see which roadways intersect with high probability areas.

## Background
The Nowicki et al. (2018) model was created to offer near real time assessment of the probability of landslides following an earthquake event. The model can be used by emergency crews to determine the best routes and modes of transportation to reach communities impacted by landslides events. The model can also be useful in determining a general idea of areas at higher risk of landslides. The downside to this model is that you’re using geospatial information to determine landslide probability and do not realize the benefits of using actual geotechnical data. However, the use of global geospatial parameters allows the model to be used anywhere in the world (not limited to the areas where geotechnical information is available).

## Problem Statement & Objectives
With several known crustal faults and the looming Cascadia Subduction Zone, the Pacific Northwest (PNW) is known for its potential to have large earthquakes. The PNW is also prone to non-seismically induced landslides events, several of which have occurred in the past. The potential for large earthquakes combined with the highly susceptible landslide environment compounds the risk of landslides in the PNW. The Nowicki et al. (2018) model offers a unique opportunity to explore pseudo landslide susceptibility and the potential effects of landslides in the PNW. The objectives of this research project are:
1. Calculating how much of the Puget Lowland is at high and low risk of landslides given an earthquake event
2. Calculating the areal percentage of each raster cell expected to have landslide occurrence given an earthquake event
3. Generate a pseudo landslide susceptibility map of the PNW using a constant peak ground velocity (PGV) input to the Nowicki et al. (2018) model. To the authors knowledge, calculating landslide susceptibility has not been performed using the Nowicki et al. (2018) model.
4. Perform an emergency response scenario where a major roadways shapefile is analyzed to see which roadways intersect with high probability areas in order to direct emergency crews to an impacted community.

## Datasets
1. Elevation data (GMTED2010) to compute slope
   - https://topotools.cr.usgs.gov/gmted_viewer/viewer.htm
2. PGV data depends on earthquake event chosen
   - https://www.designsafe-ci.org/data/browser/public/designsafe.storage.published//PRJ-1355/Frankel_etal_Production/csz010
3. Lithology data (GLIM – Global Lithological Map Database)
   - https://www.geo.uni-hamburg.de/de/geologie/forschung/geochemie/glim.html
4. Landcover data (GlobCover 2009 dataset)
   - https://www.arcgis.com/home/item.html?id=77864b7ae87a49e7984998e63d768c77
5. Compound Topographic Index (CTI) HDMA database
   - https://www.sciencebase.gov/catalog/item/591b53bae4b0a7fdb43c8d1d
6. Washington State Highway Data from WSDOT
   - https://www.wsdot.wa.gov/mapsdata/geodatacatalog/maps/NOSCALE/dot_TDO/LRS/500KLRS_2019.zip

## Tools & Packages
1. Rasterio
   - https://rasterio.readthedocs.io/en/latest/api/rasterio.html
2. Numpy
   - https://numpy.org/
3. Pandas
   - https://pandas.pydata.org/
4. GeoPandas
   - https://geopandas.org/
5. Shapely
   - https://pypi.org/project/Shapely/
6. Fiona
   - https://pypi.org/project/Fiona/
7. GDAL
   - https://gdal.org/

## Planned Methodology
The anticipated steps for this project include:
1. Download and obtain the five rasters needed to compute the probability of landslides
   - If the raster is not available convert the feature or shapefile to a raster
2. Load each of the 5 rasters into python
3. Use gdalwarp to project, trim, and resample each of the input rasters
4. Compute the probability of landslide raster from the five input rasters and model coefficients in python
5. Create subplots of each input raster and the computed probability of landslide raster in python
6. Compute the landslide susceptibility by rerunning the model with a constant PGV input
7. Study the impacts of the probability of landslides to a given earthquake event and the pseudo landslide susceptibility to answer project objectives

## Expected Outcomes
1. Identification of areas of high and low probability of landslide for a given earthquake event
2. Calculation of areal coverage of landsliding expected in a given grid cell
3. Creation of a pseudo landslide susceptibility map of the NW portion of Washington State
4. Demonstrated model applicability for use in emergency response scenarios

## Conclusions, Results and Lessons Learned
The Nowicki et al. (2018) model rapidly produces a probability of landslide map following an earthquake event. The model is useful for identifying areas of high and low probability of landslide for a given earthquake event, but values within any specific pixel should not be considered accurate. The model can also be used to help aid agencies evaluate response strategies and be used for loss estimation following earthquake events. The limitations of the model are that it uses geospatial information to determine landslide probability and does not realize the benefits of using actual geotechnical data. However, global geospatial parameters allow the model to be used anywhere in the world (not limited to the areas where geotechnical information is available).

The Nowicki et al. (2018) model was used to calculate the probability of landslide for a Cascadia Subduction Zone scenario earthquake in the NW portion of Washington State and analyze the results. Probability of landslide thresholds were created to mark areas of high and low risk to landslides. Results indicate there is more area at low risk of landslides than high risk within the Puget Lowland. However, the Olympic Peninsula, Tacoma, and Seattle areas will likely to have landslides according to the model. Because the Nowicki et al. (2018) model tends to spatially overpredict the probability of landslides the authors introduced a modification factor to represent "the actual probability of a landslide occurring," but provide few details/explanation about it. The USGS does not use the modification factor and instead applies a couple of reasonable modifications to make the model more physically sound (e.g., the probability of landslide = 0 when the slope is < 5 degrees).

By introducing a constant PGV input into the model a pseudo landslide susceptibility map (still in the form of landslide probability) was produced. The latter allowed examination of factors other than PGV that influence the probability of landslide. As expected, landslide probability is heavily influenced by slope while lithology, landcover, and cti play a smaller role. 

The model was also applied for an emergency response scenario for La Push, Washington using the Cascadia Subduction Zone scenario earthquake. The emergency response scenario highlighted the two main routes to La Push, Washington which were evaluated for probability of landslide. Zonal stats on the probability of landslide were used to determine which route was less likely to be impacted by landslides following the earthquake. The route traveling west from Olympia and then north once nearing the ocean was selected. The latter emergency response scenario shows the models applicability for use in aiding emergency response agencies to reach impacted communities following future earthquakes.

## Future Work
As more seismically induced landslides occur an updated model should be developed with new regression coefficients. The lithology and landcover regression coefficients in the current model are not physically sound likely due to the lack of landslides occurring in certain lithologies and landcovers. For example, the lithology unconsolidated sediments has a regression coefficient value of -3.22. The more negative the lithology regression coefficient is the lower the probability of landslide (the stronger the rock). Therefore, unconsolidated sediments, which represent a weak material, currently produces the lowest probability of landslide when it should be on the opposite end of the spectrum. For all facets of the model, as more seismically induced landslides occur the model should become more accurate (assuming the model is updated).

A new geospatial model to predict probability of landslide should include additional parameters that could be used as a proxy for of wetness. Currently compound topographic index is used, but, for how big of factor water plays in landslides, cti has a minor influence in the probability of landslide calculation. There is opportunity to add additional geospatial parameters that can better predict wetness in the ground. 

There is an opportunity for researchers to apply machine learning to correlate geospatial parameters to geotechnical (underground) parameters in order to better predict landslide probability.

## Other Relevant Information
* University of Washington news article showing 50 simulations for a M9 Cascadia earthquake
   * https://www.washington.edu/news/2017/10/23/50-simulations-of-the-really-big-one-show-how-a-9-0-cascadia-earthquake-could-play-out/ 
   
* Check out the Washington DNR's Geologic Information Portal to see Cascadia earthquake scenarios and mapped landslides
  * https://geologyportal.dnr.wa.gov/2d-view#wigm?-13814363,-13319051,5858815,6155391?Landslides,Earthquakes,Earthquake,Ground_Response,Cascadia_Seismic_Scenario 

* An article by the New Yorker responses by the Seattle Times
  * https://www.newyorker.com/magazine/2015/07/20/the-really-big-one
  * https://www.seattletimes.com/seattle-news/science/the-really-big-one-get-ready-now-quake-experts-advise/
  * https://www.seattletimes.com/seattle-news/environment/if-you-think-new-yorkers-earthquake-story-is-scary-better-read-this/
  
* An article by the Seattle Times that discusses the 1700 Cascadia earthquake
  * https://www.seattletimes.com/seattle-news/northwest/on-this-day-in-1700-the-really-big-one-a-magnitude-9-0-earthquake-hit-western-washington/#:~:text=Weather-,In%201700%2C%20the%20%27really%20big%20one%27%20%E2%80%94%20a%20magnitude,9.0%20earthquake%20%E2%80%94%20hit%20Western%20Washington&text=Called%20Cascadia%2C%20the%20magnitude%209.0,across%20the%20ocean%20to%20Japan. 

## References
Nowicki Jessee, M. A., Hamburger, M. W., Allstadt, K., Wald, D. J., Robeson, S. M., Tanyas, H., et al. (2018). A global empirical model for near-real-time assessment of seismically induced landslides. Journal of Geophysical Research: Earth Surface, 123, 1835–1859. https://doi.org/10.1029/2017JF004494 

Global multi-resolution terrain elevation data 2010 (GMTED2010); 2011; OFR; 2011-1073; Danielson, Jeffrey J.; Gesch, Dean B. 

Worden, C.B., E. M. Thompson, M. Hearne, and D.J. Wald (2020). ShakeMap Manual Online: technical manual, user’s guide, and software guide, U. S. Geological Survey. http://usgs.github.io/shakemap/. DOI: https://doi.org/10.5066/F7D21VPQ. 

Hartmann, Jörg; Moosdorf, Nils (2012): Global Lithological Map Database v1.0 (gridded to 0.5° spatial resolution). PANGAEA, https://doi.org/10.1594/PANGAEA.788537, Supplement to: Hartmann, Jens; Moosdorf, Nils (2012): The new global lithological map database GLiM: A representation of rock properties at the Earth surface. Geochemistry, Geophysics, Geosystems, 13, Q12004, https://doi.org/10.1029/2012GC004370 

Esri. "World Land Cover ESA 2009". Retrieved from https://www.arcgis.com/home/item.html?id=77864b7ae87a49e7984998e63d768c77  (February 16, 2021). 

Verdin, K.L., 2017, Hydrologic Derivatives for Modeling and Applications (HDMA) database: U.S. Geological Survey data release, https://doi.org/10.5066/F7S180ZP.

