# Agentic Scientific Data Assistant



This component provides the scientific data access, analysis, and reasoning layer of the Autonomous Scientific Data Framework.



## Repository



https://github.com/Sireesiru/Agentic-Scientific-Data-Assistant



## Role in the Framework



The scientific agent connects a large language model with experimental data and executable analysis tools through the Model Context Protocol (MCP).



The agent can:



\- Search DataFed collections and records

\- Retrieve experimental metadata and provenance

\- Inspect standardized HDF5 datasets and available channels

\- Access numerical experimental data

\- Generate visualizations and distributions

\- Compare datasets quantitatively

\- Invoke literature retrieval when external scientific evidence is required

\- Integrate experimental observations with retrieved literature to support scientific interpretation and next-step reasoning



## Framework Integration



The agent sits between the experimental data infrastructure and the literature RAG system:



DataFed → MCP Tools → Scientific Analysis → LLM Reasoning



When literature evidence is required:



Scientific Agent → Literature RAG → Retrieved Evidence → Scientific Agent



This separation ensures that numerical measurements are produced by executable analysis tools, while literature retrieval supplies external scientific context for interpretation.


