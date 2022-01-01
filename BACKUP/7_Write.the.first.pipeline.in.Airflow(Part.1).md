# [Write the first pipeline in Airflow(Part 1)](https://github.com/jacquiwuc/jacquiwu-blog/issues/7)

### Steps to write an Airflow DAG?
A DAG file, which is basically just a python script, is a configuration file specifying the DAG's structure as code.

There are only 5 steps you need to remember to write an Airflow DAG or workflow:
- Step 1: Importing modules
- Step 2: Default Arguments
- Step 3: Instantiate a DAG
- Step 4: Tasks
- Step 5: Setting up Dependencies

### Step 1:  Importing modules

```
from datetime import timedelta
import airflow
from airflow import DAG
from airflow.operators.bash_operator import BashOperator
```

### Step 2:  Default Arguments
- Define default and DAG-specific arguments

```
default-args = {
       'owner' : 'airflow',
       'start_date' :  airflow.utils.dates.days_ago(2),
       # 'end_date' : datetime(2018, 12, 30),
       'depends_on_past': False,
       'Email_on_retry': False,
       # If a task fails, retry it once after waiting
       # at least 5 minutes
       'retries' : 1,
       'retry_delay' : timedelta(minutes = 5), 
                 }
```

### Step 3:  Instantiate a DAG  
- Given the DAG name, and then configure the schedule etc

```
dag = DAG(
       'tutorials',
       default_args = defaults_args,
       description = 'A simple tutorial DAG',
       # Continue to run DAG once per day
       schedule_interval = timedelta(day=1),
)
```