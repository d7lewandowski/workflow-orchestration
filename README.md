# Workflow Orchestration – NYC Taxi Data (Kestra + GCP)

This project implements a **Kestra-based workflow orchestration setup** for ingesting **NYC Taxi CSV datasets** into **Google Cloud Platform (GCP)**, specifically **Google Cloud Storage (GCS)** and **BigQuery**.  
It is designed to be **fully runnable locally** using **Docker Compose**, making it suitable for development, testing, and learning purposes.

---

## Project Overview

The goal of this project is to demonstrate how to:
- Orchestrate ETL pipelines using **Kestra**
- Parameterize and manage GCP configuration using **Kestra KV store**
- Ingest large CSV datasets into **GCS**
- Create and incrementally merge tables in **BigQuery**
- Schedule workflows with timezone-aware triggers

---

## Key Components

### Orchestration Flows

- **`zoomcamp.gcp_kv`**  
  Stores core GCP configuration in Kestra’s KV store:
  - GCP project ID
  - GCP location
  - GCS bucket name
  - BigQuery dataset name

- **`zoomcamp.gcp_setup`**  
  Bootstraps GCP resources:
  - Creates the GCS bucket
  - Creates the BigQuery dataset (if not already present)

- **`zoomcamp.gcp_taxi_scheduled`**  
  A scheduled ETL workflow that:
  - Downloads NYC Taxi CSV files
  - Uploads raw data to GCS
  - Creates or merges tables in BigQuery
  - Supports multiple taxi types (e.g. yellow, green)
  - Uses parameterized year and month inputs

---

### Local Runtime Environment

The project can be run locally using **Docker Compose**, which includes:

- **Kestra** – workflow orchestration engine  
- **PostgreSQL** – metadata database for Kestra  
- **pgAdmin** – optional UI for managing Postgres  

Key file:
- **`docker-compose.yml`** — defines and runs all required services

---

- **`.gitignore`**  
  Standard ignore rules for local and environment-specific files.

---

## Use Cases

- Learning workflow orchestration with Kestra
- Practicing cloud-based ETL pipelines
- Preparing data engineering foundations for BigQuery-based analytics
- Running reproducible data pipelines locally before deploying to the cloud

---


