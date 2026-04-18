Initialized by Azure Data Factory!

flowchart TD
    subgraph Bronze Layer [Raw Data]
        A[(telemetry_data.csv)]
    end

    subgraph Silver Layer [Cleaned Data]
        B[(telemetry_data Delta Table)]
    end

    subgraph Gold Layer [Business Aggregates]
        C[(energy_summary Delta Table)]
    end

    Bronze Layer -- "PySpark (Schema inference, Drop Nulls)" --> Silver Layer
    Silver Layer -- "Spark SQL (Aggregating state-level averages)" --> Gold Layer
    
    style Bronze Layer fill:#cd7f32,stroke:#333,stroke-width:2px,color:#fff
    style Silver Layer fill:#c0c0c0,stroke:#333,stroke-width:2px,color:#fff
    style Gold Layer fill:#ffd700,stroke:#333,stroke-width:2px,color:#000
