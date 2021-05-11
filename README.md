# Alaskan-Weather

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#Data-information">Data Information</a>
     </li>
    <li>
      <a href="#hypothesis">Hypothesis</a>    
    </li>
    <li><a href="#methods">Methods</a></li>
    <li><a href="#expected-results">Expected Results</a></li>
    <li><a href="#link-to-data">Link to Data</a></li>  
  </ol>
</details>



<!-- Data Information -->
## Data Information

  This dataset was found on NASA’s Earth Data library, and originated from the National Center for
Atmospheric Research in Boulder, Colorado. It contains the historical climate information of Alaska based
on an annual 1% increase in greenhouse gases. Based on this historical data, future anticipated data is also
included. This dataset begins on 01 January, 1997, and has a time step of 1 month between each data point.
The climate information in this dataset includes the variables of irradiation, precipitation, minimum and
maximum temperature, relative humidity, vapor pressure, solar radiation, as well as the cartesian
coordinates and bounds for each line of data. Before manipulating, this dataset contains 7,7547,904 rows
and 14 columns. As there are many NaN values present, the data set will need to be filtered so the outliers
can be identified and the length can be reduced.

<!-- Hypothesis -->
## Hypothesis

It’s hypothesized that with the 1% increase in greenhouse gasses each year, there will be an increased amount of solar radiation over time, resulting in
higher minimum and maximum temperatures, less precipitation, greater humidity, and an increased vapor pressure.


<!-- Methods -->
## Methods
Firstly, the necessary modules must be imported. For this project, matplotlib, numpy, pandas, xarray, scipy, and metpy will be used, and a correlation analysis will be conducted. The original filetype is Net-CDF4, so it's necessary that xarray and pandas is used to convert this to a working dataframe. Because the original dataset containt over 7.7 milion rows, it will need to be filtered and reduced. Firstly, all NaN values were removed. Outlier values that were more than 3 standard deviations from the averages of each column were extracted. This data contains expected future weather data for Alaska up to the year 2099, so only real, measured values from the 1st 20 years of data were kept. The unit of the time series is in "months since", so the dataframe was grouped based on the month value and the mean of the average temperature for multiple instances. This reduced the dataframe down to 288 rows, and 4032 elements.

<!-- Expected Results -->
## Expected Results

This analysis will result in visualizations of the data regressions, heatmaps, and line charts showing the changes of different variables over time.

<!-- Link to Data -->
## Link to Data
The raw dataset can be accessed through these links:
  * [Google Drive](https://drive.google.com/file/d/1kjzuaNx7G6EmjFbIToN6DitoZnbmfy9V/view?usp=sharing)
  * [NASA Earth Data Search](https://search.earthdata.nasa.gov/search/granules?p=C1337992250-ORNL_DAAC&pg[0][gsk]=-start_date&g=G1422958404-ORNL_DAAC&q=vemap%20alaska&tl=1602683497!4!!&m=62.57812500000001!-149.625!1!1!0!0%2C2)
