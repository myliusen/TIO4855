# Code Repository: NTNU EiT TIØ4855 - Group 4 (Spring 2025) - GEEO-Flow

Code repository for Group 4's final product in the NTNU Experts in Teamwork (EiT) village TIØ4855, held during Spring 2025. This repository contains the code and data used for the microgrid cost optimization component of the GEEO-Flow project.

## Overview

This repository contains a Python implementation of a two-stage stochastic mixed-integer linear programming (MILP) model. The model aims to determine the cost-optimal investment mix of solar panels, wind turbines, run-of-river hydro units, and battery storage for an isolated microgrid. The objective is to minimize the total fixed installation cost while ensuring the energy demand is met reliably across various uncertain scenarios (based on variations in demand and renewable generation).

The implementation uses the `gurobipy` library to interface with the Gurobi Optimizer.

## Repository Contents

*   `stochastic_model.ipynb`: Jupyter Notebook containing the main Python code. This includes:
    *   Parameter definitions (costs, technical specifications).
    *   Loading and preprocessing of weather and demand data from Excel files.
    *   Scenario generation for stochastic optimization.
    *   Definition and construction of the MILP model using `gurobipy`.
    *   Execution of the Gurobi solver.
    *   Visualization of input data and optimization results.
*   `Weatherdata.xlsx`: Excel file containing hourly weather data (solar irradiance in W/m², wind speed in m/s) for the three case study locations (Canada, Kenya, Madeira) over one year.
*   `Data Demand Energy allocation EIT-year.xlsx`: Excel file containing hourly energy demand profiles (in Watts) for the three case study locations over one year. Includes both "real" and synthetically generated "random" demand profiles used in the model.
*   `README.md`: This file.

## Setup

1.  **Install Python:** Ensure you have Python installed (version 3.8+ recommended).
2.  **Install Gurobi:** Download, install, and obtain a license for the Gurobi Optimizer (free academic licenses are available from the [Gurobi website](https://www.gurobi.com/)). Ensure your Gurobi license is correctly configured.
3.  **Install Python Libraries:** Open your terminal or command prompt and install the required libraries:
    ```bash
    pip install gurobipy pandas openpyxl matplotlib jupyterlab
    ```
4.  **Clone Repository:** Get a local copy of this repository:
    ```bash
    git clone https://github.com/yourusername/your-repo-name.git # Replace with your actual repo URL
    cd your-repo-name
    ```

## Usage

1.  Ensure the Excel data files (`Weatherdata.xlsx` and `Data Demand Energy allocation EIT-year.xlsx`) are located in the same directory as the `stochastic_model.ipynb` notebook.
2.  Start Jupyter Notebook from your terminal or using an IDE within the repository directory.
3.  Open the `stochastic_model.ipynb` file in the Jupyter interface.
4.  **Select Location:** Modify the `LOCATION` variable near the top of the notebook code to choose the case study: `"kenya"`, `"canada"`, or `"madeira"`.
5.  **Parameter tuning:** Generation source parameters for each case must be tuned using the highlighted text provided in the code. 
6.  Run the notebook cells sequentially from top to bottom. The Gurobi optimizer will solve the MILP problem, which may take some time depending on your hardware.

## Input Data

*   **Weather Data (`Weatherdata.xlsx`):** Contains hourly solar irradiance (W/m²) and wind speed (m/s). Specific columns are selected based on the chosen `LOCATION`.
*   **Demand Data (`Data Demand Energy allocation EIT-year.xlsx`):** Contains hourly demand profiles (W). The model uses the 'Random Demand' columns corresponding to the chosen `LOCATION`.

*Note: Specific sheet names and column headers used are detailed within the notebook.*

## Output

Executing the notebook will:
*   Print the optimal investment results to the standard output:
    *   Solar panel area (m²).
    *   Number of wind turbines.
    *   Number of hydro units.
    *   Battery capacity (kWh).
    *   Minimized total fixed investment cost (USD).
*   Display plots visualizing:
    *   Weekly averaged input data (Solar, Wind, Hydro potential, Demand).
    *   Weekly averaged optimal generation mix and battery usage.
    *   Detailed hourly operation for a sample week under low, medium, and high scenarios.

## Model Formulation

The underlying mathematical model is a two-stage stochastic MILP. For the complete mathematical formulation, discussion of parameters, assumptions (e.g., constant hydro flow, simplified costs), and limitations, please refer to the main project report.

## Disclaimer

This README file was generated using generative artificial intelligence.
