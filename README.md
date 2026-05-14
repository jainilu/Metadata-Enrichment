# Metadata Enrichment and Data Quality Prototype


### Overview
This project is a Databricks-based prototype that profiles ecommerce tables, enriches column metadata, detects PII and sensitive fields, recommends data quality rules, and executes those rules to produce a table-level data quality scorecard.

### Why I Built This
The project was designed to simulate an internal data platform utility that helps data engineers onboard new tables faster by automatically generating first-pass metadata and quality recommendations.

### Dataset
Synthetic ecommerce data was generated for:
- customers
- orders
- products

The dataset intentionally includes scattered quality issues such as invalid emails, malformed phone numbers, duplicate IDs, null identifiers, invalid categories, negative amounts, and out-of-range numeric values.

### Architecture
1. Generate synthetic ecommerce data
2. Save raw data and bronze Delta tables
3. Profile column-level metadata
4. Infer semantic column types
5. Detect PII/sensitive fields and assign governance tags
6. Recommend data quality rules
7. Execute recommended rules
8. Generate data quality scorecard

### Tech Stack
- Databricks
- PySpark
- Delta Lake
- Unity Catalog Volumes
- SQL
- Python

### Key Features
- Column profiling
- Semantic type inference
- PII and sensitive-field detection
- Governance tagging
- Data quality rule recommendation
- Rule execution engine
- DQ scorecard summary

### Example Rules Generated
- email must match a valid email format
- phone number must match expected format
- age must be between 0 and 120
- order totals must be non-negative
- order status must be in an accepted list
- IDs should not be null
- likely primary keys should be unique

### Results
The scorecard identified issues across customers, orders, and products, including malformed PII fields, invalid categorical values, negative financial amounts, duplicate IDs, and missing key fields.

### Future Improvements
- Add referential integrity checks between orders and customers
- Integrate live LLM-based description generation
- Use Faker library to generate massive amounts of data
- Add dashboard visualizations for ongoing monitoring