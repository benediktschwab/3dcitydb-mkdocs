---
title: Overview
description: Overview
tags:
  - citydb-tool
  - overview
  - features
---

## Intro

The **citydb-tool** is a command-line utility designed for managing and interacting with the **3DCityDB**,
a database schema for the storage, management, and querying of 3D city models. The tool provides a set of
powerful commands to facilitate the import, export, and manipulation of spatial data, particularly within a
PostgreSQL/PostGIS database environment.

## Version compatibility

Compatibility of citydb-tool, 3DCityDB and CityGML versions are explained [here](../compatibility.md).

## Key features and commands

The citydb-tool supports a variety of operations to streamline database workflows. The following commands are available:

- **`help`**
  Displays help information about a specified command, providing guidance on its usage and options.

- **`import`**
  Allows users to import data into the 3DCityDB in a supported format, such as CityGML or CityJSON.

- **`export`**
  Enables the export of data from the database to various supported formats, including CityGML and CityJSON.

- **`delete`**
  Deletes specific features or records from the database, offering flexible control over stored data.

- **`index`**
  Performs index operations to optimize database performance, ensuring efficient querying and data retrieval.

## Supported database platforms

The citydb-tool works seamlessly with **PostgreSQL** databases enhanced with **PostGIS**, a spatial extension that enables advanced geospatial operations.

## Supported data formats

- **CityGML**: A standard format for the representation, storage, and exchange of 3D urban and landscape models.
- **CityJSON**: A JSON-based format derived from CityGML, optimized for web applications and simplified data exchange.

## Key use cases

- Importing complex 3D city models into a PostgreSQL/PostGIS database.
- Exporting city models for further analysis, visualization, or sharing in CityGML/CityJSON formats.
- Performing maintenance operations, such as deleting outdated features or indexing for better database performance.

---

The **citydb-tool** is ideal for urban planners, GIS professionals, and developers working with 3D city models who require a robust and efficient way to manage large-scale spatial data within a relational database.

The citydb command-line interface for the 3D City Database provides several general options that can be used with any command. These options allow you to configure logging, load configuration files, manage plugins, and more.

## Usage

```bash
citydb [OPTIONS] COMMAND
```

## Options

| Option                        | Description                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| `[@<filename>...]`            | One or more argument files containing options.                              |
| `--config-file=<file>`        | Load configuration from this file.                                          |
| `-L`, `--log-level=<level>`   | Log level: `fatal`, `error`, `warn`, `info`, `debug`, `trace` (default: `info`). |
| `--log-file=<file>`           | Write log messages to this file.                                            |
| `--pid-file=<file>`           | Create a file containing the process ID.                                     |
| `--plugins=<dir>`             | Load plugins from this directory.                                           |
| `--use-plugins=<plugin[=true\|false][,<plugin[=true\|false]...]` | Enable or disable plugins with a matching fully qualified class name (default: `true`). |
| `-h`, `--help`                | Show this help message and exit.                                            |
| `-V`, `--version`             | Print version information and exit.                                         |

## Using an options file for commands

For every citydb-tool command, you can store command-line options in an external options file to simplify complex
or repetitive workflows. This is especially useful when working with commands that require multiple parameters.

To reference an options file, use the @<filename> syntax. The options file contains one option per line in the
following format:

### Example options file (options.txt):

```text
--log-level=debug
--config-file=config.json
--temp-dir=/tmp/citydb_temp
--commit=1000

```

### Run the delete command with options from the file:

```bash
citydb delete @options.txt
```

## Examples

### Accessing help information

To display help information for a specific command, use the `help` command followed by the command name:

General Help: Displays a list of all available commands and general options:

```bash
citydb --help
```

Command-specific Help: Provides detailed information about a specific command and its options:

```bash
citydb export --help
citydb import --help
citydb delete --help
citydb index --help
```

### Setting the log level

To adjust the logging level for a command, use the `-L` or `--log-level` option followed by the desired level:

```bash
citydb export citygml --log-level=debug
```

### Loading configuration from a file

To load configuration settings from a file, use the `--config-file` option followed by the file path:

```bash
citydb import citygml --config-file=config.json
```

### Using plugins

To enable or disable specific plugins, use the `--use-plugins` option followed by the fully
qualified class name of the plugin:

```bash
citydb export citygml --use-plugins=com.example.plugin1=false,com.example.plugin2=true
```

### Writing log messages to a file

To save log messages to a specific file, use the `--log-file` option followed by the file path:

```bash
citydb delete --log-file=delete.log
```

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2F3dcitydb.github.io%2F3dcitydb-mkdocs%2Fcitydb-tool%2Findex%2F&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=Visitors&edge_flat=false)](https://hits.seeyoufarm.com/#history)

/// caption
///
