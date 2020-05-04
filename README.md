
# Lumen : Test Airflow instance
This is a test Airflow instance to surround Lumen and allow it to be run or tested.

You could do this all without this instance, but it gives you a few DAGs that will purposely fail and succeed
so you can test Lumen more effectively.

## Set up : Virtual environment
TODO: Change `load_examples = True` to `False`
TODO: Change `dag_folder` to `$PWD/dags`
TODO: Change `plugins_folder` to `$PWD`
TODO: Require RBAD be true

### Set up the Python virtual environment
`> python -m venv .`

### Set AIRFLOW_HOME
By putting the `AIRFLOW_HOME` env in the `bin/activate` file, you set the path each time you set up your venv.
`> echo "export AIRFLOW_HOME=$PWD" >> bin/activate`

### Activate your venv
`> source bin/activate`

### Install dependencies
`> pip install -r requirements.txt`

### Initialize your Airflow DB
`> airflow initdb`