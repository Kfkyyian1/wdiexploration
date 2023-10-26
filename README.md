![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/4f59649d-00e8-43c9-a17a-cca78268bc3d)# Data exploration and preparation for visualisation
Firstly, in preparation for plotting, the data for past 25 years was extracted from WDI (1998-2022) and brought into R studio by setting the working directory, importing the file, and subsequently renaming it as "df." Some data cleaning and wrangling was done to ensure it's in long format and ready to visualise. Preview of the raw data can be seen below.
<img width="1377" alt="Screenshot 2023-10-26 at 11 19 13 PM" src="https://github.com/Kfkyyian1/wdiexploration/assets/146427900/cd989afb-712a-41b9-a0a7-577e9343721a">

1. Replace column names from column 5-29 to show the proper Year format
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/f412c380-4ef2-4f63-b51c-804536b58e45)


2. Remove inputs with ".." missing value and replace it with empty string. This is to prep for visualisation.
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/84b2486c-a0c8-440e-82bc-cf8a3123e5dc)


3. Since column 5 onwards are all years, the class of the data was changed to numeric
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/b3207a42-d23c-4b77-baa9-29d521551ddc)


4. Pivot the data via piping and rename new dataset as df2
- #Use pivot_longer to Collect the Variables Under Years as a single column
- #Use pivot_wider to extract out variables lumped in SeriesName column
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/5991566f-9913-4588-baf8-8e0b2e47066d)


5. Rename columns and arrange data in ascending order <br>
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/23c98760-82f6-4bfc-868c-6512741993e3)


6. Merging Metadata
Since the "Region" and "Income Group" was in a separate excel sheet with metadata. The sheet was read and merged. <br>
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/5cc84f84-65ff-47eb-ae6c-03036d462e0f)

7. Final clean dataset is then exported. Preview below. <br>
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/79f0dfe9-5b1e-43e7-b3c2-443811bc27c1)

<img width="772" alt="image" src="https://github.com/Kfkyyian1/wdiexploration/assets/146427900/0f9ff5c2-888b-42bf-b38e-62a1f652634b">


# Time Series Plot: Singapore's GDP growth overtime (1998-2022)
![1_SG_GDP_Overtime](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/b17c39f0-4227-4dae-aaaf-451d2d2f4273)
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/5738f6f3-9205-4f77-b994-0d50e244fafa)

The visual representation showcased above is to offer a visual depiction of Singapore's GDP growth over time. To facilitate this, a subset of Singapore's data was extracted, with the year on the x-axis and GDP growth on the y-axis. The visual incorporates a red path line, illustrating the annual fluctuations in GDP growth from 1998 to 2022. Complementing this is a gray non-linear line, capturing the broader trends in GDP growth across the same period. 

Upon observing the visualization, it becomes evident that an outlier exists in 2010 when Singapore experienced a remarkable surge in GDP growth, subsequently stabilizing in the following years, maintaining growth rates between 2.5 and 5, before plunging in 2020. This starkly contrasts with the data preceding 2010, marked by greater volatility. Moreover, the non-linear trend line suggests an overall downward trajectory in GDP growth, but it's been picking up the past 5 years and most probably is because of recovery from Covid. To further enrich the analysis, it would be beneficial to overlay significant historical events onto the plot. These overlays could include major infrastructure projects, economic policies, or financial crises, offering valuable insights into how these events correlate with fluctuations in GDP growth.


# Scatter Plot: Correlation between economic growth and child mortality
![2_Economic Growth   Child Mortality](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/7bd94960-2c17-4cf9-993a-edc7fc1cb729) <br>
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/bc3f1a73-ef5e-4e98-936c-c69c1c7b0520) <br>
Next, the above shows a scatter plot in using cross-sectional data, aiming to show the correlation between economic growth and child mortality. Before embarking on the plotting, a few data pre-processing steps were taken. Specifically, the Region column was rectified by removing empty labels and conducted a comprehensive data summary check utilizing the "summary()" and "unique()" commands to ensure data integrity.

For the visualization itself, the dataset was harnessed on a global scale, with GDP Per Capita mapped to the x-axis and Child Mortality to the y-axis. A linear regression line was introduced, distinguished in a striking red. Furthermore, to enhance the interpretability of the x-axis, a logarithmic scale with a base of 10 was implemented, rendering the values in dollars. It's important to note that we employed the Region variable as an aesthetic, differentiating data points by color. Finally, this visualization was polished with a title and informative caption, alongside refined axis labels, facilitating a more lucid and insightful presentation.

It can be observed a discernible trend emerges from the descending trajectory of the red linear line. This trajectory signifies that higher GDP per Capita tends to correspond with lower child mortality rates. Furthermore, it is noteworthy that Sub-Saharan Africa registers the highest child mortality rates in contrast to other regions, offering a poignant illustration of this vital cross-sectional relationship.


# Animate Scatter Plot
![4_Animated Plot of Economic Growth   Child Mortality](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/06ad3d00-7eef-45b0-ae5d-609ec58c2395) <br>
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/0adcdde6-f251-43cb-be15-74dea91b8d06) <br>
The animated cross-sectional visualization above was created from the second plot, and thoughtfully segmented into distinct graphs, each focusing on regional trends using the “facet_wrap()” command. A discernible pattern emerges, revealing a consistent downward trajectory in child mortality rates across regions, with the noteworthy exception of North America. Intriguingly, a correlation between economic growth and reduced child mortality becomes apparent; instances of economic expansion coincide with declines in child mortality rates.

To delve deeper into the specific dynamics within North America, an analysis of child mortality reveals a range between 4.4 and 7.4, after excluding null (NA) records. This implies that, despite experiencing rising GDP per capita, North America has managed to sustain impressively low child mortality rates. This achievement may be attributed to various factors, including a robust healthcare system and enhanced healthcare accessibility.

Furthermore, the extent of linear progression observed in each graph conveys valuable insights. Europe and Central Asia exhibit the most extended linear lines, signifying substantial growth since 1998. Additionally, Sub-Saharan Africa's higher GDP per capita in comparison to South Asia contrasts with its elevated child mortality rates. This phenomenon may stem from a confluence of factors, including healthcare challenges, distinct socio-economic dynamics, and income inequality, illustrating that GDP per capita alone does not uniformly translate into holistic prosperity for a substantial segment of the population.


# Line Plot: North America's GDP Growth Overtime by Country
![3_North America GDP Growth Over Time](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/5fec08ea-0573-42ac-b8a6-5f2a38bec32d) <br>
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/5c18ccd2-4387-4d5e-96b1-2f782a5b88d9) <br>
The longitudinal visualization above depicts North America's GDP Growth on the vertical axis and Year on the horizontal axis, segmented by individual countries. Notably, the growth trends of Canada and the United States exhibit greater stability in comparison to Bermuda. Bermuda experienced a substantial surge in growth, reaching nearly 10 in the year 2000, followed by a sharp decline to a low point below -5 in 2009, 2012 and 2020. In contrast, Canada maintained a relatively consistent growth pattern within the range of 0 to 5, with occasional outliers noted in 2009 and 2020. Similarly, the United States demonstrated a consistent growth trajectory within the same range, albeit with an outlier in 2009 and 2020. Hence, there’s a simultaneous decline in GDP Growth across all North American countries in 2009 and 2020. 



