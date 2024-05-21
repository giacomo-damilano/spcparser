# spcparser

Code restructuring as OOP Python of the [shimadzu-spc-converter](https://github.com/uri-t/shimadzu-spc-converter/tree/master) `getspectra.py`

## Overview

`spcparser` is a Python library designed to parse and extract data from `.spc` files, which are commonly used for storing spectral data. This library is a restructured Object-Oriented Programming (OOP) version of the original procedural code found in the `shimadzu-spc-converter` project.

## Installation

To use `spcparser`, simply clone the repository and include the `spcparser.py` file in your project.

```bash
git clone <repository_url>
```

## Usage

Here's a step-by-step guide on how to use `spcparser` to extract spectral data from an `.spc` file.

### Step 1: Import the Library

First, ensure you import the `SpcParser` class from the `spcparser.py` file.

```python
from spcparser import SpcParser
```

### Step 2: Initialize the Parser

Create an instance of the `SpcParser` class, passing the filename of your `.spc` file as an argument.

```python
filename = "path/to/your/file.spc"
parser = SpcParser(filename)
```

### Step 3: Extract Data

Call the `extract_data` method to read and parse the essential data from the `.spc` file.

```python
parser.extract_data()
```

### Step 4: Get Spectral Data

Use the `get_data` method to retrieve the X and Y data arrays from the parsed `.spc` file.

```python
x_data, y_data = parser.get_data()
```

### Step 5: Utilize the Data

Now you can use the extracted `x_data` and `y_data` for further analysis or plotting.

```python
print(x_data)
print(y_data)
```

## Example

Here is a complete example that demonstrates how to use the `spcparser` library:

```python
from spcparser import SpcParser

# Specify the path to your .spc file
filename = "./UV_spectra/240417_EtOH_Ac_sohxlet_#1.spc"

# Initialize the parser
parser = SpcParser(filename)

# Extract data from the file
parser.extract_data()

# Retrieve the spectral data
x_data, y_data = parser.get_data()

# Print the data arrays
print(x_data)
print(y_data)
```

## Class and Method Details

### `SpcParser` Class

- **`__init__(self, filename)`**: Initializes the parser with the specified filename.
- **`extract_data(self)`**: Reads and extracts metadata and directory structures from the `.spc` file.
- **`get_data(self)`**: Retrieves the X and Y data arrays from the `.spc` file.

### Helper Methods

These methods are used internally by the `SpcParser` class to handle file operations and data extraction:

- **`get_params(self, f)`**: Extracts parameters from the file header.
- **`dir_from_path(self, root, namelist, params, f)`**: Navigates the directory tree to find a specific path.
- **`find_in_tree(self, name, ind, params, f)`**: Searches for a directory entry by name.
- **`traverse_dir_sibs(self, ind, params, f)`**: Traverses sibling directories.
- **`get_dir_name(self, ind, params, f)`**: Retrieves the name of a directory entry.
- **`get_dir_stream(self, ind, params, f)`**: Reads the data stream from a directory entry.
- **`bytes_to_arr(self, b, fmt)`**: Converts a byte array to a list of numbers.
- **`get_dir_lrc(self, ind, params, f)`**: Retrieves the left, right, and child indices of a directory entry.
- **`dir_ind_to_offset(self, ind, params, f)`**: Calculates the file offset for a directory entry index.
- **`stream_ind_to_offset(self, ind, params, f)`**: Calculates the file offset for a stream index.
- **`remove_null(self, s1)`**: Removes null characters from a string.
- **`get_next_sect(self, sid, params, f)`**: Finds the next sector in a stream.
- **`get_next_mini_sect(self, ind, params, f)`**: Finds the next mini-sector in a stream.
- **`get_stream_contents(self, ind, size, params, f)`**: Retrieves the contents of a data stream.
