# Ojong Bessong NKONGHO

---

**Live right now:** [Weather API](https://weather-api-production-1781.up.railway.app/docs) — a REST API serving real-time weather data for 21 cities. Click through, authorize with the key in the README, and try it.

Final-year BSc Computer Science & Engineering, DSTI School of Engineering, Paris. Pre-admitted to the MSc Data Engineering and AI, September 2026.

I build production-oriented data pipelines and backend systems with testing, CI/CD and operational monitoring.

**Open to a Data Engineering internship from 6 July 2026, and an apprenticeship from September 2026 — also open to backend engineering roles.**


---

## What I've built

**[Spark Streaming Pipeline](https://github.com/OjongBessongNKONGHO/spark-streaming-pipeline)**
End-to-end lakehouse architecture:
Kafka → Spark Structured Streaming → Delta Lake → dbt → Airflow, deployed on AWS EC2 with Terraform. 46 tests. The most complete system in this portfolio — every layer of a modern data stack, wired together.

**[AWS Data Platform](https://github.com/OjongBessongNKONGHO/aws-data-platform)**
42 AWS resources provisioned with one `terraform apply` — VPC, private RDS, encrypted S3, CloudWatch alarms wired to SNS. Built in modules so each piece is independently testable and reusable.

**[Kafka Streaming Pipeline](https://github.com/OjongBessongNKONGHO/kafka-streaming-pipeline)**
12 cities, 6 continents, three-topic architecture separating raw/validated/invalid messages, dead letter queue with a standalone reprocessing script. 44 tests.

**[DuckDB Analytics](https://github.com/OjongBessongNKONGHO/duckdb-analytics)**
12 OLAP queries over the pipeline data — anomaly detection, correlation analysis, hourly patterns — with 8 data quality checks running before any analysis touches the data. 35 tests.

**[Weather ETL Pipeline](https://github.com/OjongBessongNKONGHO/weather-etl-pipeline)**
Production ETL pipeline orchestrated with Airflow DAG with a dedicated data-quality stage that fails the run before bad data reaches PostgreSQL. 37 tests.

**[Weather API](https://github.com/OjongBessongNKONGHO/weather-api)**
A FastAPI service exposing the data the pipelines collect — authenticated, rate-limited, deployed live on Railway. 38 tests, four of which mock an external API entirely with `unittest.mock` so the suite never touches the network. README documents the exact bug that caused a 500 and how I traced it to a missing SQLAlchemy relationship.

---

## Stack

Python, SQL, FastAPI, SQLAlchemy, Pydantic v2 · Kafka, Spark, Airflow, dbt, Delta Lake, DuckDB · AWS, Terraform, Docker, Railway, GitHub Actions · PostgreSQL, Modern Data Stack,Lakehouse Architecture.

---

Previously a Data Analyst Intern at Boston University School of Medicine, processing RNA-seq genomic datasets in R on a Linux HPC cluster — where I learned that in research, data quality isn't optional, it's the whole job.

📍 Paris · nkongho.ojong-bessong@edu.dsti.institute · [LinkedIn](http://www.linkedin.com/in/nkongho-ojong)
