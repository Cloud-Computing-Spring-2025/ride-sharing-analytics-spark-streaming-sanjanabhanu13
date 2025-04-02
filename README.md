# ride-sharing-spark-streaming
Spark structured streaming example
#  Ride Sharing Analytics with Spark Structured Streaming

This project demonstrates real-time analytics on simulated ride-sharing data using **Apache Spark Structured Streaming**. It includes parsing data from a socket, performing driver-level and time-windowed aggregations, and exporting results to CSV files.

---

##  Project Overview

In this mini-project, you will:
- Simulate streaming ride data with a custom `data_generator.py` script.
- Read, parse, and process streaming data using PySpark.
- Perform real-time aggregations by driver ID and time windows.
- Output results to CSV in a structured folder format.

##  How to Run the Project

 Open two terminals in your workspace.
 Before starting the assignment, ensure the following tools are installed:

 **Python 3.x**  
   - [Download Python](https://www.python.org/downloads/)  
   - Verify installation:
     ```bash
     python --version
     ```

2. **PySpark**
   - Install using pip:
     ```bash
     pip install pyspark
     ```

3. **Faker** (for optional data simulation)
   - Install using pip:
     ```bash
     pip install faker

     ### **2. Running the Tasks**

Run each script in a separate terminal after starting the simulator.

```bash
python task1.py
python task2.py
python task3.py

### **Terminal 1**  (start the data stream):
python data_generator.py

Task 1: Ingest & Parse Streaming Data
**Objective**
Read data from a socket (localhost:9999).

Parse incoming JSON strings into structured format.

Save parsed batches to CSV.

**Command**:

python task1.py

## **Dataset Structure (Simulated)**

| Field        | Type    | Description                        |
|--------------|---------|------------------------------------|
| trip_id      | String  | Unique ID for each ride            |
| driver_id    | String  | ID of the driver                   |
| distance_km  | Float   | Trip distance in kilometers        |
| fare_amount  | Float   | Total fare for the trip            |
| timestamp    | String  | Ride start time (YYYY-MM-DD HH:MM:SS) |


**Output**:

CSV files will be saved in:output/task1_csv/batch_X/

+---------------------------------------+-------------------+--------------+-------------+---------------+
| trip_id                               | driver_id        | distance_km  | fare_amount  | timestamp    |
+---------------------------------------+-----------------+---------------+--------------+---------------|
| fc98e95e-c47e-453c-8b99-35070c849bcc  |  5,40.97         | 113.2        | 2025-04-01   |18:50:13        |
+---------------------------------------+-----------------+---------------+--------------+----------------+ 



**Task 2: Driver-Level Aggregation**
**Objective**
1)Group trips by driver_id.                                                                     

2)Compute:

      -->Total fare

      -->Average distance

Output the aggregated results to CSV for each batch.

--> python task2.py
**output**
+---------+----------+------------+
|driver_id|total_fare|avg_distance|   
+---------+----------+------------+
|29       |7.55      | 28.05      |
+---------+----------+------------+
|87       |93.03     |17.94       |
+---------+----------+------------+


**Task 3: Windowed Time-Based Analytics**
 **Objective**:
Convert timestamp to TimestampType as event_time.

Add a watermark of 2 minutes.

Perform a 5-minute windowed aggregation on fare_amount (sliding every 1 minute).

Output the sum of fares within each window.

-->python task3.py

Output
CSV files will be saved under: output/task3/batch_1/                 
+------------------------+---------------------------------+---------------------------------- +
|      total_fare        |window_start                      |    window_end                    |
+------------------------+---------------------------------+---------------------------------  +
| 162.26                 | 2025-04-02T02:22:00.000Z|         | 2025-04-02T02:27:00.000Z         |
+------------------------+---------------------------------+---------------------------------- +

## **Conclusion**

This assignment gives hands-on experience in real-time streaming analytics, simulating real-world ride data. It prepares for data engineering roles working with tools like Apache Spark, Kafka, and streaming data pipelines.

