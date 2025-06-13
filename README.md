# supplier-selection-optimization
Engineered a Python-based solution to systematically evaluate and recommend optimal suppliers from a pool of suppliers, driving strategic decision-making and enhancing operational efficiency.

# Supplier Selection and Cost Optimisation for Acme Corporation

## Executive Summary:
This project details the development of a robust data engineering and feature preprocessing pipeline designed to optimise supplier selection for Acme Corporation based on cost. The work focused on transforming raw, complex transactional data into a clean, normalised, and highly optimised dataset. This foundational preparation is crucial for enabling the subsequent development of predictive models that can accurately identify the most cost-effective suppliers for various tasks, thereby driving significant operational efficiencies and cost savings. 

## Problem Statement:
Acme Corporation faced a critical challenge in efficiently identifying the most cost-effective suppliers from a diverse pool for a wide array of tasks. The core objective was to establish a data-driven framework that could rigorously assess supplier performance and task characeristics. This project's contribution was to build the essential data infrastructure, ensuring a high-quality, feature-rich dataset, indispensable for developing a predictive model that could recommend optimal suppliers and minimise overall task costs. 

## Data Sources and Confidentiality:
The analysis was conducted using a proprietary dataset provided by the university. **Due to its confidential and academic nature, this dataset cannot be shared publicly in this repository**. 

The dataset comprised three distinct components:
* **cost_data**: 7680 records detailing the cost of a task performed by a specific supplier, including 'Task ID', 'Supplier ID', and 'Cost'.
* **supplier_data': Information for 64 unique suppliers, each defined by 18 'Supplier Features (SF).
* **task_data**: Details for 130 unique tasks, each initially characterised by 116 'Task Features (TF)'.

## Methodology:
A meticulous multi-stage data preparation and feature engineering pipeline was implemented to ensure data quality and suitability for advanced modelling:
1. **Data Ingestion and Initial Assessment**:
   * The three primary datasets ('cost_data' , 'supplier_data' , 'task_data') were loaded into pandas DataFrames.
   * Initial structural inspection was performed using '.info()' to verify data types, non-null counts, and memory footprint.
   * Thorough checks for missing values were conducted across all datasets, confirming data completeness in the raw state.
   * Duplicate entries (10 from 'cost_data' , 2 from 'supplier_data') were identified andremoved to ensure data integrity and uniqueness.

2. **Data Transformation and Integration**:
   * **Task ID Format Standardisation**: A critical step involved normalising the 'Task ID' format. Task IDs in 'task_data' were in 'MM DD' format, while 'cost_data' used 'DD/MM/YYYY'. All 'Task ID' entries were consistently converted to 'YYYY-MM-DD'. enabling seamless merging across datasets.
   * **Consolidated Dataset Creation**: 'cost_data' was integrated with 'task_data' and 'supplier_data' to form a comprehensive dataset, linking task costs with both task and supplier attributes. Task IDs without corresponding cost values were systematically dropped.

3. **Feature Selection - Low Variance Filtering**:
   * To enhance model efficiency and eliminate noise, features from 'task_data' that exhibited minimal variability were removed.
   * Features with a variance below a threshold of **0.01** were identified and dropped. This significantly reduced the initial **116 Task Feastures by 33**, resulting in a more focused and informative set of attributes. Supplier features were retained as they demonstrated sufficient variance.

4. **Feature Scaling (Min-Max Normalisation)**:
   * To prevent features with larger numerical ranges from dominating model training, 'MinMaxScaler' from scikit-learn was applied.
   * All numerical features in both 'task_data' and 'supplier_data' were scaled to a consistent range of **-1 to 1**. This normalisation step is fundamental for the optimal performance of many machine learning algorithms.

5. **Feature Selection - High Correlation Filtering**:
   * To mitigate multicollinearity and improve model interpretability, a correlation analysis was performed on the processed Task Features.
   * A correlation matrix was generated to visualise inter-feature relationships.
   * For any feature pair exhibiting a correlation coefficient of **0.8 or higher**, one of the features was removed. This step effectively reduced the number of Task Features by **64**, culminating in a final set of **19** robust and uncorrelated Task Features**, ready for predictive modelling.

## Key Findings and Impact:
The meticulous data preparaion and feature engineering pipeline successfully culminated in a **clean, normalised, and highly optimised dataset**.This rigorously prepared dataset is the cornerstone for building accurate and robust predictive models for supplier selection. By systematically addressing data quality, relevance, and collinearity, this project:
* **Enables Accurate Cost Prediction**: The streamlined dataset is primed for machine learning models to precisely forecast task costs, leading to better budgeting and financial planning.
* **Improves Model Interpretability**: By removing highly correlated features, future models will be more transparent, allowing Acme Corporation to clearly understand the key drivers of supplier costs.
* **Faciliatates Data-Driven Sourcing**: This project provides Acme Corporation with a powerful analytical asset, enabling a transition from intuitive supplier selection to a data-informed startegy for identifying the most cost-effective and suitabke partners.

## Tools and Technologies:
* **Programming Language**: Python
* **Key Libraries**:
  * 'pandas': Indispensable for all data manipulation, cleaning, and transformation tasks.
  * 'numpy': Utilised for high-performance numerical operations.
  * 'scikit-learn':Employed for 'MinMaxScaler' for feature engineering, and for implementing variance-based and correlation-based feature selection.
  * 'matplotlib' and 'seaborn': Used for creating insightful visualisations, particularly the correlation matrix to guide feature selection.

## Confidentiality Note and Project Deliverables:
Due to the confidential nature of the dataset provided by the university and the detailes analysis performed, *neither the raw data nor the complete project code can be shared publicly** in this repository. This README.md serves as a comprehensive and detailed overview of the problem, the robust methodology employed, and the significant impact derived from the project. 

While the full code is not shared, pivotal steps and methodologies are conceptually explained and can be illustrated with key data snapshots withing the original technical report **(available on request)**.

## Visualisations:

Below are some key visualisations illustrating the project's data transformations and insights:

* **Initial Data Structures**:
  * **Figure 1**: Early Exploration on cost_data data sets []
  * **Figure 2**: Early Exploration on supplier_data data sets []
  * **Figure 3**: Early Exploration on task_data data sets []
* **Missing Value Confirmation**:
  * **Figure 4**: No Missing Values in the Data sets []
* **Date Format Standardisation**:
  * **Figure 5**: Changing Date Format in Task ID []
* **Feature Scaling Impact**:
  * **Figure 6**: Normalising Features Range from -1 to 1 []
  * **Figure 7**: Normalised Task Features []
  * **Figure 8**: Normalised Supplier Features []
* **Correlation Matrix Heatmap**:
  * **Figure 9**: Correlation Chart []
