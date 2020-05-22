



# Raybeam Test Airflow instance
This is a test Airflow instance used for integration testing.

You could do this all without this instance, but it gives you a few DAGs that will purposely fail and succeed
so you can test Lumen more effectively.

## Set up : Virtual environment

### Set up the Python virtual environment
`> python -m venv .`

### Set AIRFLOW_HOME
By putting the `AIRFLOW_HOME` env in the `bin/activate` file, you set the path each time you set up your venv.

`> echo "export AIRFLOW_HOME=$PWD" >> bin/activate`

### Activate your venv
`> source bin/activate`

### Install airflow
`> pip install apache-airflow`

### Initialize your Airflow DB
`> airflow initdb`

### Set up a user (admin:admin)

`> airflow create_user -r Admin -u admin -e admin@example.com -f admin -l user -p admin`

### Symlink your plugin dev directory to plugins
`> mkdir ./plugins/`

`> ln -s <your plugin dev path> ./plugins/`

### Install any required libraries from your plugin

`> pip install -r ./plugins/<your plugin name>/requirements.txt`

