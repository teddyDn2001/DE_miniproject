# DE_miniproject
This is a small project since i self taught on coursera. It revolves around using pipeline related tools like apache spark, apache kafka and apache airflow.
# Real-Time ETL Pipeline with Kafka, Spark, and Airflow

## 📌 Project Overview
This project demonstrates a **simple real-time ETL pipeline** using:
- **Kafka** for streaming data ingestion
- **Spark Structured Streaming** for data processing
- **Apache Airflow** for workflow orchestration
- **Docker Compose** to containerize all services

It simulates real-time user data generation, processes the data with Spark, and stores the filtered results in **Parquet** files.

---

## 🛠️ Technologies Used
- **Apache Kafka** - Message broker for real-time data streaming
- **Apache Spark** - Real-time data processing engine
- **Apache Airflow** - Workflow scheduler and orchestrator
- **Docker Compose** - Container orchestration
- **Python** - Programming language (for Kafka producer & Airflow DAGs)

---

## 📈 Architecture Diagram
+-----------------+ +-----------------+ +-------------------------+ | Kafka Producer | --> | Kafka Broker | --> | Spark Structured Streaming | +-----------------+ +-----------------+ +-------------------------+ | +-----------------+ | Parquet Storage | +-----------------+

## 🚀 How it Works
1. **Kafka Producer** (`kafka_producer.py`) generates fake user data (`name`, `age`, `email`) every 2 seconds.
2. **Kafka Broker** receives and stores the messages in `user_topic`.
3. **Spark Structured Streaming** (`spark_etl.py`) reads messages from Kafka, parses JSON, filters users with `age > 18`, and writes them to **Parquet files**.
4. **Airflow** triggers and manages the Spark job execution periodically.

---

## 📂 Project Structure
my_etl_project/ 
├── docker-compose.yml 
├── kafka_producer.py  
├── spark_app/ │ 
  └── spark_etl.py 
├── dags/ │ 
  └── etl_spark_dag.py └── data/ └── (output parquet files)

## ⚙️ Setup Instructions

### 1. Clone the Repository
bash
git clone https://github.com/your-username/my_etl_project.git
cd my_etl_project

2. Start All Services
bash
Sao chép
Chỉnh sửa
docker-compose up
Services started: Zookeeper, Kafka, Spark, Airflow

3. Run Kafka Producer
In a separate terminal:

bash
Sao chép
Chỉnh sửa
python kafka_producer.py
This script will continuously send fake user data to Kafka topic user_topic.

4. Access the Interfaces
Airflow UI: http://localhost:8080

Spark UI: http://localhost:8081

Kafka: running on port 9093 (mapped to internal 9092)

📊 Example Output
Parquet files will be saved under the /data/ folder after Spark processes and filters the user data.

Each row contains

name	age	email
Linh	24	user87@example.com
Huy	27	user12@example.com
📝 Notes
spark_streaming.py file is present but not used. Main Spark code is in spark_app/spark_etl.py.

Ensure your Python environment has kafka-python installed:

bash
pip install kafka-python

📢 Future Improvements
Add Watermarking for late data handling
Add retry mechanisms for Kafka Producer
Improve Airflow DAGs (task-level retries, alerting)
Add Grafana dashboard for real-time monitoring

👨‍💻 Author
Jun | Data Engineer Enthusiast


