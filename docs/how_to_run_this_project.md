
### Creating a fork 

The first thing you need to do, is to create a fork of the repository. You can do so by clicking on the `Fork`
button that is found on the top right corner of the project's page on GitHub. Once you create a fork, you'll then have
to clone your fork onto your local machine. 

### Setup your local environment
In your forked project's directory, create and activate a fresh virtual environment:
```bash
git clone https://github.com/AnandDedha/dbt-airflow-test.git

# Create a virtual environment called `dbt_airflow_venv`
$ python -m venv dbt_airflow_venv

# Move to the Scripts folder in the dbt_airflow_venv; Please make sure to put double quotations using when directory path have spaces
$ cd  /dbt_airflow_venv/Scripts

# Set the windows execution policy
$ Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUse

# Activate the newly created virtual environment using PowerShell ; you can also use from windows cmd.exe
$ .\activate

```
In order to see how your changes will be reflected on Airflow, you can spin up the docker containers from the images
specified in `docker-compose.yml` and `Dockerfile` files. 

```bash
# Build the images (you can omit `--no-cache` in case you don't want to re-build every layer)
$ docker compose build --no-cache

# Run the containers
$ docker compose up
```
Basically, the commands above will spin up the following containers:
- An Airflow instance whose webserver can be accessd on `localhost:8080` (use `airflow` and `airflow` in user/pass credentials)
- A postgres instance containing the popular Sakila data, where dbt models can materialize
- A container that gives you access to `dbt` CLI where you can run further `dbt` commands


