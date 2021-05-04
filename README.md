# Alaskan-Weather
#Oak-Ridge-National-Laboratory-ORNL-Rotating-Shadowband-Radiometer-RSR-Analysis
Gonzalo Martinez Medina

Abstract
Oak Ridge National Laboratory uses a rotating shadowband radiometer to measure solar radiance in the Oak Ridge National Lab. Data files are available from September 2007 to November 2019. The station has the ability to measure global horizontal radiation (W/m2), diffuse horizontal irradiance, also known as diffuse sky radiation (W/m2), direct normal irradiance (W/m2), and direct normal (bird estimate) using an algorithm that produces estimates of clear sky direct beam. Each irradiance factor can be paired with meteorological components such as air temperature (℃), relative humidity (%), wind speed(m/s), wind direction (degrees from N), estimated barometric pressure (mBar), precipitation and accumulated precipitation (mm), temperature of the CR800 datalogger panel (℃), and the voltage charge of the battery that powers the datalogger and the shadowband (V). The data set from the available dates can be selected in 1-minute intervals, hourly intervals, or daily statistics.

Problem Statement
Identify changes of measured factors across time. What has changed? When? How do season affect the factors, and which factor show no impact.
Assess impact of radiation as a link to climate research and climate change.
Determine possible solar power output as an alternative based on the data collected.
Determine correlation between variables. Analyze high/low correlations and impact.
Eliminate possible outliers from dataset.
Expected Tools
Pandas descriptive statistics, specific python modules for dataset, statistical functions, frequencies, SciPy, Numpy discrete Fourier transformation, visualization with Matplotlib toolkit, and use of in class templates, Met_py modules to plot contour and surface maps of the analyzed region.

Data
Data can be found here: https://midcdmz.nrel.gov/apps/daily.pl?site=ORNL&start=20070912&yr=2019&mo=11&dy=20

and the following table can be edited to extract desired data:
