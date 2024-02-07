# Home_Sales
Module 22

This Google Colab challenge utilized PySpark and Spark SQL to calculate metrics on home sales. 

Spark was initialized and data was pulled into a DataFrame from an Amazon AWS S3 bucket; from there a temporary view was created called "home_sales".  

Since the year of a sales date was integral to the calculated metrics, I extracted the year from the "date" column and added the new column to the DataFrame (called "year_sold").  This did require an update to the temporary view. 

I then made the following calculations using Spark SQL:
- Average yearly selling price of 4 bedroom homes
- Average selling price of 3 bedroom/3 bathroom homes, based on year the house was built.
- Average selling price of 3 bedroom/3 bathroom/2 level homes that are 2000 sqft or more, based on year the house was built.

Comparing Run Times in temporary view vs. cache vs. Parquet:
Then I calculated the "View" rating of the average selling price of homes that are $350,000 or more.  I recorded that it took .8 seconds to run this calculation. Next I cached & verified the temporary table cache, and proceeded to run the sale calculation to compare the run time.  The calculation from cache took .49 seconds- almost reducing run time by half!  Lastly I partitioned the data in Parquet and ran the calculation again.  This has a run time of 1.14 seconds.  I can then conclude that the cached table had the fastest performance in this comparison.

Finally, I uncached and verified the temporary table was actually uncached.

