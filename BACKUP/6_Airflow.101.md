# [Airflow 101](https://github.com/jacquiwuc/jacquiwu-blog/issues/6)

**What is Airflow?**

Airflow is a platform that lets you build and run workflows. A workflow is represented as a DAG, i.e., Directed Acyclic Graph. Airflow contains individual pieces of work called tasks, arranged with dependencies and data flows taken into account.

**The first core concept: DAG**

- DAG:

A DAG is the core concept of Airflow, collecting tasks together, organized with dependencies and relationships to say how they should run.

- DAG RUN:

A DAG run is an object representing an instantiation of the DAG in time.

- TASK:

A task is the basic unit of execution in Airflow. Tasks are arranged into DAGs, and then have upstream and downstream dependencies set between them into order to ecpress the order they should run.

**The second core concept: Scheduler**

The scheduler monitors all tasks and DAGs and then triggers the task instances once their dependencies are complete. Behind the scenes, the scheduler spins up a subprocess, which monitors and stays in sync with all DAGs in the specified DAG directory. Once per minute, by default, the scheduler collects DAG parsing results and checks whether any active tasks can be triggered,

1.  Check for any DAGs needing a new DagRun and create them
2. Examine a batch of DAG runs for schedulable TaskInstances or complete DAG runs
3. Select schedulable TaskInstances, and whilst respecting pool limits and other concurrency limits, enqueue them for execution