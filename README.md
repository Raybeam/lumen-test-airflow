



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

## Setup your lumen deployment with emails

Setting up email notifications requires you to edit and add your smtp server credentials to your airflow.cfg
Ensure that these values are set. User, password, host, and mail_from are all values you should fill in from your smtp server settings:

>`[smtp]`\
>`smtp_host = YOUR_SMTP_HOST`\
>`smtp_starttls = True`\
>`smtp_ssl = False`\
>`smtp_user = YOUR_EMAIL_ADDRESS`\
>`smtp_password = 16_DIGIT_APP_PASSWORD`\
>`smtp_port = 587`\
>`smtp_mail_from = YOUR_EMAIL_ADDRESS`

### Setting up email with provider that does not expose airflow.cfg
In order to deploy your emails on these platforms, add the above variables as environmental variables in the the platform's provided interface. Below I'll show how to do this for astronomer and google cloud composer...

![Astronomer env variables](/imgs/Astronomer_Config.png?raw=true "Astronomer")\
![Cloud Composer env variables](/imgs/Cloud_Composer_Config.png?raw=true "Cloud Composer")
