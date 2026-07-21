### Ojong Bessong NKONGHO

Final-year BSc Computer Science & Engineering, DSTI School of Engineering, Paris. Pre-admitted to the MSc Data Engineering and AI, September 2026.
I build data systems that reach production. Two of them crashed this year. I diagnosed and fixed both in production. The READMEs document what broke and why, because that is the part worth reading.
Open to a Data Engineering internship immediately and an apprenticeship from September 2026. Also open to backend engineering roles.

### Projects

### [Weather API](https://github.com/OjongBessongNKONGHO/weather-api)
FastAPI service on PostgreSQL, authenticated and rate-limited. Full async SQLAlchemy 2.0 migration with psycopg3, which surfaced a production crash from a pool misconfiguration and a separate CI failure from SQLite rejecting pool arguments it does not support. Both fixed. Instrumented with Prometheus and Grafana using a custom ASGI middleware that records request duration by route template rather than raw path. The distinction matters: raw paths create one time series per city name, per typo, per scanner probe. Alembic migrations, structured logging, database latency on the health endpoint. 41 tests.

### [Spark Streaming Pipeline](https://github.com/OjongBessongNKONGHO/spark-streaming-pipeline)
Kafka into Spark Structured Streaming into Delta Lake on S3, dbt transformations on top, Airflow orchestrating, Terraform provisioning the AWS infrastructure. Batch analysis runs in its own Docker container, not inside the Airflow scheduler process, so a broken dependency cannot take down the orchestrator. Local development runs entirely against MinIO so the full pipeline works without real AWS credentials. Includes a Delta Lake maintenance job that compacts small files produced by streaming micro-batches and physically removes orphaned data files. Five production incidents documented in the README. 56 tests.

### [Kafka Streaming Pipeline](https://github.com/OjongBessongNKONGHO/kafka-streaming-pipeline)
Real-time pipeline for 21 cities across 6 continents. Dead letter queue with a standalone reprocessing script and a monitoring script that reports message counts, error breakdowns and oldest unresolved message age. Avro schemas with BACKWARD compatibility enforced via Confluent Schema Registry. The registry rejects breaking type changes before they reach consumers. Confluent wire format serializer with schema ID caching so the registry is only contacted once per process. Data contract layer validates business rules at the pipeline entry point: temperature within earthly range, humidity as a percentage, timestamps not in the future. 90 tests.

### [AWS Data Platform](https://github.com/OjongBessongNKONGHO/aws-data-platform)
44 AWS resources across five independent Terraform modules: networking, compute, storage, database, monitoring. VPC with public and private subnets, RDS PostgreSQL in the private subnet, AES256-encrypted S3 data lake, CloudWatch alarms wired to SNS. S3 VPC Gateway Endpoint with a policy restricting access to the data lake bucket only. Without that restriction, the endpoint allows traffic to any S3 bucket in any account, which is a data exfiltration path. A boto3 script verifies teardown is actually complete by querying AWS by resource tag after terraform destroy, since a destroy can report success while a resource silently fails to delete. 16 tests.

### [DuckDB Analytics](https://github.com/OjongBessongNKONGHO/duckdb-analytics)
14 OLAP queries covering anomaly detection, temperature-humidity correlation, hourly patterns, data freshness monitoring and month-over-month trend analysis. Eight data quality checks run before any query executes. Parquet export with Snappy compression via PyArrow, Click CLI, APScheduler for hourly runs. 37 tests.

### [Weather ETL Pipeline](https://github.com/OjongBessongNKONGHO/weather-etl-pipeline)
Airflow DAG with a validation task between transform and load. Seven quality checks. If one fails, the DAG fails. Bad data does not reach PostgreSQL. 37 tests.

### Stack
Python, SQL, FastAPI, SQLAlchemy 2.0 async, Pydantic v2, fastavro, Kafka, Spark, Airflow, dbt, Delta Lake, DuckDB, Prometheus, Grafana, AWS, Terraform, Docker, GitHub Actions, PostgreSQL, psycopg3

Previously Data Analyst Intern at Boston University School of Medicine, processing bulk RNA-seq datasets in R on a Linux HPC cluster. Reproducibility requirements were strict enough that cutting corners showed up immediately in the results.

📍 Paris · nkongho.ojong-bessong@edu.dsti.institute · LinkedIn
