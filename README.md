# Data exploration and preparation for visualisation
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


5. Rename columns so it reads better and arrange data in ascending order
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/a057a7a8-4c29-4972-b20f-19c264c67e91)
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/cb2b37f7-6e04-456e-9617-fe2defdb02f8)


6. Merging Metadata
Since the "Region" and "Income Group" was in a separate excel sheet with metadata. The sheet was read and merged.
![image](https://github.com/Kfkyyian1/wdiexploration/assets/146427900/5cc84f84-65ff-47eb-ae6c-03036d462e0f)







# Time Series Plot: Singapore's GDP growth overtime (1998-2022)
# Scatter Plot: Correlation between economic growth and child mortality
# Animate Scatter Plot
# Line Plot: North America's GDP Growth Overtime by Country



