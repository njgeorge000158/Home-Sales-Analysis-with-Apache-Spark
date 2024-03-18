![fwp-sic-1c67bda0ab1d5a3b9d13dcd87ff84277680166f0](https://github.com/njgeorge000158/Home_Sales/assets/137228821/aee2c111-8a23-4306-8269-a02e7fb74b5f)

----

# Home Sales Analysis with Google Colab and PySpark

----

With PySpark on Google Colab, this project looks for key metrics about home sales data using temporary views, data partitions, and cached tables. The project answers the following questions about home sales:

1. What is the average price for a four-bedroom house sold for each year?

<img width="655" alt="Screenshot 2023-11-27 at 3 32 09 PM" src="https://github.com/njgeorge000158/Home_Sales/assets/137228821/ded279c0-78ee-4623-82ee-76f26d03acd9">

2. What is the average price of a home for each year it was built that has three bedrooms and three bathrooms?

<img width="641" alt="Screenshot 2023-11-27 at 3 33 06 PM" src="https://github.com/njgeorge000158/Home_Sales/assets/137228821/48a84d89-4db0-40c0-a242-14bbbe336cc4">

3. What is the average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet?

<img width="714" alt="Screenshot 2023-11-27 at 3 34 51 PM" src="https://github.com/njgeorge000158/Home_Sales/assets/137228821/a2028c29-b2f0-4bad-8f95-bfa1ac4ddd72">

4. What is the "view" rating for homes costing more than or equal to $350,000?

<img width="685" alt="Screenshot 2023-11-27 at 3 35 37 PM" src="https://github.com/njgeorge000158/Home_Sales/assets/137228821/7b08cf35-9c83-4b18-be1c-1d35f486adab">

Many factors influence query runtime: query complexity, size of data set, system resources, and hardware configuration, among others. All factors being equal for this project, both cached data and Parquet formatted data have faster runtimes compared to the original data. Specifically, caching stores the data in memory for rapid retrieval as opposed to reading information from the hard drive, and Parquet is an optimized storage format specifically designed for efficient data processing that offers several advantages over traditional formats by enabling column pruning and predicate pushdown. These features allow queries to leverage columnar optimizations to skip irrelevant columns and partitions during execution for faster performance, reduced storage requirements, and improved overall data processing efficiency. The following execution times demonstrate the advantages of using caching and partitioning to improve the runtime of data analysis tasks, which are crucial for working effectively with large data sets.

<img width="690" alt="Screenshot 2023-11-27 at 4 03 45 PM" src="https://github.com/njgeorge000158/Home_Sales/assets/137228821/fef0d54b-1b8b-4fa0-99c1-f9c005eed4bc">

<img width="650" alt="Screenshot 2023-11-27 at 4 04 09 PM" src="https://github.com/njgeorge000158/Home_Sales/assets/137228821/28f7f104-f646-4977-8bc9-87162ed2ae7b">

<img width="702" alt="Screenshot 2023-11-27 at 4 04 42 PM" src="https://github.com/njgeorge000158/Home_Sales/assets/137228821/c8823867-b2ec-47ca-b53d-be2d7dcf5f84">

In conclusion, the provided home sales information does not show any direct relationship between the year of construction or sale and the average price. Consequently, there is likely other determinants for housing prices, such as changes in economic conditions, changes in market conditions, location, and comparative property attributes.
