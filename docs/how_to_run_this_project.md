
## Run the project as it is

### Creating a fork 

The first thing you need to do, is to create a fork of the repository. You can do so by clicking on the `Fork`
button found on the top right corner of the project's page on GitHub. Once you create a fork, you'll then have
to clone your fork onto your local machine. 

### Spin up the docker containers

you can spin up the docker containers from the images
specified in `docker-compose.yml` and `Dockerfile` files. 

```bash
# Build the images (you can omit `--no-cache` in case you don't want to re-build every layer)
$ docker compose build --no-cache

# Run the containers
$ docker compose up
```
The commands above will spin up the following containers:
- An Airflow instance whose webserver can be accessd on `localhost:8080` (use `airflow` and `airflow` in user/pass credentials)
- A postgres instance containing the popular Sakila data, where dbt models can materialize
- A container that gives you access to `dbt` CLI where you can run further `dbt` commands


## Customize the project or contribute to the project.

## Setting up a local environment
The next few sections will help you set up a local development environment where you can quickly test your changes, 
before opening a Pull Request. 

### Creating a fork 

The first thing you need to do, is to create a fork of the repository. You can do so by clicking on the `Fork`
button found on the top right corner of the project's page on GitHub. Once you create a fork, you'll then have
to clone your fork onto your local machine. 

### Setup your local environment
In your forked project's directory, create and activate a fresh virtual environment:
```bash
# Create a virtual environment called `dbt-airflow-venv`
$ python3 -m venv ~/dbt-airflow-venv

# Activate the newly created virtual environment
$ source ~/dbt-airflow-venv/bin/activate
```

Every single merge into `main` branch will trigger a new patch, minor or major version upgrade based on the commit 
messages pushed  from the Pull Request.
The automated release mechanism is based on 
[conventional commits](https://www.conventionalcommits.org/en/v1.0.0/#summary).
Every single commit must follow the structural elements described in Conventional Commits' specification. 
The repository also contains pre-commit hooks that will ensure compliance to the specification. 
Make sure to install pre-commit hooks to avoid any inconsistencies, by following the steps outlined below. 
```bash
# Install `pre-commit` package from PyPI
$ python3 -m pip install pre-commit 

# Install hooks from `.pre-commit-config.yaml`
$ pre-commit install
pre-commit installed at .git/hooks/pre-commit
```

### Testing your changes locally
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
