## Data Transformation (Medallion Architecture)
```mermaid
flowchart TD
    subgraph Bronze [Raw Data]
        A[(telemetry_data.csv)]
    end

    subgraph Silver [Cleaned Data]
        B[(telemetry_data Delta Table)]
    end

    subgraph Gold [Business Aggregates]
        C[(energy_summary Delta Table)]
    end

    Bronze -- "PySpark (Schema inference, Drop Nulls)" --> Silver
    Silver -- "Spark SQL (Aggregating state-level averages)" --> Gold
    
    style Bronze fill:#cd7f32,stroke:#333,stroke-width:2px,color:#fff
    style Silver fill:#c0c0c0,stroke:#333,stroke-width:2px,color:#fff
    style Gold fill:#ffd700,stroke:#333,stroke-width:2px,color:#000
