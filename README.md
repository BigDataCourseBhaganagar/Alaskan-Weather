# Alaskan-Weather

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#Data-information">Data Information</a>
     </li>
      <li><a href="#project-goals">Project Goals</a></li>
    <li>
      <a href="#hypothesis">Hypothesis</a>    
    </li>
    <li><a href="#methods">Methods</a></li>
    <li><a href="#results-and-conclusion">Results & Conclusion</a></li>
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

<!-- Project Goals -->
The main purpose of this project is to reduce a large set of data into a working dataframe that can be used to further analysis. This will require the use of different python packages and an understanding of how they work. Once a working dataframe is achieved, the correlation between different variables will be observed for a better understanding of how different components of weather relate to one another.

<!-- Hypothesis -->
## Hypothesis

It can be hypothesized that the location of each datapoint has an effect on each variable. It’s expected that the average temperature will decrease, while the amount of precipitation, solar radiation, irradiation, vapor pressure, relative humidity, and ambient dewpoint will all increase with increasing latitude values. It’s also hypothesized that throughout each of the year, the average temperatures will peak during the summer and spring seasons, and drastically decrease during the last half of the year. It’s also assumed that with the 1% increase in greenhouse gasses each year, there will be an increased amount of solar radiation over time, resulting in higher average temperatures, less precipitation, greater humidity, and an increased vapor pressure over time. To solve this, a correlation analysis will be conducted.


<!-- Methods -->
## Methods
Firstly, the necessary modules must be imported. For this project, matplotlib, numpy, pandas, xarray, scipy, and metpy will be used, and a correlation analysis will be conducted. The original filetype is Net-CDF4, so it's necessary that xarray and pandas is used to convert this to a working dataframe. Because the original dataset contained over 7.7 milion rows, it will need to be filtered and reduced. Firstly, all NaN values were removed. Outlier values that were more than 2 standard deviations from the averages of each column were extracted using scipy, reducing the dataframe to about 3.6 million rows.

Using metpy, the ambient dewpoint and heat index were calculated and added to the dataframe. Using the datetime module, the data was averaged based on the month and year and set to their own data frame. With all of the desired data, a correlattion analysis was conducted. Firs, a seaborn heatmap was used to find the correlation between each variable using:

```ruby
cor = DataA.corr()
plt.figure(figsize=(10, 8))
sn.heatmap(cor, annot = False, cmap = 'Blues')
plt.show()
```
To find the correlation between the latitude values and the desired variables, an Alaskan-based heatmap was created along with a scatter splot. To create the heatmap, the desired variables were converted to a numpy array to allow for the use of a colormap for the plot. The heatmap was created using:

```ruby
proj = ccrs.LambertConformal(central_longitude = -153, central_latitude = 65)
fig = plt.figure(figsize = (12,10))
ax = fig.add_subplot(1,1,1, projection = proj)
ax.set_extent([-179,-145,50,70],ccrs.Geodetic())
ax.add_feature(USCOUNTIES.with_scale('5m'))
at = ax.scatter(DataAA.lon, DataAA.lat, c = avg, cmap = 'inferno', transform = ccrs.PlateCarree(), s=(DataAA.Avg_Temp/15)**9.5)
ax.gridlines(draw_labels=True, dms=True, x_inline=False, y_inline=False)
fig.colorbar(at, ax=ax)
```
For the monthly and yearly analysis, scatter and lineplots were used to show each variable's relationship with time. With the completed analysis, conclusions can be made.

<!-- Results and Conclusion -->
## Results & Conclusion

From the first correlation analysis for each variable against another, strong correlaions appear to be present at multiple instances. The Avg Temp appeared to correlate with many other values, but this was expected as the temperature plays a major roll in weather conditions. Additionally, a strong correlation occurred between solar radiation and irridiation, as well as the dewpoint and average temperature, vapor pressure, and minimum temperature. 

For the correlation between the latitude values and the selected variables, the average temperature, relative humidity, irradiation, solar radiation, precipitation, vapor pressure, and the ambient dewpoint had an overall decrease with increasing latitude coordinate values. However, the heat index increased with higher values.

Upon analysis, it was found that the solar radiation had an overall decrease with increasing year, while the average temperature, relative humidity, and vapor pressure decreased. There was a slight decrease in precipitation with respect to the year, but overall there was no notable trend.

For the monthly time analysis, it’s observed that due to the absense of sun during the colder seasons in Alaska, there is a decrease in solar radiation, average temperature, precipitation, and vapor pressure. However, the humidity spikes during the last half of the year.
From this analysis, it’s been observed that the latitude coordinate does in fact have an effect on the many components of weather. 

The average temperature, relative humidity, irradiation, solar radiation, precipitation, vapor pressure, and the ambient dewpoint increase with increasing latitude values, while the heat index decreases.  It was also found that throughout an average year, Alaska’s absence of sun causes a drop in the vapor pressure, average temperature, solar radiation, and precipitation, but a spike in the relative humidity


<!-- Link to Data -->
## Link to Data
The raw dataset can be accessed through these links:
  * [Google Drive](https://drive.google.com/file/d/1kjzuaNx7G6EmjFbIToN6DitoZnbmfy9V/view?usp=sharing)
  * [NASA Earth Data Search](https://search.earthdata.nasa.gov/search/granules?p=C1337992250-ORNL_DAAC&pg[0][gsk]=-start_date&g=G1422958404-ORNL_DAAC&q=vemap%20alaska&tl=1602683497!4!!&m=62.57812500000001!-149.625!1!1!0!0%2C2)
