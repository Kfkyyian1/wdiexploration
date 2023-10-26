# Data exploration and preparation for visualisation
Firstly, in preparation for plotting, the data for past 25 years was extracted from WDI (1998-2022) and brought into R studio by setting the working directory, importing the file, and subsequently renaming it as "df." Some data cleaning and wrangling was done to ensure it's in long format and ready to visualise. Preview of the raw data can be seen below.
<img width="1377" alt="Screenshot 2023-10-26 at 11 19 13 PM" src="https://github.com/Kfkyyian1/wdiexploration/assets/146427900/cd989afb-712a-41b9-a0a7-577e9343721a">

1. Replace column names from column 5-29 to show the proper Year format
 - colnames(df)[5:29]<-c(1998:2022)

2. Remove inputs with ".." missing value and replace it with empty string. This is to prep for visualisation.
- df == ".." #booleans will show TRUE for missing data, FALSE for cell with data
- class(df == "..") #can observe it's a matrix
- df[df == ".."] = "" #by passing the matrix in the dataset, the TRUE cells will be replaced with empty cell

3. Since column 5 onwards are all years, the class of the data was changed to numeric
- df[5:ncol(df)] <- lapply(df[5:ncol(df)],as.numeric)

4. Pivot the data via piping and rename new dataset as df2
- #Use pivot_longer to Collect the Variables Under Years as a single column
- #Use pivot_wider to extract out variables lumped in SeriesName column
- df %>% 
  pivot_longer(cols = 4:ncol(df), names_to = "Year", values_to = "Values") %>% 
  pivot_wider(names_from = Series.Name, values_from = "Values") -> df2 

5. Rename columns so it reads better and arrange data in ascending order
- colnames(df2) <- c("Country", "CountryCode","Year", "GDPGrowth", "GDPPerCap","ChildMortality")
- df2 <- arrange(df2, CountryCode, Year)

# Merging Meta Data






# Time Series Plot: Singapore's GDP growth overtime (1998-2022)
# Scatter Plot: Correlation between economic growth and child mortality
# Animate Scatter Plot
# Line Plot: North America's GDP Growth Overtime by Country



