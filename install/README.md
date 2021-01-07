# Setup

Create directory at home folder
```
$ mkdir ~/airflow
$ export AIRFLOW_HOME=~/airflow
```
Install from pypi using pip
```
$ pip install apache-airflow
```
Edit airflow.cfg
```
$ vi ~/airflow/airflow.cfg 
```
and set the following:
```
rbac = True
```
Initialize the database
```
$ airflow initdb
```
Create user
```
$ airflow create_user \ 
    -u <user> \
    -f <first name> \
    -l <last name> \
    -r <role: Admin> \
    -e <email> \
    -p <password>
```
Start the web server, default port is 8080
```
$ airflow webserver --port 8080
```
Start the scheduler. Open a new terminal or else run webserver with ``-D`` option to run it as a daemon
``` 
$ airflow scheduler
```
Visit localhost:8080 in the browser and use the admin account you just created to login. Enable the example_bash_operator dag in the home page
