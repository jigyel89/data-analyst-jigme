# data-analyst-jigme
Descriptive Analysis

Project Title: 

Analyzing Painted Bikeways in Vancouver: Infrastructure, Trends, and Insights

Student: Jigme Namgyel (2233149)

Objective

The primary objective of this descriptive analysis is to summarize and interpret key characteristics of painted bikeways in Vancouver, using the "Bikeways – Painted Lanes" dataset. The aim is to uncover patterns in construction timelines, street segment types, bikeway subtypes, and operational status, ultimately supporting informed decisions in city planning, safety enhancement, and infrastructure investment.

Dataset

The dataset was downloaded from the City of Vancouver’s Open Data Portal and includes 24 columns with information about painted bikeways. It captures diverse aspects of each bikeway segment, enabling a multidimensional understanding of their development and characteristics. Key fields include:

•	Route and Street Information: Bike route name, Street name

•	Bikeway Classification: Bikeway type, Subtype (e.g., Shared Lane, Buffered Lane)

•	Operational Status: Status (Active or Inactive)

•	Physical Features: Street segment type (Arterial, Residential, etc.), Segment length, Surface type, Speed limit

•	Construction Data: Year of construction, Upgrade year, Construction notes

•	Directionality and Accessibility: Bikeway and Vehicle direction, Snow removal capability, AAA (All Ages and Abilities) Network designation

This comprehensive structure allows for in-depth examination of both temporal and spatial characteristics of Vancouver's painted bikeway network.

Methodology

1.	Data Collection & Ingestion:

The dataset was downloaded and ingested into Amazon S3 using structured folder hierarchies. Each step adhered to the Open Data Portal’s guidelines for weekly updates. AWS S3 (st-raw-jig) served as the raw data repository.

2.	Data Preparation:

Data was profiled and cleaned using AWS Glue DataBrew. Key operations included:

o	Addressing missing values in columns like Construction note, Upgrade year, and Notes

o	Fixing delimiter issues that initially caused incorrect column separation (changed from AWS default  delimiter ‘,’ to delimiter used for the dataset which was ‘;’)

o	Renaming columns using CamelCase and ensuring consistent data types across numeric and string fields

3.	Data Storage & Cataloging:

The cleaned dataset was exported to S3 in both CSV (for human-readable access) and Parquet (for optimized querying) formats. AWS Glue Crawlers were used to extract schema information and store it in the AWS Glue Data Catalog for use in Amazon Athena SQL queries.

4.	Summarization & ETL Processing:

AWS Glue Studio's Visual ETL feature enabled transformation and summarization without coding. Segment-level aggregations were performed to answer specific questions related to year-wise construction, subtype growth, and bikeway activity status.

5.	Descriptive Analysis

The primary objective of this analysis is to answer key business questions related to street segment lengths and bikeway construction. I performed data queries using Amazon Athena and SQL to derive insights efficiently while minimizing query costs.

Questions Addressed
1.	What is the average length of a street segment?

2.	Which street segment is the longest, and which one is the shortest?
 
3.	For each type of street segment, what is the longest and shortest segment?
 
4.	How much bikeway has been built each year, broken down by street segment type?

Key Findings

Street Segment Length Distribution

The average, minimum, and maximum lengths of bikeway segments were calculated by street type:

•	Arterial segments had the longest average bikeway lengths, suggesting they are prioritized for long continuous biking infrastructure.

•	Residential segments were shorter, indicating they may serve as connectors rather than major bikeway corridors.

Bikeway Construction Trends Over Time

•	Construction activity peaked in specific years, revealing cyclical infrastructure investment aligned with city plans.

•	A timeline analysis revealed expansion phases that coincided with policy shifts or infrastructure funding availability.


Subtype Distribution by Street Segment Type

•	Analysis of subtypes like Shared Lanes, Buffered Lanes, and others showed how certain configurations were favored for specific street types.

•	Buffered Lanes were more prevalent in high-traffic arterial and secondary arterial roads, aligning with safety requirements.

Bikeway Status and Street Type Correlation

•	Arterial roads were more likely to have active bikeways, suggesting they receive more attention for upkeep and public usage.

•	Residential streets had a more mixed activity status, possibly due to lower usage intensity or lesser maintenance priority.

Year-over-Year Growth by Subtype

•	Buffered lanes exhibited a sharp increase in deployment after 2015, likely due to new cycling safety initiatives.

•	Other subtypes such as Shared Lane Markings remained relatively stable, indicating a mature deployment stage.

Visualizations Used

•	The annual number of bikeway segments constructed 

•	The spread of segment lengths across street types 

•	The breakdown of subtypes within each street type (Diagram 16)

•	Multi-variable correlations, such as status vs. subtype vs. segment type

 

Recommendations

•	Prioritize Maintenance of Arterial Routes: These routes not only have longer bikeways but also see higher activity. Continued investment is essential for safety and reliability.

•	Expand Bikeways in Residential Zones: Despite lower current density, residential streets have great potential for safe biking corridors, especially for local commuting and children.

•	Promote Buffered Lanes on Key Roads: Given their growth and safety profile, these should be expanded beyond current deployment patterns.

•	Ensure Data Quality for Ongoing Analysis: Routine checks using AWS Glue's quality modules will help maintain trust in data-driven decisions.


Tools and Technologies

•	AWS Services: S3 (storage), Glue (ETL), Glue DataBrew (cleaning), Glue Crawler (schema discovery), Athena (SQL querying), CloudWatch and CloudTrail (monitoring), KMS (encryption)

•	File Formats: CSV (for general access), Parquet (for optimized analytics with partitioning)

•	Security: Data was protected using AWS KMS encryption, and versioning/replication was used for resilience and recovery

Conclusion

This descriptive analysis offers a comprehensive understanding of Vancouver’s painted bikeway infrastructure. Through structured profiling, cleaning, and visualization, the project highlights key trends in how bikeways have evolved over time and how they are distributed by type, status, and location. These insights empower policymakers, engineers, and urban planners to make evidence-based decisions that enhance the safety, equity, and efficiency of the city’s cycling infrastructure.
Furthermore, the methodologies and AWS architecture implemented here establish a solid foundation for advanced analytics, predictive modeling, and scalable reporting in future transportation projects.



