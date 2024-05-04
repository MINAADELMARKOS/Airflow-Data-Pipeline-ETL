# Airflow Data Pipeline ETL

## Project Overview
Welcome to the ETL Data Pipeline project using Airflow! This repository contains an ETL data pipeline project that leverages Airflow DAGs (Directed Acyclic Graphs) to extract employee data from PostgreSQL schemas, load it into an AWS S3 Data Lake, transform it using Python scripts, and finally load it into a Snowflake data warehouse using Slowly Changing Dimension (SCD) type 2.

## Table of Contents
- [Project Details](#project-details)
- [Tools and Technologies](#tools-and-technologies)
- [Project Files](#project-files)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Project Details
The project uses Airflow DAGs to orchestrate an hourly ETL process for extracting employee data from HR and Finance PostgreSQL schemas and loading it into a Snowflake data warehouse to maintain historical employee salary changes.

![New Project](https://github.com/Dina-Hosny/ETL-Data-Pipeline-using-AirFlow/assets/46838441/32769201-4ecb-487a-b999-bbed1a851c2b)

### Project Steps
1. **Airflow DAG**: Implement an Airflow DAG that runs hourly and uses the TaskFlow approach to pass outputs between tasks.
  
2. **Data Extraction**: Implement two tasks that use the `SqlToS3Operator` to extract data from PostgreSQL schemas and load it into AWS S3 buckets in CSV format. One task extracts HR data, and the other extracts Finance data.

3. **Data Transformation**: Implement two tasks that use Python functions on the extracted data to retrieve the IDs of new records for insertion and records that require updates to apply the Slowly Changing Dimension (SCD) type 2 concept.

4. **Data Loading**: Load the transformed data into the Snowflake data warehouse table.

5. **Branching Logic**: The Airflow DAG includes Python functions using the `BranchPythonOperator` to check for new records to insert or update and avoid errors.

## Tools and Technologies
- **Apache Airflow**: Workflow orchestration platform for managing ETL processes.
- **Python**: Used for data transformation scripts and Airflow tasks.
- **Pandas**: Data manipulation and analysis library for Python.
- **PostgreSQL**: Source database for extracting HR and Finance data.
- **Snowflake**: Target data warehouse for storing historical data.
- **AWS S3**: Data Lake for storing extracted data in CSV format.
- **ETL**: Extract, Transform, Load process for managing data.
- **SCD**: Slowly Changing Dimension concept for tracking data history.

## Project Files
- **Dags**: Contains the Airflow DAG definition.
- **Includes**: Contains SQL and Python scripts used in the Airflow DAG.
- **Output**: Contains screenshots or other artifacts from the Airflow DAG output.

## Installation
1. Clone the repository:
    ```shell
    git clone https://github.com/yourusername/airflow-data-pipeline-etl.git
    cd airflow-data-pipeline-etl
    ```

2. (Optional) Create a virtual environment and activate it:
    ```shell
    python3 -m venv venv
    source venv/bin/activate
    ```

3. Install the required dependencies:
    ```shell
    pip install -r requirements.txt
    ```

4. Set up your environment variables for PostgreSQL, Snowflake, and AWS S3 access credentials.

## Usage
- Set up Airflow with the necessary configurations for your environment.
- Run the Airflow DAG to execute the ETL process.
- Monitor the DAG execution in the Airflow web interface.

## Contributing
Contributions are welcome! Feel free to:
- Fork the repository and create a pull request with your changes.
- Suggest improvements or provide feedback.
- Follow the code style and guidelines provided in the repository.

## License
This project is licensed under the [MIT License](LICENSE).

---
![Screenshot 2023-05-14 191951](https://github.com/Dina-Hosny/ETL-Data-Pipeline-using-AirFlow/assets/46838441/eee98f52-db18-4022-bce0-6c38fb7dadd2)
Happy analyzing! If you have any questions or feedback, please feel free to open an issue on GitHub.


