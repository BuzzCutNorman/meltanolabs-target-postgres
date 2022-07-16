# `target-postgres`

Target for Postgres.

Built with the [Meltano SDK](https://sdk.meltano.com) for Singer Taps and Targets.

## Capabilities

* `about`
* `stream-maps`
* `schema-flattening`

## Settings

| Setting             | Required | Default | Description |
|:--------------------|:--------:|:-------:|:------------|
| sqlalchemy_url      | True     | None    | SQLAlchemy connection string, example `postgresql://postgres:postgres@localhost:5432/postgres` |
| stream_maps         | False    | None    | Config object for stream maps capability. |
| stream_map_config   | False    | None    | User-defined config values to be used within map expressions. |
| flattening_enabled  | False    | None    | 'True' to enable schema flattening and automatically expand nested properties. |
| flattening_max_depth| False    | None    | The max depth to flatten schemas. |

A full list of supported settings and capabilities is available by running: `target-postgres --about`

# target-postgres

This tap is in **development**, it probably doesn't work yet, stick with https://hub.meltano.com/loaders/target-postgres for now 

## Installation

- [ ] `Developer TODO:` Come back to this re [#5](https://github.com/MeltanoLabs/target-postgres/issues/5)

```bash
pipx install -e .
```

## Configuration

### Configure using environment variables

This Singer target will automatically import any environment variables within the working directory's
`.env` if the `--config=ENV` is provided, such that config values will be considered if a matching
environment variable is set either in the terminal context or in the `.env` file.

### Source Authentication and Authorization

The database account provided must have access to:
1. Create schemas 
1. Create tables (DDL)
1. Push Data to tables (DML)

## Usage

You can easily run `target-postgres` by itself or in a pipeline using [Meltano](https://meltano.com/).

### Executing the Target Directly

```bash
target-postgres --version
target-postgres --help
# Test using the "Carbon Intensity" sample:
pipx install git+https://gitlab.com/meltano/tap-carbon-intensity
tap-carbon-intensity | target-postgres --config /path/to/target-postgres-config.json
```

## Developer Resources

### Initialize your Development Environment

```bash
pipx install poetry
poetry install
```

### Create and Run Tests

Create tests within the `target_postgres/tests` subfolder and
  then run:

```bash
poetry run pytest
```

You can also test the `target-postgres` CLI interface directly using `poetry run`:

```bash
poetry run target-postgres --help
```

### Testing with [Meltano](https://meltano.com/)

_**Note:** This target will work in any Singer environment and does not require Meltano.
Examples here are for convenience and to streamline end-to-end orchestration scenarios._

Your project comes with a custom `meltano.yml` project file already created. 

Next, install Meltano (if you haven't already) and any needed plugins:

```bash
# Install meltano
pipx install meltano
# Initialize meltano within this directory
meltano install
```

Now you can test and orchestrate using Meltano:

```bash
# Test invocation:
meltano invoke target-postgres --version
```

### SDK Dev Guide

See the [dev guide](https://sdk.meltano.com/en/latest/dev_guide.html) for more instructions on how to use the Meltano SDK to
develop your own Singer taps and targets.