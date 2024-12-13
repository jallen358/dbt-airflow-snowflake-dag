Overview
========

### Purpose
The purpose of this project is to familiarize myself with deploying DAGs in airflow and the syntax and tools of DBT. 

This project uses Astro which is a connector between DBT and Airflow. To run the code, create your own astro instance using: 
```shell
astro dev start
```
This command will spin up 4 Docker containers on your machine, each for a different Airflow component:

- Postgres: Airflow's Metadata Database
- Webserver: The Airflow component responsible for rendering the Airflow UI
- Scheduler: The Airflow component responsible for monitoring and triggering tasks
- Triggerer: The Airflow component responsible for triggering deferred tasks

You should be able to access the Airflow UI for your local Airflow project. To do so, go to http://localhost:8080/ and log in with 'admin' for both your Username and Password.
You should also be able to access your Postgres Database at 'localhost:5432/postgres'.


Then, add the 'data_pipeline' folder to your dags folder and copy the dbt_dag.py and requirements.txt contents. 
At this point, you should see the dag populate in Airflow. Be patient as it may take a few minutes

### Resources I used:
- dbt [documentation](https://docs.getdbt.com/docs/introduction)
- Astronomer [documentation](https://github.com/astronomer/astronomer-cosmos)

Project Contents
================

Your Astro project contains the following files and folders:

- dags: This folder contains the Python files for your Airflow DAGs. By default, this directory includes one example DAG:
    - `example_astronauts`: This DAG shows a simple ETL pipeline example that queries the list of astronauts currently in space from the Open Notify API and prints a statement for each astronaut. The DAG uses the TaskFlow API to define tasks in Python, and dynamic task mapping to dynamically print a statement for each astronaut. For more on how this DAG works, see our [Getting started tutorial](https://www.astronomer.io/docs/learn/get-started-with-airflow).
- Dockerfile: This file contains a versioned Astro Runtime Docker image that provides a differentiated Airflow experience. If you want to execute other commands or overrides at runtime, specify them here.
- include: This folder contains any additional files that you want to include as part of your project. It is empty by default.
- packages.txt: Install OS-level packages needed for your project by adding them to this file. It is empty by default.
- requirements.txt: Install Python packages needed for your project by adding them to this file. It is empty by default.
- plugins: Add custom or community plugins for your project to this file. It is empty by default.
- airflow_settings.yaml: Use this local-only file to specify Airflow Connections, Variables, and Pools instead of entering them in the Airflow UI as you develop DAGs in this project.

