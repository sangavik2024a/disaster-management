# Disaster Management System

## Overview

This project implements a real-time disaster monitoring and alert system focused on flood-risk scenarios. It integrates live weather data from the internet, on-site water level monitoring using an ultrasonic sensor, and human presence detection using a camera module.

The system is built around an ESP32 microcontroller, which evaluates environmental and local sensor data. When critical thresholds are exceeded and a human presence is detected, the ESP32 sends an alert to a shared dashboard used by volunteers, NGOs, and government rescue operators. The goal is to reduce response time during emergencies and prioritize rescue efforts where human life is at risk.

---

## Project Structure

```
disaster-management/
│
├── main/            # Core backend logic and system integration
├── dashboard/       # Shared web dashboard for alerts and monitoring
├── weatherapi/      # Live weather data retrieval and processing
├── cvdetection/     # Human detection using camera module
└── README.md
```

---

## System Components

### Weather API Module (`weatherapi/`)

* Fetches live weather data from an online API.
* Monitors:

  * Wind speed
  * Rainfall (in cm)
* Compares values against predefined danger thresholds.
* Acts as the first stage of risk evaluation.

### Water Level Detection (Ultrasonic Sensor)

* Ultrasonic sensor is deployed at a flood-prone location.
* Continuously measures water level.
* Detects when water exceeds a defined danger limit.
* Provides localized real-time flood data.

### Human Detection (`cvdetection/`)

* Uses a camera module for detecting human presence.
* Ensures alerts are triggered only when people are present.
* Helps reduce false alarms in unoccupied areas.

### ESP32 Control Logic

The ESP32 acts as the central controller. It triggers an alert only when all three conditions are met:

1. Weather parameters exceed threshold.
2. Water level is above the danger limit.
3. Human presence is detected.

If these conditions are satisfied, the ESP32 sends an alert to the shared dashboard.

---

## Dashboard (`dashboard/`)

The web dashboard is accessible to:

* Volunteers
* NGOs
* Government rescue operators

It displays:

* Active alerts
* Weather conditions
* Water level status
* Risk location details

This centralized interface improves coordination and speeds up critical response actions.

---

## Working Logic

The alert mechanism follows a multi-condition validation approach:

* Severe weather detected from live API data.
* Dangerous water level confirmed by ultrasonic sensor.
* Human presence verified through camera detection.

This layered verification ensures accurate risk identification and minimizes false positives.

---

## Hardware Requirements

* ESP32 microcontroller
* Ultrasonic sensor
* Camera module
* Internet connectivity (for weather API)

---

## Applications

* Flood-prone regions
* Riverbank monitoring
* Urban drainage systems
* Disaster early-warning systems

---

## Objective

The primary objective of this system is to save time during critical rescue operations by combining environmental intelligence with real-time on-site sensing and human detection. It prioritizes alerts where human lives are at risk and enables faster, coordinated disaster response.
