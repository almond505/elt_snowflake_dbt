# ELT Pipeline: Airflow, dbt, and Snowflake

## Project Overview

This repository contains the code and configuration for building a robust, cloud-native **ELT (Extract, Load, Transform)** data pipeline. The project demonstrates industry-standard practices for data orchestration, warehousing, and transformation using best-in-class tools.

The pipeline is designed to:
1.  **E/L (Extract/Load):** Simulate data ingestion into a centralized data warehouse (**Snowflake**).
2.  **T (Transform):** Transform the raw data into optimized, consumption-ready data models using **dbt (data build tool)**.
3.  **Orchestrate:** Schedule and monitor the entire workflow using **Apache Airflow**.

---

## Core Technology Stack

| Component | Tool | Description |
| :--- | :--- | :--- |
| **Data Warehouse** | **Snowflake** | The powerful, cloud-agnostic data platform used for storing raw data and hosting the final data marts. |
| **Transformation** | **dbt (data build tool)** | Used to define, document, and test data transformations via SQL, enforcing software engineering best practices for analytics code. |
| **Orchestration** | **Apache Airflow** | Manages and schedules the dependencies between tasks, specifically orchestrating the execution of the `dbt` project. |
| **Data Modeling** | **SQL & Jinja** | Used within dbt models to build analytical structures like fact and dimension tables. |

---

## Key Concepts Explored

### 1. Data Modeling

The project implements **dimensional modeling** techniques to ensure data is optimized for analysis and reporting:

* **Fact Tables:** Designed to store quantitative, event-based data and foreign keys to dimension tables.
* **Dimension Tables:** Used to store descriptive attributes related to the facts (e.g., product details, customer information).
* **Data Marts:** Creating consumption-ready schemas for specific business domains or use cases.

### 2. dbt Best Practices

The dbt project is structured to enforce data quality and maintainability:

* **Staging Layer (`stg_`):** Minimal transformations applied to raw data to ensure consistency and clean data types.
* **Marts Layer (`marts_`):** Final, business-logic-driven models (fact/dim) ready for BI tools.
* **Tests & Documentation:** Comprehensive schema and data tests, along with documentation, are included for all critical models.

### 3. Snowflake Role-Based Access Control (RBAC)

The pipeline setup incorporates **Snowflake RBAC** principles to manage access securely:

* **Roles:** Creation of custom roles (e.g., `DBT_DEVELOPER`, `ANALYST_ROLE`).
* **Privileges:** Assigning granular privileges (USAGE, SELECT, CREATE) to roles to adhere to the **principle of least privilege**.
* **Hierarchical Roles:** Structuring roles to inherit permissions for streamlined management.

### 4. Airflow Orchestration

Airflow is used to automate the transformation layer:

* **dbt Operator:** Utilizing a custom or community dbt operator to execute dbt commands (`dbt seed`, `dbt run`, `dbt test`) within a scheduled **DAG** (Directed Acyclic Graph).
* **Dependencies:** Defining explicit dependencies to ensure data is loaded/seeded *before* the dbt transformation process begins.

---

## Reference Tutorial

This project is directly inspired by a live, end-to-end tutorial demonstrating how to integrate these powerful tools.

**Tutorial Link:** [Building an ELT Pipeline with dbt, Snowflake, and Airflow](https://youtu.be/OLXkGB7krGo?si=-QUw3X9yv4PIN2xl)

---
