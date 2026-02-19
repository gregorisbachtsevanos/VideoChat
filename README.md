# AutoTimer — Automatic Desktop Activity Tracker (SQLite Edition)

AutoTimer is a lightweight cross-platform background activity tracker that automatically records how much time you spend on applications and websites by monitoring the active window on your system.

This version introduces **professional upgrades** including SQLite storage, idle detection, improved Linux reliability, and daemon-style execution.

---

# Features

✅ Automatic active window tracking
✅ Idle detection (keyboard + mouse inactivity)
✅ SQLite database storage (safe & scalable)
✅ Cross-platform support (Windows, macOS, Linux)
✅ Background daemon loop
✅ Reliable Linux window detection
✅ Per-activity time tracking with precise durations
✅ Crash-safe persistence

---

# Project Structure

```
project/
│
├── autotimer.py        # Main tracking engine (daemon loop)
├── activity.py         # SQLite database layer
├── linux.py            # Linux window detection
├── activities.db       # Auto-generated SQLite database
└── README.md
```

---

# How It Works

1. The app checks the active window every second.
2. Idle time is calculated using OS input detection.
3. When a window change occurs:

   * The previous activity is closed
   * A time entry is stored in SQLite
4. If inactivity exceeds the idle threshold → activity becomes **Idle**

---

# Database Schema

### activities

| column | type    |
| ------ | ------- |
| id     | INTEGER |
| name   | TEXT    |

### time_entries

| column      | type    |
| ----------- | ------- |
| id          | INTEGER |
| activity_id | INTEGER |
| start_time  | TEXT    |
| end_time    | TEXT    |
| seconds     | INTEGER |

---

# Installation

## Clone repository

```
git clone <repo-url>
cd <repo-folder>
```

---

## Platform Requirements

### Linux

```
sudo apt install x11-utils xprintidle
```

### Windows

```
pip install pywin32
```

### macOS

```
pip install pyobjc
```

---

# Usage

Run tracker:

```
python autotimer.py
```

Stop:

```
CTRL + C
```

Database file (`activities.db`) will be created automatically.

---

# Run as Background Service

### Linux

```
nohup python autotimer.py &
```

### Windows

```
pythonw autotimer.py
```

---

# Idle Detection

Idle detection measures keyboard and mouse inactivity.

Default threshold:

```
IDLE_LIMIT = 60 seconds
```

If exceeded → activity recorded as **Idle**.

You can modify this value in `autotimer.py`.

---

# Major Improvements Over Previous Version

| Feature              | Old Version        | New Version        |
| -------------------- | ------------------ | ------------------ |
| Storage              | JSON               | SQLite             |
| Idle detection       | X                  | ✓                  |
| Linux reliability    | Fragile            | Robust             |
| Background execution | Partial            | Native daemon loop |
| Data safety          | Risk of corruption | ACID-safe          |
| Analytics readiness  | Limited            | Query-ready        |

---

# Known Limitations

* Browser tab detection only tracks window titles
* Idle detection on macOS is basic
* No GUI dashboard
* No analytics interface
* No auto-startup integration
* No activity classification

---

# Future Improvements

* Browser tab deep tracking
* Analytics dashboard with charts
* Productivity scoring AI
* Weekly & monthly reports
* Automatic startup service integration
* Activity classification (productive vs unproductive)
* Screenshot sampling
* Multi-device sync
* Privacy filters
* Web dashboard

---

# Contributing

Pull requests and feature suggestions are welcome.

---

# License

MIT License
