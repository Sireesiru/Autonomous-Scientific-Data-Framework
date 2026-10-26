# Framework Architecture



The Autonomous Scientific Data Framework integrates experimental data lifecycle automation, provenance-aware scientific analysis, and literature-grounded reasoning as three modular layers.



## Architecture



```text

&#x20;                   EXPERIMENTAL FACILITY

&#x20;                            |

&#x20;                            v

&#x20;                Experimental Instruments

&#x20;                            |

&#x20;                            v

+--------------------------------------------------+

|  LAYER 1: AUTOMATED DATA LIFECYCLE              |

|                                                  |

|  Apache Airflow                                  |

|  Watch -> Stage -> Standardize -> Analyze        |

|                         -> Register              |

+-------------------------+------------------------+

&#x20;                         |

&#x20;                         v

&#x20;                      DataFed

&#x20;                         |

&#x20;                         v

+--------------------------------------------------+

|  LAYER 2: SCIENTIFIC DATA AGENT                 |

|                                                  |

|  MCP Tools -> Data Discovery -> Data Inspection |

|            -> Quantitative Analysis             |

|                          |                       |

|                         LLM                      |

+-------------------------+------------------------+

&#x20;                         |

&#x20;                scientific question

&#x20;                         |

&#x20;                         v

+--------------------------------------------------+

|  LAYER 3: LITERATURE RAG                        |

|                                                  |

|  Scientific Embeddings -> FAISS -> MMR          |

|                          |                       |

|                  Literature Evidence             |

+-------------------------+------------------------+

&#x20;                         |

&#x20;                         v

&#x20;                 Scientific Agent

&#x20;                         |

&#x20;                         v

&#x20;             Evidence-Grounded Interpretation

&#x20;                         |

&#x20;                         v

&#x20;              Hypothesis / Recommended

&#x20;               Analysis or Experiment


