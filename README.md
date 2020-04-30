
# Lumen : Test Airflow instance
This is a test Airflow instance to surround Lumen and allow it to be run or tested.

You could do this all without this instance, but it gives you a few DAGs that will purposely fail and succeed
so you can test Lumen more effectively.

## Set up : Virtual environment
TODO: Change `load_examples = True` to `False`
TODO: Change `dag_folder` to `$PWD/dags`
TODO: Change `plugins_folder` to `$PWD/plugins`

`> python -m venv .`
`> source bin/activate`
`> export AIRFLOW_HOME=$PWD/airflow`
`> pip install -r requirements.txt`
`> airflow initdb`