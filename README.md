# SupplyChain Manufacturing — Big Data Pipeline
### ISM 6562 | Team: The Leftside Undergrads

## Team Members
- Aisha Nomani
- An Chu
- Aurelia Vo
- Sai Han Shan Pha
- Mohammed Aljumai

## Project Scenario
We are acting as data engineers consulting for **PrecisionParts Manufacturing**. We designed and built a complete big data pipeline covering data storage, batch transformation, real-time streaming, and pipeline orchestration.

## Architecture Overview
Our pipeline is built on four layers:
1. **Store** (Stage 1) — HDFS data lake with landing, curated, and analytics zones
2. **Transform** (Stage 2) — PySpark batch processing to clean, join, and aggregate data
3. **Stream** (Stage 3) — Kafka + Spark Structured Streaming for real-time machine telemetry
4. **Orchestrate** (Stage 4) — Airflow DAGs for scheduling, quality gates, and monitoring

### Steps
1. Clone the repository:
```bash
   git clone https://github.com/aishanomani/The_Leftside_Undergrads_Final
   cd The_Leftside_Undergrads_Final
```

2. Downloaded the data:
```bash
   mkdir -p data/raw
```
   Download all files from: https://github.com/prof-tcsmith/ism6562s26-class/tree/main/final-projects/data/08-supplychain-manufacturing

   Place them in `data/raw/`

3. Start the full infrastructure:
```bash
   docker compose up -d
```

4. Create Airflow admin user:
```bash
   winpty docker exec -it airflow-webserver airflow users create \
     --username airflow --password airflow \
     --firstname Air --lastname Flow \
     --role Admin --email airflow@airflow.com
```

5. Access the services:
   - Airflow: http://localhost:8082 (user: airflow / pass: airflow)
   - Spark UI: http://localhost:8081
   - HDFS UI: http://localhost:9870
   - Kafka UI: http://localhost:8080

6. Run the Kafka producer:
```bash
   cd producers
   python event_producer.py
```

## Data Sources
All datasets are pre-generated and available in the course data repository: https://github.com/prof-tcsmith/ism6562s26-class/tree/main/final-projects/data/08-supplychain-manufacturing 

| File | Description |
|------|-------------|
| `production-lines.csv.gz` | Production line output and shift data |
| `inventory-levels.csv.gz` | Stock levels across warehouse locations |
| `equipment-sensors.csv.gz` | Real-time machine sensor readings |
| `quality-inspections.json.gz` | Defect inspection results per batch |
| `supplier-performance.json.gz` | Supplier delivery and quality scores |

## Key Findings
*To be updated*

## Repository Structure
The_Leftside_Undergrads_Final/
├── README.md
├── docker-compose.yml
├── hadoop.env
├── data/
│   └── raw/                        
├── notebooks/
│   ├── 01-data-lake-setup.ipynb
│   ├── 02-spark-transforms.ipynb
│   ├── 03-streaming-pipeline.ipynb
│   └── 04-exploration.ipynb
├── dags/
│   ├── batch_pipeline.py
│   └── streaming_monitor.py
├── producers/
│   └── event_producer.py
├── report/
│   ├── final-report.pdf
│   └── architecture-diagram.png
└── presentation/
└── slides.pdf