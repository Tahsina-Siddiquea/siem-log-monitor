# SIEM Log Monitor (Python)

A Python-based cybersecurity utility designed to inspect system and application log files to identify indicators of malicious activity.
This project demonstrates practical defensive security techniques including threat detection logic, event correlation, pattern matching, and automated reporting.


## Project Overview

Modern computing environments generate extensive logs that contain valuable forensic evidence of security incidents.
Manually analyzing these logs is inefficient and error-prone.

This project introduces an automated approach to log inspection by parsing event records and identifying patterns commonly associated with cyberattacks such as brute-force attempts, injection activity, and unauthorized access.

The tool was developed to simulate real-world tasks performed by Security Operations Center (SOC) analysts.


## Key Features

### Brute-Force Detection

Counts failed login attempts per IP address and raises alerts when a threshold is exceeded.

### SQL Injection Detection

Uses pattern matching to identify common SQL injection payloads such as:

* ' OR '1'='1
* --
* ;
* logical OR/AND injection attempts

### Suspicious Endpoint Monitoring

Detects access attempts to high-risk URLs like:

* /admin
* /wp-admin
* /login
* /config

### Automated Security Reporting

Generates a readable report including:
* Analysis timestamp
* Total log lines analyzed
* Brute-force alerts
* SQL injection alerts
* Suspicious endpoint access

Report is saved automatically as: `security_report.txt`

## Project Structure
```
log-monitor/
│
├── log_analyzer.py      # Main analyzer script
├── sample_log.txt       # Example log file for testing
├── security_report.txt  # Generated report (after running)
└── README.md
```

## Requirements

* Python 3.x
* No external libraries required



## Usage

### Run the analyzer
```
python log_analyzer.py sample_log.txt
```

### Example Output
```
===== SECURITY LOG ANALYSIS REPORT =====
Analysis Time: 2026-03-10
Total Log Lines Analyzed: 6

---- Brute Force Detection ----
[ALERT] 192.168.1.5 - 3 failed login attempts

---- SQL Injection Attempts ----
[ALERT] 10.0.0.1 - Suspicious Query detected

---- Suspicious Endpoint Access ----
[WARNING] 172.16.0.8 accessed /admin
```
## Screenshots
![Terminal Output](terminal.png)
![Generated Report](report.png)

## Configuration
You can adjust detection sensitivity inside the script:
```
FAILED_LOGIN_THRESHOLD = 3
```
You can also modify:

* SQL injection patterns
* Suspicious endpoints list

to match real-world environments.



## Performance Considerations

The analyzer is optimized for sequential log processing and can handle moderately large datasets efficiently.
Performance may vary depending on log size and pattern complexity.

Potential optimizations include:

* Streaming analysis pipelines
* Multiprocessing for large-scale datasets
* Integration with real-time log feeds

## Security & Ethical Use

This tool is intended for:

* Cybersecurity education
* Incident response simulations
* Authorized log auditing
* Defensive research activities

Unauthorized analysis of sensitive operational logs may violate privacy or regulatory policies.


## Learning Outcomes

Developing this project strengthens understanding of:

* Event correlation techniques
* Intrusion detection logic
* Pattern-based threat identification
* Security monitoring workflows
* Automation of defensive analysis tasks



## Author

This project was created as part of a cybersecurity learning portfolio to gain hands-on experience in defensive security tooling and incident investigation methodologies.


## License

Provided for educational and research purposes.
Users are encouraged to adapt and extend the analyzer within controlled and authorized environments.
