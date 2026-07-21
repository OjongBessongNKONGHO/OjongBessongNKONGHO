Ojong Bessong NKONGHO

Final-year BSc Computer Science & Engineering at DSTI School of Engineering, Paris. Pre-admitted to the MSc Data Engineering and AI, September 2026.
This year I built six data engineering systems from scratch. Two of them crashed in production. I fixed both. The READMEs say what broke and why because that is the part worth documenting.
Available for a Data Engineering internship immediately, and an apprenticeship from September 2026.

Projects

Weather API
FastAPI service on PostgreSQL, authenticated and rate-limited. I migrated the database layer to async SQLAlchemy 2.0 with psycopg3, which surfaced a production crash I traced to a pool misconfiguration and a separate CI failure caused by SQLite rejecting pool arguments it doesn't support. Both fixed. I then instrumented the service with Prometheus and Grafana, writing a custom ASGI middleware that records request duration by route template rather than raw path — the difference matters because raw paths create one time series per city name, per typo, per scanner probe. 41 tests.

Kafka Streaming Pipeline
Real-time pipeline for 21 cities. Messages that fail validation go to a dead letter queue with a monitoring script and a reprocessing script. I added Avro serialization with BACKWARD compatibility enforced by Confluent Schema Registry, the registry rejects breaking changes before they reach consumers. The serializer implements the Confluent wire format so any compatible consumer can identify the schema from the message bytes. I also built a data contract layer that validates business rules at the pipeline entry point: temperature within earthly range, humidity as a percentage, timestamps not in the future. 90 tests.

Spark Streaming Pipeline
Kafka into Spark Structured Streaming into Delta Lake, dbt transformations on top, Airflow orchestrating the whole thing. Batch analysis runs in its own Docker container rather than inside the Airflow scheduler so a broken dependency in one cannot affect the other. I wrote a Delta Lake maintenance job that compacts the small files streaming creates and physically removes orphaned data files. Local development runs against MinIO so nothing needs real AWS credentials. 56 tests.

AWS Data Platform
44 AWS resources across five Terraform modules. I added an S3 VPC Gateway Endpoint with a policy that restricts it to the data lake bucket only. Without the policy, the endpoint allows traffic to any S3 bucket in any account, which is a data exfiltration path. I also wrote a boto3 script that verifies teardown is actually complete by querying AWS by resource tag after terraform destroy, because destroy can report success while a resource silently fails to delete. 16 tests.

DuckDB Analytics
14 OLAP queries on weather data. Eight data quality checks run before any query executes. Results export to Parquet with Snappy compression. 37 tests.

Weather ETL Pipeline
Hourly Airflow pipeline. A validation task sits between transform and load. If it fails, the DAG fails. Bad data does not reach PostgreSQL. 37 tests.


Stack
Python, SQL, FastAPI, SQLAlchemy 2.0 async, Pydantic v2, fastavro, Kafka, Spark, Airflow, dbt, Delta Lake, DuckDB, Prometheus, Grafana, AWS, Terraform, Docker, GitHub Actions, PostgreSQL, psycopg3

Previously Data Analyst Intern at Boston University School of Medicine, processing bulk RNA-seq datasets in R on a Linux HPC cluster.

📍 Paris, nkongho.ojong-bessong@edu.dsti.institute, LinkedIn


