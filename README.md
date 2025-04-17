# California Current System: Upwelling Predictions





# Background
##### Increased carbon dioxide emissions has caused global atmospheric temperatures to rise, which has led to various climatic shifts. Some of these shifts include changes in weather patterns and rising sea-surface temperatures and are expected to get worse (Fig. 1). It is also expected that upwelling will increase in the future, which can result in more primary productivity due to upwelling bringing cold nutrient-rich waters to the surface (Fig. 2) [2, 3]. However, this primary productivity can result in algal blooms that can potentially become hazardous to local communities and marine life (Fig. 3) [4]. Understanding the impacts of potential increased algal bloom frequency is important to fishing communities and commercial fisheries since they can impact the overall health of the ecosystem [1].

![Alt text](Figures/Figure1.png)
###### Figure 1: Projected annual carbon emissions and projected global atmospheric temperatures. Highlights how atmospheric temperatures are expected to continue to increase, indicating potential further shifts in climatic feedback. image source [7]

![Alt text](Figures/Figure2.png)
###### Figure 2: Areas of coastal upwelling zones. image source [5]

![Alt text](Figures/Figure3.png)
###### Figure 3: Diagram briefly showcasing how upwelling occurs and how it influences primary productivity leading to algal blooms. image source [3]

# Data
##### From NOAA’s Coastwatch ERDDAP system, two datasets were downloaded:
    Timeframe and Coordinate Box Dimensions
        09-03-2021 to 04-01-2025 (Wind)
        09-03-2021 to 03-29-2025 (SST)
        35º N to 40º N, -125º W to -123º W
            California Current System
##### Wind (time, lat, lon, u_wind, v_wind, ekman_upwelling)
    File that was downloaded from the link: windsproducts.csv
    Link to data page: https://coastwatch.pfeg.noaa.gov/erddap/griddap/erdQCwindproducts1day.html?wind_u%5B(2025-04-09T12:00:00Z)%5D%5B(10.0)%5D%5B(44.500045):(32.166724)%5D%5B(-131.166715):(-118.833394)%5D,wind_v%5B(2025-04-09T12:00:00Z)%5D%5B(10.0)%5D%5B(44.500045):(32.166724)%5D%5B(-131.166715):(-118.833394)%5D&.draw=vectors&.vars=longitude%7Clatitude%7Cwind_u%7Cwind_v&.color=0x000000&.bgColor=0xffccccff
##### Sea-Surface Temperature (time, lat, lon, sst)
    File that was downloaded from the link: sst.csv
    Link to data page: https://coastwatch.pfeg.noaa.gov/erddap/griddap/ncdcOisst21Agg_LonPM180.html 

# Methods
##### Interpolation Method: Spline Interpolation
##### Machine Learning Method: Random Forest and Neural Network
##### Extra: Logistic Regression + Plots

## Parameters Used
##### Upwelling occurs when there are strong offshore winds and for the California Current System, those are northerly/northwesterly/equatorward winds and events are typically 1-2 weeks [3]. For CCS, it also causes cold nutrient-rich bottom waters to be brought to the surface, hence we can use sea-surface temperatures and chlorophyll-a data. Unfortunately, chl-a datasets were too large for download (2019 MacBook Pro was used) and when a .csv file was downloadable, it was on a much shorter time scale than wind and SST datasets, as well as still too computationally heavy. 

##### Parameters are based on what is known to cause upwelling in the CCS as well as Barrow Canyon, AK to help refine the upwelling definition in the code (DatasetPreparation.ipynb). Upwelling in Barrow occurs when winds are greater than 4 m/s, last for more than 12 hours and are easterly winds, strong upwelling events occur with >10 m/s that last for 4 or more days [8]. Together, upwelling was defined using positive u wind (meridional, west-east (x) direction), negative v wind (zonal, north-south (y) direction), wind speed > 5 m/s and if SST decreased. U and v wind were defined based on that positive u wind met wind from the west, and negative v wind indicating winds from the north (Fig. 4). 

##### These parameters were defined on a 1+ and 3+ day scale. 1+ day will overestimate the true number of actual upwelling events occurring, while 3+ day scale will likely overestimate but not as much as the 1+ day. This was also not to limit events that are longer than 14 days as with upwelling there are lag responses. Meaning that non-favorable upwelling winds will need to persist almost as long as what would result in upwelling, but if they were to reverse back to favorable upwelling winds in less than 6 hours, upwelling could still persist.

###### Relative parameter used in code: 
######     (u_wind > 0 and v_wind < 0 and wind_speed > 5 and SST_decrease == True)

###### Note: did not use ekman_upwelling data in defining parameters but can still be used - upwelling is occurring when ekman_upwelling > 0, otherwise downwelling is occurring (ekman_upwelling < 0) [1]

![Alt text](Figures/Figure4.png)
###### Figure 4: Zonal (v in y direction) vs Meridonal (u in x direction) wind, how to define northwesterly/eqautorward winds for the upwelling parameter [6]

## Dataset Preparation Code
    DatasetPreparation.ipynb
    Datasets Created: wind_sst.csv, upwelling_spatial.csv and upwelling_nonspatial.csv

## Upwelling Predictions Code
    UpwellingPredictions-2.ipynb
    
## Logistic Regression Code
    Logistic_CorrelationPlot-2.ipynb

## Visual Representation Code
    ImageAnalysis.ipynb
    # just a basic timeseries plot that showcases the upwelling = 1 vs SST

# Results and Summary
![Alt text](Figures/Figure5.png)
###### Figure 5:

![Alt text](Figures/Figure6.png)
###### Figure 6:

![Alt text](Figures/Figure7.png)
###### Figure 7:

![Alt text](Figures/Figure8.png)
###### Figure 8:

![Alt text](Figures/Figure9.png)
###### Figure 9:

![Alt text](Figures/Figure10.png)
###### Figure 10:

![Alt text](Figures/Figure11.png)
###### Figure 11:

# Notes 
##### 1. A 2019 MacBook Pro was used (took up about 30 GB of computer storage)
##### 2. All code was done in Jupyter Lab (through Anaconda extension)
##### 3. Data is very computationally heavy, recommend a computer with more RAM than what was used
##### 4. Neural Network may showcase a potential dataset processing error

# Rerefences

##### [1] Bograd, S. J., Schroeder, I., Sarkar, N., Qiu, X., Sydeman, W. J., & Schwing, F. B. (2009). Phenology of Coastal Upwelling in the California Current. Geophysical Research Letter, 36(1). https://doi.org/10.1029/2008GL035933.

##### [2] Ding, H., Alexander, M. A., & Jacox, M. G. (2021). Role of Geostrophic Currents in Future Changes of Coastal Upwelling in the California Current System. Geophysical Research Letters, 48(3). https://doi-org.lp.hscl.ufl.edu/10.1029/2020GL090768.

##### [3] Northwest Fisheries Science Center. (2024). Oceanography of the Northern California Current Study Area. NOAA Fisheries. www.fisheries.noaa.gov/west-coast/science-data/oceanography-northern-california-current-study-area#:~:text=Coastal%20Upwelling,-Coastal%20upwelling%20is&text=Upwelling%20can%20occur%20year%2Dround,(Figure%20CU%2D01).

##### [4] Townhill, B. L., Tinker, J., Jones, M., Pitois, S., Creach, V., Simpson, S. D., Dye, S., Bear, E., & Pinnegar, J. K. (2018). Harmful Algal Blooms and Climate Change: Exploring Future Distribution Changes. ICES Journal of Marine Sciences, 75(6), pp. 1882-1893. https://doi.org/10.1093/icesjms/fsy113.

##### [5] Upwelling. National Ocean Service (NOAA). https://oceanservice.noaa.gov/education/tutorial_currents/03coastal4.html

##### [6] Ichsana, D. (2023). Meteorology 101: How to Plot Wind Map. Medium. https://dwikita-ichsana.medium.com/meteorology-101-how-to-plot-wind-map-e43c196edce8

##### [7] Lindsey, R., & Dahlman, L. (2024). Climate Change: Global Temperature. NOAA Climate. www.climate.gov/news-features/understanding-climate/climate-change-global-temperature

##### [8] Pickart, R. S., Schulze, L. M., Moore, G. W. K., Charette, M. A., Arrigo, K. R., Dijken, G. V., Danielson, S. L. (2013). Long-term Trends of Upwelling and Impacts on Primary Productivity in the Alaskan Beaufort Sea. Deep Sea Research Part I: Oceanographic Research Papers, 79, pp. 106-121. https://doi.org/10.1016/j.dsr.2013.05.003.
