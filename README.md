# CyberRecon - Advanced Reconnaissance Toolkit

<div align="center">

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20Windows%20%7C%20macOS-lightgrey.svg)

**A comprehensive and modular reconnaissance tool designed for cybersecurity professionals and penetration testers.**

[Features](#features) • [Installation](#installation) • [Usage](#usage) • [Documentation](#documentation) • [Contributing](#contributing)

</div>

## 🚀 Key Features

### 🔍 Passive Reconnaissance
- **WHOIS Lookup**: Gather detailed domain registration info.
- **DNS Enumeration**: Query all record types (A, AAAA, MX, NS, TXT, SOA, CNAME).
- **Subdomain Discovery**: Utilize Certificate Transparency logs and threat intelligence sources.

### 🎯 Active Reconnaissance
- **Port Scanning**: Leverage socket-based scanning and Nmap integration.
- **Banner Grabbing**: Identify services and versions running on open ports.
- **Technology Detection**: Detect web frameworks and server technologies.

### 📊 Reporting & Analysis
- **Multiple Formats**: Export reports in text, HTML, or JSON formats.
- **Comprehensive Analysis**: Includes executive summaries and detailed technical findings.
- **Timestamped Results**: Complete audit trail with IP resolution.

### ⚡ Advanced Features
- **Modular Architecture**: Run individual modules independently.
- **Parallel Processing**: Optimized for high-performance async operations.
- **Rate Limiting**: Built-in throttling to ensure respectful API usage.
- **Error Resilience**: Handles network interruptions gracefully.
- **Docker Support**: Ready-to-use containerized deployment.

## 📋 System Requirements

- Python 3.8 or higher
- Nmap (for advanced port scanning)
- Internet connection (for API-based modules)

## 🔧 Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd task1
Install required Python libraries:

bash
Copy
Edit
pip install -r requirements.txt
Install Nmap (optional but recommended):

Ubuntu/Debian:

bash
Copy
Edit
sudo apt-get install nmap
CentOS/RHEL:

bash
Copy
Edit
sudo yum install nmap
Windows:
Download from Nmap.

macOS:

bash
Copy
Edit
brew install nmap
📖 Usage Instructions
Basic Command
bash
Copy
Edit
python main.py --target example.com --all
Individual Modules
bash
Copy
Edit
# WHOIS lookup
python main.py --target example.com --whois

# DNS enumeration
python main.py --target example.com --dns

# Subdomain discovery
python main.py --target example.com --subdomains

# Port scanning
python main.py --target example.com --portscan

# Banner grabbing
python main.py --target example.com --banners

# Technology detection
python main.py --target example.com --tech
Advanced Options
bash
Copy
Edit
# Custom port range for scanning
python main.py --target example.com --portscan --ports 1-1000

# Specify output format and file
python main.py --target example.com --all --output-format html --output-file report.html

# Adjust verbosity level
python main.py --target example.com --dns --verbose

# Silent mode
python main.py --target example.com --whois --quiet
Configuration File
The tool uses a configuration file at config/config.yaml, where you can adjust settings such as:

API Keys: For advanced subdomain discovery.

Timeouts: Configure network operation timeouts.

Rate Limits: Control the frequency of API calls.

Default Ports: Set port ranges for scanning.

User Agents: Define HTTP request headers.

Example config:

yaml
Copy
Edit
api:
  timeout: 10
  rate_limit: 1.0
  user_agent: "CyberRecon/1.0"

scanning:
  default_ports: "1-1000"
  timeout: 5
  max_threads: 100

subdomain_apis:
  - "https://crt.sh/?q=%25.{domain}&output=json"
  - "https://api.hackertarget.com/hostsearch/?q={domain}"
🎯 Available Command Line Options
Option	Description	Example
--target	Target domain or IP	--target example.com
--whois	Perform WHOIS lookup	--whois
--dns	Perform DNS enumeration	--dns
--subdomains	Discover subdomains	--subdomains
--portscan	Run port scan	--portscan
--banners	Grab service banners	--banners
--tech	Detect technologies	--tech
--all	Run all modules	--all
--ports	Specify port range	--ports 1-1000
--output-format	Set report format (text/html/json)	--output-format html
--output-file	Define output file path	--output-file report.html
--verbose	Increase output verbosity	--verbose
--quiet	Silent mode	--quiet

📊 Sample Report Outputs
Text Report
yaml
Copy
Edit
=== CyberRecon Report ===
Target: example.com
Scan Date: 2024-01-15 10:30:45

=== WHOIS Information ===
Domain: example.com
Registrar: Example Registrar Inc.
Registration Date: 2023-01-01
Expiration Date: 2025-01-01

=== DNS Records ===
A Records:
- 93.184.216.34

MX Records:
- 10 mail.example.com

=== Open Ports ===
22/tcp  SSH    OpenSSH 8.2
80/tcp  HTTP   nginx/1.18.0
443/tcp HTTPS  nginx/1.18.0

=== Security Analysis ===
• Missing security headers detected
• Outdated software versions found
• Weak SSL/TLS configuration
HTML Report
The HTML version includes:

Executive summary with risk ratings.

Expandable sections with detailed findings.

Security recommendations.

Interactive charts and graphs.

Professional design with CSS.

🏗️ Project Layout
bash
Copy
Edit
task1/
├── main.py                 # CLI entry point
├── config/
│   └── config.yaml        # Configuration file
├── modules/
│   ├── whois_module.py    # WHOIS functionality
│   ├── dns_module.py      # DNS enumeration
│   ├── subdomain_module.py # Subdomain discovery
│   ├── port_scanner.py    # Port scanning
│   ├── banner_grabber.py  # Banner grabbing
│   └── tech_detector.py   # Technology detection
├── utils/
│   ├── logger.py          # Logging utilities
│   ├── config.py          # Configuration management
│   └── network.py         # Network utilities
├── reports/
│   └── report_generator.py # Report generation
├── logs/                  # Application logs
└── requirements.txt       # Python dependencies
🔒 Security Considerations
Ethical Usage Guidelines
Authorization: Only scan systems that you own or have explicit permission to test.

Responsible Disclosure: Report any vulnerabilities found through appropriate channels.

Rate Limiting: The tool includes built-in rate limiting to prevent overloading target systems.

Legal Compliance: Ensure you comply with all local laws and regulations when using this tool.

Privacy Protection
No Data Storage: The tool does not store scan results permanently.

Anonymization: For sensitive assessments, consider using VPNs or proxies.

Log Management: Review and sanitize logs before sharing.

🐛 Troubleshooting
Common Issues
1. Permission Denied Errors

bash
Copy
Edit
# Run with appropriate permissions for port scanning
sudo python main.py --target example.com --portscan
2. DNS Resolution Failures

bash
Copy
Edit
# Check DNS configuration
nslookup example.com
3. Network Timeouts

bash
Copy
Edit
# Increase timeout in config/config.yaml
api:
  timeout: 30
4. Missing Dependencies

bash
Copy
Edit
# Reinstall requirements
pip install -r requirements.txt --force-reinstall
Debug Mode
Enable debug logging for troubleshooting:

bash
Copy
Edit
python main.py --target example.com --all --verbose
Check logs in the logs/ directory for detailed information.

🤝 Contributing
Fork the repository

Create a feature branch: git checkout -b feature-name

Commit changes: git commit -am 'Add feature'

Push to branch: git push origin feature-name

Submit a pull request

Development Guidelines
Follow PEP 8 coding standards.

Write unit tests for new features.

Ensure documentation is up-to-date.

📄 License
Distributed under the MIT License. See LICENSE for more information.

css
Copy
Edit

This structure provides a clean and comprehensive README that covers all the necessary sections to help 
