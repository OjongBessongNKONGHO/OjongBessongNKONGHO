# Ojong Bessong NKONGHO

Final-year BSc Computer Science & Engineering, DSTI School of Engineering, Paris. Pre-admitted to the MSc Data Engineering and AI, September 2026.

Six data engineering systems built from scratch this year. All of them run. All of them have tests. The READMEs document what broke during deployment and how I fixed it — because that is the part that actually takes time.

**Open to a Data Engineering internship from 6 July 2026, and an apprenticeship from September 2026 — also open to backend engineering roles.**

---

**Live right now:** [Weather API](https://weather-api-production-1781.up.railway.app/docs) — authenticated, rate-limited, deployed on Railway. Authorize with the key in the README and call it.

---

## What I've built

**[Spark Streaming Pipeline](https://github.com/OjongBessongNKONGHO/spark-streaming-pipeline)**
Kafka → Spark Structured Streaming → Delta Lake on S3, dbt on top, Airflow orchestrating, Terraform provisioning the AWS infrastructure. Deployed on EC2. Five production incidents documented in the README — S3AFileSystem ClassNotFoundException, AMI drift forcing instance replacement on every terraform apply, environment variables not propagating from .env into docker-compose. 46 tests.

**[AWS Data Platform](https://github.com/OjongBessongNKONGHO/aws-data-platform)**
42 AWS resources in one terraform apply. VPC, private RDS, encrypted S3 data lake, five CloudWatch alarms wired to SNS. Five independent Terraform modules — networking, compute, storage, database, monitoring.

**[Kafka Streaming Pipeline](https://github.com/OjongBessongNKONGHO/kafka-streaming-pipeline)**
Three-topic architecture separating raw, validated and invalid messages. Dead letter queue with a standalone reprocessing script that preserves the original Kafka offset so nothing is lost and everything is traceable. 44 tests.

**[DuckDB Analytics](https://github.com/OjongBessongNKONGHO/duckdb-analytics)**
12 OLAP queries — anomaly detection, temperature-humidity correlation, hourly patterns. Eight data quality checks run before any query touches the data. 35 tests.

**[Weather ETL Pipeline](https://github.com/OjongBessongNKONGHO/weather-etl-pipeline)**
Airflow DAG with a validation task between transform and load. Seven quality checks. If one fails, the DAG fails — bad data does not reach PostgreSQL. 37 tests.

**[Weather API](https://github.com/OjongBessongNKONGHO/weather-api)**
FastAPI, PostgreSQL, deployed live. The README documents the exact 500 error I hit and how I traced it to a missing SQLAlchemy relationship. 38 tests, four of which mock the OpenWeatherMap HTTP layer entirely.

---

## Stack

Python, SQL, FastAPI, SQLAlchemy, Pydantic v2 · Kafka, Spark, Airflow, dbt, Delta Lake, DuckDB · AWS, Terraform, Docker, Railway, GitHub Actions · PostgreSQL

---

Previously at Boston University School of Medicine, processing bulk RNA-seq datasets in R on a Linux HPC cluster. Reproducibility requirements there were strict enough that cutting corners showed up immediately in the results.

📍 Paris · nkongho.ojong-bessong@edu.dsti.institute · [LinkedIn](http://www.linkedin.com/in/nkongho-ojong)
