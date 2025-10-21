# Chinook Sales Simulator

This project is a synthetic sales data generator for the Chinook database. It's designed to simulate daily sales transactions (D-1) to provide a dynamic data source for ETL/ELT pipelines.

## Features

*   Generates a configurable number of sales for the previous day (D-1).
*   Distributes sales randomly throughout the 24-hour period.
*   Ensures data integrity by using a single database transaction for the entire batch.
*   Connects securely to a Neon database using `neonctl`.

## Requirements

*   Python 3.11+
*   [uv](https://docs.astral.sh/uv/)
*   [neonctl](https://neon.com/docs/reference/neon-cli)
*   A running instance of the [Chinook database] (https://neon.com/docs/import/import-sample-data) on Neon.

## Setup

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd chinook_db
    ```

2.  **Create a `.env` file:**
    Create a `.env` file in the root of the project with your Neon credentials:
    ```
    NEON_ORG_ID=<your-neon-org-id>
    NEON_PROJECT_ID=<your-neon-project-id>
    ```

3.  **Install dependencies:**
    ```bash
    uv sync
    ```

## Usage

To run the simulation, execute the following command, replacing `<number_of_sales>` with the desired amount:

```bash
echo "<number_of_sales>" | uv run python d1_sales_simulator.py
```

For example, to generate 10 sales:

```bash
echo "10" | uv run python d1_sales_simulator.py
```
