# Apple Data Engineering Pipeline

This project provides a comprehensive example of a production-ready data engineering workflow. It demonstrates best practices in data extraction, transformation, and loading (ETL) processes, ensuring data integrity, scalability, and efficiency. The workflow is designed to be robust and maintainable, reflecting real-world scenarios encountered in modern data engineering environments using Python and Apache Spark.

## Overview

The pipeline is organized into several modules:

- **Reader/Extractor:** Reads data from various sources (e.g., CSV, Parquet, Delta files) using a factory pattern to create the appropriate reader object.
- **Transformer:** Applies data transformation logic to clean, reshape, or enrich the data as needed.
- **Loader:** Writes the transformed data to the desired destination (which could be a database, file system). A factory approach is used here as well to select the appropriate loader.

The main orchestration file `apple_data_engineering` ties together the above components, triggering the extraction, transformation, and loading steps in sequence.

## Project Structure

Below is an outline of the project’s file structure along with a brief description of each module:

- **apple_data_engineering**
  - Main script that orchestrates the entire data pipeline.
  - Initializes the pipeline components and runs the ETL process.
  
- **reader_factory**
  - Contains the logic to create appropriate reader objects based on the data type or file format.
  - Implements the factory design pattern for data source ingestion.
  
- **extractor**
  - Implements the extraction logic.
  - Uses the reader objects (created via `reader_factory`) to load data from the specified sources.
  
- **transform**
- Contains transformation functions to process and clean the extracted data.
    -  Customers who purchased AirPods after buying an iPhone.
    - Also customers who purchased only iPhones and AirPods. 
  
- **loader**
  - Implements the logic to load or write the transformed data to a target destination.
  - Handles connections and writes to target systems (e.g., databases or file systems).
  
- **loader_factory**
  - Provides a factory method to select and instantiate the correct loader based on the target data store.
  - Promotes flexibility and scalability by easily allowing additional loader types to be added.


## Setup and Installation

1. **Create a SQL Warehouse Cluster in Databricks:**  
    Set up a SQL warehouse cluster to handle compute resources for your data pipeline.

2. **Create a Catalog:**  
    In Databricks, create a catalog named `apple`. This catalog will be used to organize and store your data assets.

3. **Create Volumes:**  
    - Within the `apple` catalog, create a volume named `tables` to store your datasets.
    - For the final data outputs, create another volume named `output` to store the processed results.

These steps ensure your data is organized and accessible throughout the ETL workflow.

### ETL Workflow
1. **Extract:** Data is read from the source using the reader factory, which instantiates the correct data source (such as a CSV reader).
2. **Transform:** The raw data is then processed and transformed according to business logic defined in the transformation module.
3. **Load:** Finally, a loader (obtained from the loader factory) writes the transformed data to the target destination.

### Prerequisites
- **Python 3.7+**
- **Apache Spark**# apple-data-engineering
