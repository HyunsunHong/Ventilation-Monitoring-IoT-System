# Ventilation Monitoring IoT System  
*Multi-sensor-based Collaborative Ventilation System for Preventing Respiratory Infections in Public Spaces*

## Overview
This project implements an **IoT-based collaborative ventilation monitoring system** designed to prevent the spread of respiratory infections (e.g., COVID-19) in **public spaces** such as libraries, classrooms, and offices.  

The system uses **temperature, humidity, and CO₂ sensors** to monitor indoor air quality and applies **machine learning models** to determine whether ventilation is required. When poor ventilation is detected, the system provides **real-time notifications** via a web interface, encouraging users to cooperate in ventilating the space.

This repository contains the full implementation described in the paper:  
*“Multi-sensor-based Collaborative Ventilation Systemfor Preventing Respiratory Infections in Public Spaces”* (2023)

---

## System Architecture
The system consists of three main components:

1. **Sensor Nodes**  
   - Devices installed in the monitored space.  
   - Equipped with:
     - Temperature & Humidity Sensor (DHT11)  
     - CO₂ Sensor (CM1106)  
   - Collects environmental data without compromising privacy.  
   - Sends readings to the Sensor Server via **MQTT**.

2. **Sensor Server**  
   - Aggregates sensor data from multiple nodes.  
   - Uses **Random Forest Classifier** (via scikit-learn) to determine ventilation status.  
   - Publishes ventilation alerts when poor air quality is detected.

3. **Web Server**  
   - Provides a user-friendly web interface.  
   - Built with **PHP, HTML, CSS, JavaScript**.  
   - Sends **real-time browser notifications** (web push) to subscribed users.  
   - Allows administrators to configure sensors, collect datasets, and train ML models.



 

---

## Getting Started

### Prerequisites
- Hardware:
  - Raspberry Pi 3 Model B+ (or similar)  
  - DHT11 sensor  
  - CM1106 CO₂ sensor  
- Software:
  - Python 3.x  
  - [scikit-learn](https://scikit-learn.org)  
  - [paho-mqtt](https://pypi.org/project/paho-mqtt/)  
  - PHP / Apache or Nginx for web server  

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/HyunsunHong/Ventilation-Monitoring-IoT-System.git
   cd Ventilation-Monitoring-IoT-System
   ```

2. Configure MQTT broker (e.g., Mosquitto).

3. Deploy the **Sensor Server** and connect **Sensor Nodes**.

4. Set up the **Web Server** and configure user accounts.

---

## Example Workflow
1. Sensor nodes periodically send temperature, humidity, and CO₂ values.  
2. The sensor server aggregates data and applies the trained Random Forest model.  
3. If ventilation is required, the server publishes a ventilation alert.  
4. The web server delivers a **push notification** to subscribed users’ browsers.  
5. Occupants ventilate the space collaboratively.  

---

## Case Study
- Test environment: 24.5 m² room with 2 openings (door, window).  
- Deployed 2 sensor nodes (near door & window).  
- Collected **661 data points** over 12 ventilation cycles.  
- Achieved:
  - Accuracy: **84.09%**  
  - Precision: **78.57%**  
  - Recall: **83.02%**  
  - F1-score: **81.00%**  

---

