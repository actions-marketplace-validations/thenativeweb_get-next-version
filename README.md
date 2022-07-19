# get-next-version

get-next-version gets the next version for your repository according to semantic versioning based on conventional commits.

## Installation

Go to the [releases page](https://github.com/thenativeweb/get-next-version/releases), find the download url for your architecture and operating system, and copy it.

Then, run the following steps:

```shell
# Download the latest release (insert the url here)
$ curl -o get-next-version <URL>

# Ensure the binary is executable
$ chmod a+x get-next-version

# Move the binary to the application directory
$ sudo mv get-next-version /usr/local/bin
```

## Quick Start

Go to the repository and run `get-next-version`. The tool will analyse the history of your repository and output the next version for your release.

```shell
$ get-next-version
```

Optionally, you may hand over the `--repository` (or short `-r`) flag to specify the path to the repository you want to analyse, if it is not in the current working directory.

```shell
$ get-next-version --repository <PATH>
```

By default, output will be shown in a human-readable format. If you want to show the output in a machine-readable format, you can use the `--format` (or short `-f`) flag:

```shell
# Show output in JSON format
$ get-next-version --fornat json

# Show output in GitHub Action format
$ get-next-version --fornat github-action
```

## Using the GitHub Action

For convenience, you may use the GitHub Action when running `get-next-version` inside a workflow on GitHub.

```yaml
name: Example workflow

on: pull_request

jobs:
  example:
    name: Example
    runs-on: ubuntu-latest

    steps:
    - name: Clone repository
      uses: actions/checkout@v3
    - name: Get next version
      id: get_next_version
      uses: thenativeweb/get-next-version
    - name: Show the next version
      run: |
        echo ${{ steps.get_next_version.outputs.version }}
        echo ${{ steps.get_next_version.outputs.hasNextVersion }}
```