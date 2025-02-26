
### Core Concepts Covered

*   **Spark Overview:**
    *   Spark is a unified, open-source computing engine for parallel data processing.
    *   It supports languages like Java, Scala, Python, and R.
    *   Spark is known for its speed, being potentially 100 times faster than MapReduce due to in-memory processing.
*   **Spark Components:**
    *   **Low-Level APIs:** RDDs (Resilient Distributed Datasets) and distributed variables form the base.
    *   **Structured APIs:** Spark SQL, DataFrames, and Datasets are built on RDDs and optimized for use.
    *   **Libraries and Ecosystem:** Includes Structured Streaming, advanced analytics, and graph query languages.
*   **Spark Architecture:**
    *   **Driver:** The heart of the Spark application, responsible for maintaining information, analyzing, distributing, and scheduling work.
    *   **Executors:** JVM processes that run on cluster machines, executing tasks and reporting status to the driver.
    *   **Jobs, Stages, and Tasks:** A job is divided into stages based on shuffles, and stages are further divided into tasks.  Each core can handle one task at a time, enabling parallel processing.
*   **Key Concepts:**
    *   **Partitions:** Spark breaks data into chunks called partitions for parallel processing by executors.
    *   **Transformations:** Instructions to modify data (e.g., select, where, groupBy). They are of two types:
        *   **Narrow Transformations:** Each partition contributes to at most one partition.
        *   **Wide Transformations:** One partition can contribute to multiple partitions, leading to data shuffling.
    *   **Actions:** Trigger the execution of the logical plan created by transformations (e.g., viewing data, collecting data, writing to data sources).
    *   **Lazy Evaluation:** Spark waits until an action is called to execute the computational graph (logical plan of transformations), allowing for optimization.
    *   **Spark Session:** The entry point for Spark execution, responsible for executing code in the cluster. A single Spark application has one Spark Session.
*   **DataFrames:**
    *   The most important structured API, resembling a table with rows and columns.
    *   Each column has associated metadata (schema).
    *   DataFrames are stored in partitions and are immutable (cannot be changed after creation, but new DataFrames can be created from existing ones).
*   **Execution Planning:**
    *   **Logical Planning:**
        *   Code is supplied, and Spark creates an unresolved logical plan.
        *   The plan is validated against a catalog.
        *   A resolved logical plan is created and optimized by the Catalyst Optimizer, generating an optimized logical plan.
    *   **Physical Planning:**
        *   Spark generates multiple physical plans based on the cluster configuration.
        *   Plans are evaluated using a cost model.
        *   The best physical plan is selected and sent to executors for execution against data partitions.
*   **DAG (Directed Acyclic Graph):** Spark uses DAGs to resolve its execution plan.
