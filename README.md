
## Weather ETL Pipeline with Apache Airflow and PostgreSQL

This project demonstrates an ETL (Extract, Transform, Load) pipeline built with Apache Airflow to fetch real-time weather data from the Open-Meteo API, transform it into a structured format, and store it in a PostgreSQL database. The pipeline is containerized using Docker for ease of deployment and management.

## Key Features

* Automated Weather Data Extraction: Retrieves weather metrics such as temperature, windspeed, and weather codes for a specified location (London).
* Data Transformation: Processes and structures the raw API response for efficient storage and analysis.
* Database Integration: Stores transformed data in a PostgreSQL database, creating the table dynamically if it does not exist.

## Prerequisites

* Apache Airflow: Installed and configured.
* Docker: Installed for containerized deployment.
* PostgreSQL: Database running in a Docker container (configured in docker-compose.yml).
* Airflow Connections:
     * PostgreSQL: PostgreSQL: Set up in Airflow with connection type Postgres.
     * HTTP: Set up in Airflow for Open-Meteo API.
* PostgreSQL: Set up in Airflow with connection type Postgres.
* HTTP: Set up in Airflow for Open-Meteo API.

### Setup and Usage

## 1. Clone the Repository

git clone <repository_url>

cd <repository_directory>

## 2. Start Services

Run the following command to start PostgreSQL via Docker:

docker-compose up -d


For Airflow, use Astro CLI to start your Airflow environment:

astro dev start


## 3. Configure Airflow Connections

* PostgreSQL Connection:
   * Connection ID: postgres_default
   * Host: postgres_db
   * Port: 5432
   * User: postgres
   * Password: postgres
   * Database: postgres
* HTTP Connection:
   * Connection ID: open_meteo_api
   * Host: https://api.open-meteo.com

## 4. Deploy the DAG

Place the weather_etl_pipeline.py file in Airflow's dags/ directory and activate the DAG from the Airflow UI.

## 5. Monitor the Pipeline

Monitor the pipeline's execution and logs via the Airflow UI.

## Outputs

* Database Table: weather_data


## Sample Output Data in `weather_data` Table  

| **latitude** | **longitude** | **temperature** | **windspeed** | **winddirection** | **weathercode** | **timestamp**          |  
|--------------|---------------|-----------------|---------------|-------------------|-----------------|------------------------|  
| 51.5074      | -0.1278       | 12.5            | 10.2          | 180               | 1               | 2025-01-19 10:00:00    |  
| 51.5074      | -0.1278       | 11.0            | 12.8          | 220               | 2               | 2025-01-19 11:00:00    |  
| 51.5074      | -0.1278       | 10.2            | 8.5           | 140               | 3               | 2025-01-19 12:00:00    |  
| 51.5074      | -0.1278       | 9.8             | 6.4           | 200               | 2               | 2025-01-19 13:00:00    |  
| 51.5074      | -0.1278       | 8.9             | 5.2           | 150               | 1               | 2025-01-19 14:00:00    |  



## Tools Used

* Apache Airflow: Workflow orchestration.
* PostgreSQL: Data storage.
* Open-Meteo API: Weather data provider.
* Docker: Containerization.
* DBeaver: Database management tool.
