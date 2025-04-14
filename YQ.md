`yq` is a command-line tool designed for parsing, transforming, and querying YAML—a human-friendly data serialization standard that is commonly used for configuration files and data exchange. `yq` is akin to `jq`, but specifically for YAML instead of JSON.

There are several versions of `yq`, written in different languages (Python, Go, etc.). One of the most popular and feature-rich versions is written in Go by Mike Farah. This guide will cover usage of Mike Farah's `yq` since it is robust and widely used.

# `yq` for YAML Processing

## Installation

### On macOS (using Homebrew):

```bash
brew install yq
```

### On Linux (using Snap):

```bash
sudo snap install yq
```

### On Windows (using Chocolatey):

```bash
choco install yq
```

### Direct Download:

Check the [GitHub Releases page for `yq`](https://github.com/mikefarah/yq/releases) to download binaries for different platforms.

## Basic Usage

The `yq` command operates on YAML files with a similar syntax to `jq` for JSON, allowing you to query and manipulate YAML data.

## Example YAML

Consider the following YAML stored in `example.yml`:

```yaml
people:
  - name: "Alice"
    age: 30
    city: "New York"
  - name: "Bob"
    age: 25
    city: "Los Angeles"
```

## Common Operations

### Reading and Pretty Printing

Print the entire YAML content:

```bash
yq eval '.' example.yml
```

### Accessing Specific Elements

Access the names of all people:

```bash
yq eval '.people[].name' example.yml
```

### Filtering Content

Select people older than 26:

```bash
yq eval '.people[] | select(.age > 26)' example.yml
```

## Modifying YAML

### Adding/Updating Fields

Add an email field to each person (outputs modified YAML):

```bash
yq eval '.people[] |= . + {"email": "unknown@example.com"}' example.yml
```

### Deleting Fields

Delete the `city` attribute:

```bash
yq eval '(... | select(has("city")) | del(.city))' example.yml
```

### Editing In-Place

To save the changes back to the original file, use the `-i` flag:

```bash
yq eval -i '.people[].age += 1' example.yml
```

### Creating Arrays or Lists

Convert list of names into an array:

```bash
yq eval '[.people[].name]' example.yml
```

## Advanced Usage

### Combining Queries

Chain queries to perform complex transformations:

```bash
yq eval '.people[] | select(.age > 26) | {name: .name, location: .city}' example.yml
```

### Handling Multiple Files

Process multiple files simultaneously by passing them to `yq`:

```bash
yq eval '.some-key' file1.yml file2.yml
```

### String and Data Manipulations

Update all names to uppercase:

```bash
yq eval '.people[].name |= upcase' example.yml
```

### Handling JSON Input/Output

`yq` can also process JSON data, making it versatile:

Convert a JSON file to YAML:

```bash
yq eval -P example.json
```

### Querying with Anchors and Aliases

Suppose you use YAML references; `yq` can handle these with ease, allowing you to interact with complex YAML types including anchors and aliases.

## Conclusion

`yq` by Mike Farah is a powerful tool for handling YAML data, making it straightforward to parse, manipulate, and query YAML files programmatically. Its syntax and functionality are inspired by `jq`, making it a great choice for users familiar with JSON processing who need to manage YAML data.

Key Points:
- Utilize `yq` for efficient YAML data processing, similar to `jq` for JSON.
- Use chaining and logical operations to perform complex queries.
- Modify and update YAML files in-place with the `-i` flag.
- Handle different data formats and convert between YAML and JSON.

Experiment with the `yq` filters and commands on your YAML files to fully leverage its capabilities in configuration management and data processing tasks!