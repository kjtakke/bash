# Crudini Documentation

## Overview

Crudini is a utility for configuring INI-like files in a flexible and script-friendly way on Linux systems. INI files are simple, structured text files commonly used for configuration settings. Crudini provides an easy-to-use command-line interface to read, modify, and manage these files without manually editing them, which can be error-prone and cumbersome.

## Installation

Before using Crudini, you need to install it on your system. It is usually available in the package repositories of most Linux distributions.

### On Ubuntu/Debian

```bash
sudo apt update
sudo apt install crudini
```

### On CentOS/RHEL

For CentOS/RHEL 8 and later:

```bash
sudo dnf install crudini
```

For CentOS/RHEL 7:

First, enable the EPEL repository if it's not already enabled:

```bash
sudo yum install epel-release
```

Then, install Crudini:

```bash
sudo yum install crudini
```

### On Fedora

```bash
sudo dnf install crudini
```

## Basic Usage

Crudini can be used for various operations on INI files, such as getting, setting, and removing values. Here's a breakdown of its primary functionalities:

### Syntax

```bash
crudini [OPTIONS] OPERATION FILE [SECTION [PARAMETER [VALUE ...]]]
```

### Operations

- `--get`: Retrieve a parameter's value.
- `--set`: Set a parameter's value.
- `--del`: Remove a parameter or an entire section.
- `--merge`: Merge content into the file.

### Options

- `--verbose`: Display verbose output.
- `--help`: Display help message and exit.
- `--inplace`: For `--merge` operation, update the file in place.
- `--format=FORMAT`: Specify output format for `--get` operation (`ini`, `sh`, `json`, or `xml`).

### Examples

#### Retrieve a Value

To retrieve the value of a parameter:

```bash
crudini --get config.ini section parameter
```

#### Set a Value

To set or change the value of a parameter in a section:

```bash
crudini --set config.ini section parameter value
```

#### Remove a Parameter

To remove a specific parameter from a section:

```bash
crudini --del config.ini section parameter
```

#### Remove a Section

To remove an entire section:

```bash
crudini --del config.ini section
```

#### Merge INI Content

To merge new content into the existing INI file:

```bash
crudini --merge config.ini <<< "
[new_section]
parameter=value
"
```

## Advanced Usage

### Working with Nested Sections

Some INI files support nested sections, which can be accessed using a colon `:` separator.

```bash
crudini --get nested.ini section1:subsection parameter
```

### Output in Different Formats

Crudini can output in various formats, which is useful for scripting or integration with other tools.

```bash
crudini --get --format=json config.ini section parameter
```

## Best Practices

1. **Backup Configuration Files**: Before using Crudini to modify configuration files, it's best practice to create a backup.
   
   ```bash
   cp config.ini config.ini.bak
   ```

2. **Verify Changes**: After making changes with Crudini, it's essential to verify the changes by reviewing the file.

   ```bash
   crudini --get config.ini section parameter
   ```

3. **Use Scripts for Automation**: Automate configuration management tasks by incorporating Crudini commands into shell scripts. This reduces manual errors and ensures consistency.

4. **Permissions**: Ensure you have the necessary permissions to read or write to the configuration files, especially when running commands that alter their content.

## Conclusion

Crudini is a powerful and flexible tool for managing INI files directly from the command line. Its straightforward interface makes it ideal for both simple and complex tasks, from reading a single configuration value to automating configuration changes across multiple systems.

For more detailed information, refer to the Crudini [GitHub repository](https://github.com/pixelb/crudini) or check the built-in help command.

```bash
crudini --help
```