



# Lumen : Test Airflow instance
This is a test Airflow instance to surround Lumen and allow it to be run or tested.

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

### Symlink your Lumen dev directory to plugins
`> mkdir ./plugins/`

`> ln -s <your Lumen dev path> ./plugins/`

### Set up a user (admin:admin)

`> airflow create_user -r Admin -u admin -e admin@example.com -f admin -l user -p admin`

### Set up Lumen
Move over the main Lumen DAG and sample DAGs (if wanted)

`> plugins/lumen_plugin/bin/lumen init`

`> plugins/lumen_plugin/bin/lumen add_samples`

## Set up : Astronomer
First, download the [Astronomer CLI](https://www.astronomer.io/docs/cli-getting-started/)

### Initialize Astronomer
In your working directory
`> astro dev init`

### Clone your repo into Astro plugins
Docker doesn't load files at symlinks so you'll
need to clone your repo into Astronomer's plugins directory if you want to use it as your development environment 
`> git clone git@github.com:Raybeam/lumen_plugin.git plugins/lumen_plugin`

### Copy over Lumen requirements
`> cat plugins/lumen_plugin/requirements.txt >> requirements.txt`

### Setup Lumen
`> plugins/lumen_plugin/bin/lumen init`

Only the DAG works from the Lumen binary right now.

`> plugins/lumen_plugin/bin/lumen add_samples --dag_only`

### Start Astronomer
`> astro dev start`