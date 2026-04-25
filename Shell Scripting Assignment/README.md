# Shell Scripting Assignment — Intrusion Detection System

## Files

```
Shell Scripting Assignment/
├── sanitize.sh                  # Task 1 — log cleaner
├── detect.sh                    # Task 2 — brute force detector
├── report.sh                    # Task 3 — port analysis dashboard
├── timeline.sh                  # Task 4 — hourly threat timeline
├── auth.log.txt                 # Sample raw authentication log
├── whitelist.txt.txt            # Trusted IP addresses
├── Shell Scripting Question.pdf
└── README.md
```

## Running the Pipeline

The four scripts are meant to be run in order. Each feeds into the next.

### Step 1 — Sanitize the raw log

```bash
bash sanitize.sh auth.log.txt
# Output: clean_log.csv
```

### Step 2 — Detect attackers and generate firewall rules

```bash
bash detect.sh clean_log.csv whitelist.txt.txt firewall_rules.sh
# Output: firewall_rules.sh (iptables DROP rules for attackers above threshold)
```

### Step 3 — Print port analysis to terminal

```bash
bash report.sh clean_log.csv
```

### Step 4 — Print hourly attack timeline to terminal

```bash
bash timeline.sh clean_log.csv
```

## Script Reference

| Script | Input(s) | Output | What it does |
|--------|----------|--------|--------------|
| `sanitize.sh` | `auth.log.txt` | `clean_log.csv` | Strips corrupt lines, anonymizes root/admin, normalizes `\|` → `,` |
| `detect.sh` | `clean_log.csv`, `whitelist.txt.txt`, output filename | `firewall_rules.sh` | Counts failed logins per IP; blocks non-whitelisted IPs with >10 failures |
| `report.sh` | `clean_log.csv` | stdout | Table of targeted ports across all failed attempts |
| `timeline.sh` | `clean_log.csv` | stdout | Failed attempt count grouped by hour (00–23) |

## Notes

- `whitelist.txt.txt` — note the double extension; pass the full filename as-is when calling `detect.sh`
- `firewall_rules.sh` is generated fresh each run; delete it before re-running `detect.sh` if you want a clean slate
- All scripts require standard GNU tools: `sed`, `awk`, `grep`, and `sort` — no additional installs needed
