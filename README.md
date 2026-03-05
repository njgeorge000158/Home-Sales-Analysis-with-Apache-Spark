![home_sales](https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/f76b8b4c-8a75-46f6-92bc-156d3c9e7dc0)

----

# **Home Sales Analytics at Scale: A PySpark Analysis on Google Colab**

----

## **Project Overview**

This project leverages PySpark on Google Colab to extract key metrics from a home sales dataset using Spark SQL queries, temporary views, cached tables, and Parquet-formatted data partitions. Beyond answering specific questions about home sale prices, the project serves as a practical demonstration of how different data storage and retrieval strategies affect query performance — a critical consideration when working with large-scale datasets in distributed computing environments.

---

## **Analytical Questions and Findings**

### *Question 1: What is the average price of a four-bedroom house sold each year?*

<img width="803" alt="home_sales_query3" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/a66cadf6-01ab-4763-acda-5379ff876ffe">

As shown in Image 1, the Spark SQL query filters the dataset to four-bedroom homes, groups by sale year, and returns the following average prices:

| Year | Average Price |
|---|---|
| 2022 | $296,363.88 |
| 2021 | $301,819.44 |
| 2020 | $298,353.78 |
| 2019 | $300,263.70 |

The results reveal a notably narrow price range across all four years — a spread of only about $5,500 from the lowest to the highest annual average. Prices peaked in 2021 at approximately $301,819 before declining modestly in 2022 to $296,364. No clear directional trend is apparent: prices fluctuate slightly from year to year without a sustained upward or downward trajectory. This stability suggests that, for four-bedroom homes specifically, annual sale year alone is a weak predictor of price — other factors are likely driving individual sale prices within each year.

### *Question 2: What is the average price of a three-bedroom, three-bathroom home by year built?*

<img width="797" alt="home_sales_query4" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/80885e84-ba01-4cb1-80ab-e7c41c4de379">

Image 2 presents average prices for three-bedroom, three-bathroom homes grouped by the year in which the home was constructed, spanning 2010 through 2017:

| Year Built | Average Price |
|---|---|
| 2017 | $292,676.79 |
| 2016 | $290,555.07 |
| 2015 | $288,770.30 |
| 2014 | $290,852.27 |
| 2013 | $295,962.27 |
| 2012 | $293,683.19 |
| 2011 | $291,117.47 |
| 2010 | $292,859.62 |

Again, the price variation across years is remarkably compressed — all eight averages fall within a roughly $7,200 range, with no consistent upward or downward trend tied to construction vintage. Homes built in 2013 command the highest average price in this category at approximately $295,962, while 2015-built homes are the least expensive at $288,770. The absence of a clear relationship between build year and average price suggests that construction year alone does not meaningfully drive market value for this home configuration — the market appears to value these homes comparably regardless of when they were built.

### *Question 3: What is the average price of a three-bedroom, three-bathroom, two-floor home of at least 2,000 square feet, by year built?*

<img width="864" alt="home_sales_query5" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/c394ee93-2ae4-4057-abe3-40d8cc4c62bd">

Adding floor count and minimum square footage as additional filters, Image 3 refines the previous query further:

| Year Built | Average Price |
|---|---|
| 2017 | $280,317.58 |
| 2016 | $293,965.10 |
| 2015 | $297,609.97 |
| 2014 | $298,264.72 |
| 2013 | $303,676.79 |
| 2012 | $307,539.97 |
| 2011 | $276,553.81 |
| 2010 | $285,010.22 |

This more constrained query produces greater year-to-year variation than the previous two — a range of approximately $31,000 from the lowest average (2011 at $276,554) to the highest (2012 at $307,540). Interestingly, the pattern here does not follow a simple linear trend: prices are highest for homes built between 2012 and 2014, dip sharply for 2011-built homes, and taper off again for the most recently built homes in 2017. This non-linear pattern reinforces the conclusion that construction year is not a reliable standalone predictor of price — even when controlling for bedroom count, bathroom count, floor count, and minimum living area.

### *Question 4: What is the "view" rating for homes with an average price of at least $350,000?*

<img width="830" alt="home_sales_query6" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/e51fd232-62ab-4e69-a49e-d882fb5f5307">

The fourth and most revealing query examines the relationship between a property's view rating — scored on a scale from 0 to 99 — and average sale price, filtered to homes averaging $350,000 or more. Images 4 through 7 all present versions of this query run under different execution strategies, with the top 20 results displayed in each case. A selection of the results:

| View Rating | Average Price |
|---|---|
| 99 | $1,061,201.42 |
| 98 | $1,053,739.33 |
| 97 | $1,129,040.15 |
| 96 | $1,017,815.92 |
| 91 | $1,137,372.73 |
| 84 | $1,117,233.13 |
| 92 | $970,402.55 |

The results are striking. Every view rating displayed in the top 20 results is associated with an average home price well above $1,000,000 — in several cases approaching or exceeding $1.1 million. This stands in dramatic contrast to the relatively flat price patterns observed in the first three queries. Where bedroom count, bathroom count, floor count, and build year produced average prices clustered in the $275,000–$310,000 range, view rating produces averages three to four times higher. This finding strongly implies that view quality is among the most powerful determinants of home price in this dataset — far more influential than the structural and temporal attributes explored in the preceding queries.

---

## **Query Performance: Uncached vs. Cached vs. Parquet**

<img width="797" alt="home_sales_query7" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/68e9d1c6-7e04-4026-916e-1cdf0d618b58">

<img width="798" alt="home_sales_query8" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/5b8f6624-5add-4def-976b-0cfbd68ed11a">

<img width="652" alt="home_sales_query9" src="https://github.com/njgeorge000158/Home-Sales-Analysis-with-Google-Colab-and-PySpark/assets/137228821/1ec90324-98b2-4bb8-afeb-97a7f6c5555a">

A central objective of this project is to demonstrate the performance implications of different data storage and retrieval strategies in a Spark environment. The same view-rating query was executed under three conditions, with execution times recorded:

| Execution Method | Runtime |
|---|---|
| Uncached (original data) | 1.6829 seconds |
| Cached table | 1.0190 seconds |
| Parquet-formatted partition | 1.1948 seconds |
| Parquet DataFrame API | 1.5331 seconds |

Caching delivered the fastest execution time, reducing runtime by approximately 39% compared to the uncached baseline. By loading the dataset into memory, Spark eliminates the I/O overhead of reading from disk on repeated queries — a benefit that compounds significantly as dataset size grows. Parquet formatting produced the second-best performance, running approximately 29% faster than the uncached baseline. Parquet's columnar storage format enables two powerful optimizations: column pruning, which skips columns irrelevant to the query, and predicate pushdown, which filters data at the storage layer before it reaches the query engine — reducing both the volume of data read and the computational work required. The Parquet DataFrame API approach, while using the same underlying file format, ran slightly slower than the SQL-based Parquet query, reflecting the different execution paths taken by the two methods.

All factors being equal — query complexity, dataset size, system resources, and hardware configuration — both caching and Parquet formatting offer meaningful and measurable performance advantages over unoptimized data access. For large-scale production workloads, these gains would be substantially more pronounced.

---

## **Conclusions**

The home sales analysis surfaces two primary findings. First, the structural and temporal attributes most commonly associated with home valuation — bedroom count, bathroom count, floor count, build year, and sale year — show surprisingly little relationship with average price in this dataset. Averages across all permutations of these attributes cluster within a relatively narrow band, with no consistent directional trend tied to any single variable. This suggests that housing prices are driven by a more complex combination of factors, including economic and market conditions, geographic location, neighborhood characteristics, and comparative property attributes — none of which are fully captured by the variables available in this dataset.

Second, and most compellingly, view rating emerges as a dramatically more powerful price signal than any structural attribute examined. Homes with high view ratings command average prices exceeding $1,000,000 — three to four times the averages produced by any other query in the analysis. For buyers, sellers, and analysts alike, this finding underscores the outsized premium the market places on scenic views relative to the physical characteristics of the home itself.

From a technical standpoint, the project demonstrates concretely that caching and Parquet formatting are not merely theoretical optimizations — they produce measurable, reproducible performance gains even on modest datasets, and their value scales directly with data volume.

----

## Copyright

Nicholas J. George © 2023. All Rights Reserved.
