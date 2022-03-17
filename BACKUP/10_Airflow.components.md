# [Airflow components](https://github.com/jacquiwuc/jacquiwu-blog/issues/10)

**Airflow Scheduler:** 

This component is responsible for scheduling jobs. This is a multithreaded Python process that triggers the workflow execution according to set schedule and commands task instance execution when the upstream dependencies have been resolved and required conditions have been met.

The task state is retrieved and updated from the database accordingly. The web server then uses these saved states to display job information.


**Airflow Celery:**

The 'executor' and 'load balance' mechanism of Airflow: selects the available Worker Node based on the load and submits task for execution to the selected node


**Airflow Worker:**

The process that executes the submitted task. Needs to have local shell access to the process being executed.


**Airflow Flower:**

The component that allows end user to monitor performance of Airflow Celery component via web-browser UI.


**Airflow Webserver:**

The component that allows end user to monitor performance of Airflow as a system, schedule/unschedule DAGs, retrieve task/DAG status via web-browser UI