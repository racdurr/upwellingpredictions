# California Current System: Upwelling Predictions





# Background
Increased carbon dioxide emissions has caused global atmospheric temperatures to rise, which has led to various climatic shifts. Some of these shifts include changes in weather patterns and rising sea-surface temperatures and are expected to get worse (Fig. 1). It is also expected that upwelling will increase in the future, which can result in more primary productivity due to upwelling bringing cold nutrient-rich waters to the surface (Fig. 2) [2, 3]. However, this primary productivity can result in algal blooms that can potentially become hazardous to local communities and marine life (Fig. 3) [4]. Understanding the impacts of potential increased algal bloom frequency is important to fishing communities and commercial fisheries since they can impact the overall health of the ecosystem [1].

###### Figure 1: Projected annual carbon emissions and projected global atmospheric temperatures. Highlights how atmospheric temperatures are expected to continue to increase, indicating potential further shifts in climatic feedback. image source [7]
###### Figure 2: Areas of coastal upwelling zones. image source [5]
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
##### Machine Learning Method: Random Forest
##### Other: Logistic Regression + Plots

## Dataset Preparation Code
    DatasetPreparation.ipynb

## Upwelling Predictions Code


## Visual Representation Code




# Summary

# Notes 


# Rerefences

##### [1] Bograd, S. J., Schroeder, I., Sarkar, N., Qiu, X., Sydeman, W. J., & Schwing, F. B. (2009). Phenology of Coastal Upwelling in the California Current. Geophysical Research Letter, 36(1). https://doi.org/10.1029/2008GL035933.

##### [2] Ding, H., Alexander, M. A., & Jacox, M. G. (2021). Role of Geostrophic Currents in Future Changes of Coastal Upwelling in the California Current System. Geophysical Research Letters, 48(3). https://doi-org.lp.hscl.ufl.edu/10.1029/2020GL090768.

##### [3] Northwest Fisheries Science Center. (2024). Oceanography of the Northern California Current Study Area. NOAA Fisheries. www.fisheries.noaa.gov/west-coast/science-data/oceanography-northern-california-current-study-area#:~:text=Coastal%20Upwelling,-Coastal%20upwelling%20is&text=Upwelling%20can%20occur%20year%2Dround,(Figure%20CU%2D01).

##### [4] Townhill, B. L., Tinker, J., Jones, M., Pitois, S., Creach, V., Simpson, S. D., Dye, S., Bear, E., & Pinnegar, J. K. (2018). Harmful Algal Blooms and Climate Change: Exploring Future Distribution Changes. ICES Journal of Marine Sciences, 75(6), pp. 1882-1893. https://doi.org/10.1093/icesjms/fsy113.

##### [5] Upwelling. National Ocean Service (NOAA). https://oceanservice.noaa.gov/education/tutorial_currents/03coastal4.html

##### [6] Ichsana, D. (2023). Meteorology 101: How to Plot Wind Map. Medium. https://dwikita-ichsana.medium.com/meteorology-101-how-to-plot-wind-map-e43c196edce8

##### [7] Lindsey, R., & Dahlman, L. (2024). Climate Change: Global Temperature. NOAA Climate. www.climate.gov/news-features/understanding-climate/climate-change-global-temperature

##### [8] Pickart, R. S., Schulze, L. M., Moore, G. W. K., Charette, M. A., Arrigo, K. R., Dijken, G. V., Danielson, S. L. (2013). Long-term Trends of Upwelling and Impacts on Primary Productivity in the Alaskan Beaufort Sea. Deep Sea Research Part I: Oceanographic Research Papers, 79, pp. 106-121. https://doi.org/10.1016/j.dsr.2013.05.003.
