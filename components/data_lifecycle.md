# Automated Data Lifecycle and Analysis



This component provides the automated experimental data lifecycle layer of the Autonomous Scientific Data Framework.



## Repository



https://github.com/Sireesiru/cnms-microflows-airflow-data\_standardization\_analysis



## Role in the Framework



Apache Airflow orchestrates the movement and processing of newly generated experimental data through the scientific data infrastructure.



The workflow supports:



\- Monitoring incoming experimental data

\- Staging newly generated files

\- Converting instrument-specific data into standardized HDF5-based representations

\- Executing automated analysis workflows

\- Registering experimental data and metadata in DataFed

\- Tracking workflow execution, failures, and retries



## Integration with the Scientific Agent



Once experimental data are registered in DataFed, the Agentic Scientific Data Assistant can discover the records through MCP tools, inspect their metadata and provenance, access standardized datasets, and execute scientific analyses.



This creates the data pathway:



Instrument → Airflow → Standardization/Analysis → DataFed → MCP Scientific Agent



