# ecommerceproject
Ecommerce Project Assessment PEI

## Tech Stack
- Databricks
- PySpark
- Delta Lake
- Python unittest
- SQL

## Architecture Overview
- **Raw Layer**  
  Ingests source datasets from different file systems into Databricks volumes with basic cleansing and normalization.
- **Enriched Dimensions**  
  - `dim_customers` - customer dimension attributes with SCD implemented
  - `dim_products` - product dimension attributes with SCD implemented
- **Fact Table**  
  - `orders_enriched` - orders facts enriched with customer and product dimension attributes
- **Analytics Layer**  
  - Profit aggregations for business analysis

## Pipeline Execution
**`unit_test`** notebook acts as the pipeline entry point. Executing this notebook triggers the entire pipeline in the following sequence:       
**`unit_test → serving → enrich_table → raw_ingestion → utils`**

## Performance & Optimization
Considering the data size, below optimization technique is considered.
- Adaptive Query Execution enabled
- Delta Auto Optimize is enabled to automatically reduce small file creation problem.
- No partitioning, Z-ORDER, or liquid clustering intentionally due tiny dataset

