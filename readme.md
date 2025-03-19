# PySpark Basic

This repository contains a basic example of using PySpark to load, transform, and display data. The example demonstrates initializing a Spark session, loading data from a CSV file, performing transformations, and viewing results.

## Prerequisites

To run this example, you’ll need:

- Python 3.x
- PySpark (Installation instructions below)

## Installation

1. **Install PySpark**:

    You can install PySpark using pip:
    ```bash
    pip install pyspark
    ```

2. **Download or Clone this Repository**:

    Clone this repository to your local machine or download the example code.

## Usage

Follow these steps to run the PySpark code:

1. Open the file containing the example code (`pyspark_example.py`).
2. Replace `"path/to/your_file.csv"` with the path to your CSV file.

3. Run the code:

    ```bash
    python pyspark_example.py
    ```

## Code Overview

The example code performs the following steps:

1. **Initialize SparkSession**: Creates a new Spark session to run PySpark.
2. **Load Data**: Loads data from a CSV file with headers and infers schema.
3. **Transform Data**:
   - **Select** specific columns.
   - **Filter** rows based on a condition.
   - **Group By** a column and count occurrences.
4. **Display Results**: Shows the filtered and grouped data.
5. **Stop SparkSession**: Stops the session once processing is complete.

### Example Code

```python
from pyspark.sql import SparkSession

# Start a Spark session
spark = SparkSession.builder \
    .appName("Basic PySpark Example") \
    .getOrCreate()

# Load a CSV file
data = spark.read.csv("path/to/your_file.csv", header=True, inferSchema=True)

# Select columns and filter data
data = data.select("column1", "column2")
filtered_data = data.filter(data["column1"] > 100)

# Group by a column and count occurrences
grouped_data = data.groupBy("column2").count()

# Show results
filtered_data.show()
grouped_data.show()

# Stop the Spark session
spark.stop()
