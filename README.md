 
# Power Monitor - Technical Documentation

## Overview
The **Power Monitor** is a Python-based tool designed to track the resource usage and power consumption of a specific application on your computer. Whether you're analyzing performance, optimizing energy efficiency, or debugging an application, this tool provides real-time insights into CPU usage, memory consumption, and estimated power draw.

The project is structured into multiple modules, each responsible for a specific function:
- `monitor.py` – The main script that runs the monitoring process.
- `process_tracker.py` – Tracks CPU, memory, and GPU usage.
- `power_logger.py` – Logs performance data into a CSV file.
- `list_process.py` – Lists currently running processes.



## Features
- **Monitor a Specific Application** – Enter the name of any running application, and the tool will track its resource consumption.
- **Baseline Power Measurement** – Establishes system power usage at idle to provide accurate application-specific estimates.
- **Real-time Performance Logging** – Saves CPU, RAM, and GPU usage data into `performance_log.csv`.
- **Data Visualization** – Generates graphs showing trends in resource consumption.
- **Error Handling** – Manages terminated processes and inaccessible applications gracefully.



## Codebase Breakdown

### 1. `monitor.py` (Main Script)
This is the central script that:
- Takes user input for the process to monitor.
- Identifies the application's PID (Process ID).
- Collects CPU, RAM, and GPU usage.
- Logs data and displays real-time statistics.
- Calls `power_logger.py` to store performance logs.

### 2. `process_tracker.py` (Tracks Application Resource Usage)
Handles tracking for CPU, RAM, and GPU usage.

Key functions:
- `get_process_pid(process_name)`: Finds the process ID based on the given name.
- `get_process_cpu_ram_usage(pid)`: Fetches CPU and RAM consumption.
- `get_gpu_usage()`: Retrieves GPU load and power consumption (for NVIDIA GPUs).

### 3. `power_logger.py` (Logs Data to CSV)
Handles logging power-related metrics into `data/performance_log.csv`.

Key functions:
- `log_power_usage(process_name, cpu_usage, ram_usage, gpu_usage, gpu_power)`: Stores real-time performance data into a CSV file.

### 4. `list_process.py` (Lists Running Processes)
Displays all currently running applications to help users identify the process they want to monitor.

Key function:
- `list_running_processes()`: Retrieves all active process names and their PIDs.



## How It Works
1. **User Input** – You enter the name of the application you want to monitor (e.g., `chrome.exe`).
2. **Process Identification** – The script finds the corresponding process and starts tracking its resource usage.
3. **Monitoring** – The tool logs CPU, RAM, and GPU usage in real time, updating every few seconds.
4. **Logging & Graphing** – Data is saved into `performance_log.csv`, and a graph is generated for visual analysis.



## Project Structure
```
POWER_MONITOR/
├── .venv/                  # Virtual environment (optional)
├── data/
│   ├── performance_log.csv # Logs resource usage
│   ├── performance_graph.png # Auto-generated performance graph
├── docs/                   # Documentation
├── src/
│   ├── monitor.py          # Main script
│   ├── power_logger.py     # Logs power consumption
│   ├── process_tracker.py  # Tracks process resource usage
│   ├── list_process.py     # Lists all running processes
├── README.md               # Project documentation
```



## Running the Project

### 1. Install Dependencies
Make sure you have the required Python packages:
```sh
pip install psutil GPUtil tabulate
```

### 2. Run the Monitoring Script
```sh
python src/monitor.py
```

### 3. Enter the Application Name
When prompted, type the name of the application you want to monitor (e.g., `chrome.exe`).

### 4. View Results
- **CSV Log**: `data/performance_log.csv`
- **Graph Visualization**: `data/performance_graph.png`



## Key Highlights
- **Accurate Resource Tracking** – Monitors CPU, RAM, and GPU in real-time.
- **TDP-Based Power Estimation** – Estimates power draw based on system specifications.
- **User-Friendly Output** – Presents data in a clear, tabulated format.
- **Automated Graphing** – Generates a performance trend graph for better analysis.



## Conclusion
The **Power Monitor** project is a handy tool for developers, system analysts, and anyone looking to optimize application performance and energy efficiency. With its modular design, real-time tracking, and automated logging, it provides valuable insights in an easy-to-use format.
