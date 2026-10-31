# 🚢 The TitanLift

**A smart elevator simulation for a 10-floor building, built in C with a GTK GUI.**

| | |
|---|---|
| **Institute** | Cambodia Academy of Digital Technology (CADT), Institute of Digital Technology |
| **Course** | Algorithm & Computational Thinking 2 |
| **Lecturer** | Han Leangsiv |
| **Group / Team** | Group 5, Team 9 |
| **Date** | 3 July 2026 |
| **Team** | Choeun Linda • Oeurn Meylih |

---

## 📖 Overview

The RMS Titanic had four elevators: three reserved for First Class passengers and one shared by everyone else. TitanLift brings that idea of priority access into a modern building, but makes it **fair and temporary**: a verified VIP card scan gives priority only for that one trip, then the lift returns to normal service.

- The building has **10 floors**. Floor 9 is a **VIP floor** that only authorized users can reach, and Floor 10 is an exclusive rooftop sky bar. The other floors are open to everyone.
- **"Titan"** stands for something strong, powerful and reliable. **"Lift"** is the elevator itself.
- The system tracks the lift's current floor, moving direction and request queue, and gives different priorities to normal passengers and VIP cardholders.
- It was built because most traditional elevators treat every request the same, even when someone needs to get somewhere urgently.

---

## ✨ Key Features

| # | Feature | What it does |
|---|---|---|
| 1 | **Floor Request Queue (priority-based)** | Stores passenger requests and processes the highest priority first |
| 2 | **VIP Express Mode** | A card scan sends the lift directly and non-stop to Floor 9 |
| 3 | **Card Scan Authentication** | Validates VIP card IDs before granting Floor 9 access; fake or unknown cards are rejected |
| 4 | **Emergency Alarm Mode** | Stops the lift, returns it to Ground, opens the doors, and blocks card scans |
| 5 | **Passenger Capacity Limit** | Rejects entry when the lift is full: **8 passengers** or more than **560 kg** (70 kg per passenger) |

---

## ⚙️ How It Works

Request priority order: **ALARM > VIP > NORMAL**

1. The user presses a floor button or scans a VIP card.
2. **Alarm active?** If yes, a lockout message is shown.
3. **Cabin full?** If passengers ≥ 8 or weight > 560 kg, the request is rejected and logged.
4. Otherwise the request is added to the queue.
5. **VIP request in queue?** If yes, the lift goes express to Floor 9, then reverts to normal mode.
6. `moveLift()` moves the lift floor by floor using a timer.
7. The lobby door opens (passenger boards, +70 kg) and closes (passenger exits, −70 kg).
8. If more requests are in the queue, the cycle repeats. Otherwise the lift is idle.

### Main functions

| Function | Role |
|---|---|
| `add_request(int floor, priority)` | Adds a floor request to the queue |
| `scanCard(int cardID)` | Receives a scanned card ID |
| `is_valid_card()` | Checks the card ID and returns `bool` |
| `triggerAlarm(Lift*)` | Activates emergency alarm mode |
| `resetAlarm()` | Restores NORMAL mode |
| `processNextRequest()` | Picks the next request by priority (ALARM > VIP > NORMAL) |
| `get_next_request()` | Pulls the next request from the queue |
| `moveLift()` | Moves the lift floor by floor |
| `lobby_door()` | Opens and closes the doors |
| `update_shaft_display()` | Updates the shaft display after every move |

---

## 🖥️ GUI

The **TitanLift Control Panel** (built with GTK) has:

- A status bar: current floor, passengers (x/8) and weight (x kg / 560 kg)
- A **Titan Lift Shaft** view showing Ground to Rooftop, with the VIP (9) floor highlighted
- An **Activity Log** showing movement, doors opening and closing, boarding, and requests added
- **Floor buttons** (Ground to Rooftop)
- A **VIP Card Scanner** input with a Scan button
- **Trigger Alarm** and **Reset Alarm** buttons

---

## 🧰 Tech Stack

- **Language:** C 
- **GUI:** GTK

---

## ▶️ How to Run

```bash
# Install GTK development files first (example for Ubuntu/Debian)
sudo apt install libgtk-4-dev build-essential pkg-config

# Compile all C files in this folder
gcc *.c -o titanlift $(pkg-config --cflags --libs gtk4)

# Run
./titanlift
```

---

## 💡 What We Learned

- Improved our C programming skills.
- Used **structs, functions and strings** together.
- Solved a real problem from our own idea instead of only doing textbook exercises.
- Built our first GUI.
- Worked as a team and helped each other finish.

---
