# Real-Time Data Streaming | End-to-End Data Engineering Pipeline

An end-to-end data engineering project demonstrating the integration of modern data technologies to build a complete data ingestion, streaming, processing, and storage pipeline.

The system leverages Apache Airflow for workflow orchestration, Apache Kafka for event streaming, Apache Spark for distributed data processing, and Apache Cassandra for storing processed data. The entire infrastructure is containerized using Docker and managed through Docker Compose.

## Table of Contents

- [Overview](#overview)
- [System Architecture](#system-architecture)
- [Pipeline Workflow](#pipeline-workflow)
- [Technology Stack](#technology-stack)
- [Key Features](#key-features)
- [Getting Started](#getting-started)
- [Learning Objectives](#learning-objectives)

## Overview

This project implements a complete data engineering pipeline that collects data from an external API, orchestrates ingestion workflows, streams events through a distributed messaging system, processes incoming records, and stores the resulting data in a NoSQL database.

The architecture integrates multiple services into a unified environment, demonstrating how different components of a modern data engineering ecosystem interact to support scalable data processing.

## System Architecture

The pipeline consists of several interconnected components, each responsible for a specific stage of the data lifecycle.

### Architecture Components

**1. Data Source**
- Uses the Random User Generator API to retrieve randomly generated user information.
- Provides an external data source for demonstrating API-based ingestion.

**2. Apache Airflow**
- Orchestrates and schedules data ingestion workflows.
- Manages task dependencies and execution.
- Coordinates the extraction and loading of API data into PostgreSQL.

**3. PostgreSQL**
- Stores the initially extracted API records.
- Acts as the source database for subsequent streaming operations.

**4. Apache Kafka and Zookeeper**
- Kafka handles event streaming and message distribution.
- Zookeeper provides coordination for the Kafka infrastructure.

**5. Schema Registry and Control Center**
- Schema Registry manages and validates Kafka message schemas.
- Control Center provides monitoring and management capabilities for the Kafka environment.

**6. Apache Spark**
- Consumes incoming Kafka streams.
- Performs distributed data processing and transformations.
- Uses a master-worker architecture to distribute processing workloads.

**7. Apache Cassandra**
- Stores the processed data.
- Provides a distributed NoSQL storage layer for downstream data access.

### Architecture Diagram

![Data Engineering Architecture](https://github.com/airscholar/e2e-data-engineering/blob/main/Data%20engineering%20architecture.png)

## Pipeline Workflow

The complete data pipeline follows this execution sequence:

1. **Data Extraction:** Airflow triggers a Python-based ingestion task that retrieves user information from the external API.
2. **Initial Storage:** Extracted records are loaded into PostgreSQL.
3. **Change Streaming:** Kafka captures and distributes the relevant data from the source database.
4. **Message Management:** Schema Registry manages message schemas, while Kafka handles event distribution.
5. **Stream Processing:** Apache Spark consumes Kafka messages and performs the required transformations.
6. **Data Persistence:** Processed records are written into Apache Cassandra for persistent storage.

## Technology Stack

| Technology | Purpose |
|---|---|
| Apache Airflow | Workflow orchestration and scheduling |
| Python | Data extraction and application logic |
| Apache Kafka | Distributed event streaming |
| Apache Zookeeper | Kafka coordination |
| Kafka Schema Registry | Message schema management |
| Kafka Control Center | Kafka monitoring and management |
| Apache Spark | Distributed data processing |
| PostgreSQL | Relational database and initial data storage |
| Apache Cassandra | Distributed NoSQL storage |
| Docker | Application containerization |
| Docker Compose | Multi-container infrastructure management |

## Key Features

- **Automated Data Ingestion:** Extract data from external APIs using Python and Airflow.
- **Workflow Orchestration:** Schedule and manage pipeline execution through Airflow DAGs.
- **Event-Driven Architecture:** Use Kafka to distribute data between pipeline components.
- **Distributed Processing:** Process streaming data using Apache Spark.
- **Schema Management:** Manage structured Kafka messages through Schema Registry.
- **Scalable Storage:** Persist processed records using Apache Cassandra.
- **Containerized Infrastructure:** Deploy and manage the entire environment using Docker Compose.
- **Modular Architecture:** Independent services make the pipeline easier to maintain and extend.

## Getting Started

### Prerequisites

Ensure the following tools are installed:

- Docker Desktop
- Docker Compose
- Git

### Installation

**1. Clone the repository**

```bash
git clone YOUR_REPOSITORY_URL