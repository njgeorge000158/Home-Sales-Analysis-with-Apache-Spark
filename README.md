![home_sales](https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/f76b8b4c-8a75-46f6-92bc-156d3c9e7dc0)

----

# Home Sales Analysis with Google Colab and PySpark

----

With PySpark on Google Colab, this project looks for key metrics about home sales data using temporary views, data partitions, and cached tables. The project answers the following questions about home sales:

1. What is the average price for a four-bedroom house sold for each year?

<img width="803" alt="home_sales_query3" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/a66cadf6-01ab-4763-acda-5379ff876ffe">

2. What is the average price of a home for each year it was built that has three bedrooms and three bathrooms?

<img width="797" alt="home_sales_query4" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/80885e84-ba01-4cb1-80ab-e7c41c4de379">

3. What is the average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet?

<img width="864" alt="home_sales_query5" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/c394ee93-2ae4-4057-abe3-40d8cc4c62bd">

4. What is the "view" rating for homes costing more than or equal to $350,000?

<img width="830" alt="home_sales_query6" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/e51fd232-62ab-4e69-a49e-d882fb5f5307">

Many factors influence query runtime: query complexity, size of data set, system resources, and hardware configuration, among others. All factors being equal for this project, both cached data and Parquet formatted data have faster runtimes compared to the original data. Specifically, caching stores the data in memory for rapid retrieval as opposed to reading information from the hard drive, and Parquet is an optimized storage format specifically designed for efficient data processing that offers several advantages over traditional formats by enabling column pruning and predicate pushdown. These features allow queries to leverage columnar optimizations to skip irrelevant columns and partitions during execution for faster performance, reduced storage requirements, and improved overall data processing efficiency. The following execution times demonstrate the advantages of using caching and partitioning to improve the runtime of data analysis tasks, which are crucial for working effectively with large data sets.

<img width="797" alt="home_sales_query7" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/68e9d1c6-7e04-4026-916e-1cdf0d618b58">

<img width="798" alt="home_sales_query8" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/5b8f6624-5add-4def-976b-0cfbd68ed11a">

<img width="652" alt="home_sales_query9" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/1ec90324-98b2-4bb8-afeb-97a7f6c5555a">


In conclusion, the provided home sales information does not show any direct relationship between the year of construction or sale and the average price. Consequently, there is likely other determinants for housing prices, such as changes in economic conditions, changes in market conditions, location, and comparative property attributes.

----

## Copyright

Nicholas J. George © 2023. All Rights Reserved.
