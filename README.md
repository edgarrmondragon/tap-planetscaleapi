# tap-planetscaleapi

`tap-planetscaleapi` is a Singer tap for [PlanetScale API](https://api-docs.planetscale.com/reference/getting-started-with-planetscale-api).

Built with the [Meltano Tap SDK](https://sdk.meltano.com) for Singer Taps.

## Installation

Install from PyPi:

```bash
pipx install tap-planetscaleapi
```

Install from GitHub:

```bash
pipx install git+https://github.com/edgarrmondragon/tap-planetscaleapi.git@main
```

## Capabilities

* `catalog`
* `state`
* `discover`
* `about`
* `stream-maps`
* `schema-flattening`
* `batch`


## Settings

| Setting             | Required | Default | Description |
|:--------------------|:--------:|:-------:|:------------|
| service_token_id    | True     | None    | The service token ID, visible on the service token page |
| service_token       | True     | None    | The service token value |
| stream_maps         | False    | None    | Config object for stream maps capability. For more information check out [Stream Maps](https://sdk.meltano.com/en/latest/stream_maps.html). |
| stream_map_config   | False    | None    | User-defined config values to be used within map expressions. |
| flattening_enabled  | False    | None    | 'True' to enable schema flattening and automatically expand nested properties. |
| flattening_max_depth| False    | None    | The max depth to flatten schemas. |
| batch_config        | False    | None    |             |

A full list of supported settings and capabilities is available by running: `tap-planetscaleapi --about`

## Supported Python Versions

* 3.8
* 3.9
* 3.10
* 3.11
* 3.12

A full list of supported settings and capabilities for this tap is available by running:

```bash
tap-planetscaleapi --about
```

### Configure using environment variables

This Singer tap will automatically import any environment variables within the working directory's
`.env` if the `--config=ENV` is provided, such that config values will be considered if a matching
environment variable is set either in the terminal context or in the `.env` file.

### Source Authentication and Authorization

## Usage

You can easily run `tap-planetscaleapi` by itself or in a pipeline using [Meltano](https://meltano.com/).

### Executing the Tap Directly

```bash
tap-planetscaleapi --version
tap-planetscaleapi --help
tap-planetscaleapi --config CONFIG --discover > ./catalog.json
```

## Developer Resources

Follow these instructions to contribute to this project.

### Initialize your Development Environment

```bash
pipx install poetry
poetry install
```

### Create and Run Tests

Create tests within the `tests` subfolder and
  then run:

```bash
poetry run pytest
```

You can also test the `tap-planetscaleapi` CLI interface directly using `poetry run`:

```bash
poetry run tap-planetscaleapi --help
```

### Testing with [Meltano](https://www.meltano.com)

_**Note:** This tap will work in any Singer environment and does not require Meltano.
Examples here are for convenience and to streamline end-to-end orchestration scenarios._

<!--
Developer TODO:
Your project comes with a custom `meltano.yml` project file already created. Open the `meltano.yml` and follow any "TODO" items listed in
the file.
-->

Next, install Meltano (if you haven't already) and any needed plugins:

```bash
# Install meltano
pipx install meltano
# Initialize meltano within this directory
cd tap-planetscaleapi
meltano install
```

Now you can test and orchestrate using Meltano:

```bash
# Test invocation:
meltano invoke tap-planetscaleapi --version
# OR run a test `elt` pipeline:
meltano elt tap-planetscaleapi target-jsonl
```

### SDK Dev Guide

See the [dev guide](https://sdk.meltano.com/en/latest/dev_guide.html) for more instructions on how to use the SDK to
develop your own taps and targets.
