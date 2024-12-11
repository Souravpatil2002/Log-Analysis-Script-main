# Log Analysis Script

## Table of Contents
1. Overview
2. Features
3. Requirements
4. Installation
5. Usage
6. Input Format
7. Output
8. Customization
9. Limitations
10. License

---

## Overview

The  **Log Analysis Script** is a Python-based tool designed to analyze web server logs for key insights. It helps in:
- Counting the number of requests per IP address.
- Identifying the most frequently accessed endpoints.
- Detecting suspicious activities like brute force login attempts.

The script is tailored for tasks involving cybersecurity, data analysis, and server monitoring.

---

## Features

### 1. Count Requests per IP Address
- Extracts all IP addresses from the log file.
- Counts the number of requests made by each IP address.
- Displays the results sorted in descending order of request counts.

### 2. Identify the Most Accessed Endpoint
- Extracts endpoints (e.g., URLs or resource paths) from the log file.
- Identifies the endpoint accessed the highest number of times and its access count.

### 3. Detect Suspicious Activity
- Searches for log entries with failed login attempts (e.g., HTTP status code `401` or "Invalid credentials").
- Flags IP addresses with failed login attempts exceeding a configurable threshold (default: 10 attempts).

### 4. Output Results
- Displays results in a readable format on the terminal.
- Saves the results in a CSV file (`log_analysis_results.csv`).

---

## Requirements

- **Python**: Version 3.8 or higher
- **Python Libraries**:
  - `os`
  - `csv`
  - `collections`

---

## Installation

1. Clone this repository or download the script file.
2. Ensure Python 3.8 or higher is installed on your system.
3. Save your log file (e.g., `sample.log`) in the same directory as the script, or note its file path for input.

---

## Usage

1. **Run the Script**:
   - From the terminal:
     ```bash
     python log_analysis.py
     ```
   - From a Jupyter Notebook:
     Execute the cells sequentially.

2. **Input the Log File Path**:
   When prompted, enter the path to your log file:
   ```plaintext
   Enter the path to the log file: sample.log

3.**View Results**:
Results will be displayed in the terminal.
Results will also be saved in a CSV file named log_analysis_results.csv.


## Input Format

The log file should adhere to a standard server log format with the following structure:
### Example Log Entries:
``192.168.1.1 - - [03/Dec/2024:10:12:34 +0000] "GET /home HTTP/1.1" 200 512 ``
``203.0.113.5 - - [03/Dec/2024:10:12:35 +0000] "POST /login HTTP/1.1" 401 128 "Invalid credentials"``
``10.0.0.2 - - [03/Dec/2024:10:12:36 +0000] "GET /about HTTP/1.1"   200 256``
- **IP Address**: Identifies the client making the request (e.g., `192.168.1.1`).
- **Timestamp**: Date and time when the request was made (e.g., `[03/Dec/2024:10:12:34 +0000]`).
- **HTTP Method**: Specifies the type of request (e.g., `GET`, `POST`).
- **Endpoint**: The resource being accessed (e.g., `/home`).
- **HTTP Version**: Specifies the protocol version (e.g., `HTTP/1.1`).
- **Status Code**: Indicates the outcome of the request (e.g., `200`, `401`).
- **Response Size**: Number of bytes in the server's response (e.g., `512`).
- **Optional Message**: Additional context for the request, such as error details.

---

## Output

### Terminal Output
The analysis generates three key results:

1. **Requests Per IP Address**:
Displays the total number of requests grouped by IP address in descending order:
2. **Most Accessed Endpoint**:
Identifies the endpoint accessed most frequently:
3. **Suspicious Activity**:
Highlights IP addresses with failed login attempts exceeding the defined threshold:

Customization
Change Suspicious Activity Threshold
By default, the script flags IPs with 10 or more failed login attempts. You can customize this value by modifying the FAILED_LOGIN_THRESHOLD in the script:
**OUTPUT**
```bash
IP Address Request Counts
203.0.113.5          8
198.51.100.23        8
192.168.1.1          7
10.0.0.2             6
192.168.1.100        5
Most Frequently Accessed Endpoint
/login (Accessed 13 times)
Suspicious Activity Detected
Results saved to log_analysis_results.csv
