🛡️ Endpoint Process Watchdog

Real-Time Process Monitoring & Automatic Threat Response

Endpoint Process Watchdog is a lightweight endpoint-security tool that continuously monitors running processes on a host and automatically takes action when suspicious or unauthorized processes appear.

Built for SOC analysts, IR workflows, and blue-team environments.
Perfect for detecting unexpected binaries, rogue scripts, malware processes, or unauthorized admin tools before they cause damage.

🚀 Features
🔍 Real-Time Process Monitoring

Continuously scans active processes on the endpoint and flags anything unexpected or unapproved.

⚔️ Automatic Threat Response

Terminate, log, or quarantine suspicious processes based on your configuration.

📁 Custom Whitelist / Blacklist

Define trusted processes and blocklisted process names, hashes, or paths.

📣 Alerting

Send alerts via:

Console output

Log file

Optional Discord webhook

Optional email notifications

🧠 SOC / IR Oriented

Designed to simulate real endpoint detection behavior without needing a full EDR platform.

🖥️ What It Detects

Endpoint Process Watchdog can identify:

Unauthorized admin tools (e.g., nmap, nc, msfconsole)

Suspicious shells (bash, sh, python, powershell) in unusual locations

Malware-like behavior (rapid spawning, child-process chains)

Processes running from /tmp, /dev/shm, or weird directories

High-risk processes not in the whitelist

Name-spoofed processes (svch0st, cr0n, etc.)

🛠️ How It Works

Monitors running processes at a set interval

Compares running processes against:
✔ Allowed whitelist
✔ Blocked blacklist

Creates detailed logs for SOC triage

Takes action if configured to do so (kill/alert/log)

📦 Installation

Clone the project:

git clone https://github.com/<YOUR-USERNAME>/endpoint-process-watchdog
cd endpoint-process-watchdog


Install required Python packages:

pip install psutil requests

⚙️ Configuration

Create or edit config.json:

{
  "whitelist": [
    "systemd",
    "python3",
    "bash",
    "sshd",
    "gnome-shell"
  ],
  "blacklist": [
    "nmap",
    "nc",
    "msfconsole",
    "svch0st",
    "malware.py"
  ],
  "scan_interval": 3,
  "discord_webhook": "",
  "email_alerts": false
}

Config Options
Option	Description
whitelist	Processes allowed to run
blacklist	Processes that trigger immediate alerts
scan_interval	How often the monitor scans processes
discord_webhook	Optional: Send alerts to Discord
email_alerts	Optional: Enable email notifications
🟣 Using the Watchdog
Run the Monitor
sudo python3 watchdog.py


Recommended to run as root for full process visibility.

🔔 Alert Example

When a blacklisted or unknown process appears:

[ALERT] Suspicious process detected!
Name: nmap
PID: 1421
Path: /usr/bin/nmap
Action: TERMINATED
Timestamp: 2025-11-23 01:34:12

📸 Screenshots

Add images to your /images folder and replace these:

![](images/watchdog_running.png)
![](images/alert_detected.png)
![](images/terminated_process.png)


📋 Notice

Requires Python 3.7+

Requires elevated permissions for full process visibility

Does not replace an enterprise EDR — it is for training, detection logic, and SOC readiness

👤 Author

Malik Lewis
Cybersecurity | SOC | Incident Response | Detection Engineering
