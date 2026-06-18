# Wireless IoT & 5G Network Performance Dataset Collection

## Overview

This repository contains experimentally generated datasets from Raspberry Pi–based IoT communication systems over multiple networking environments, including **5G, Wi-Fi, and MQTT-based cloud communication**.

The datasets are designed for analyzing **end-to-end network performance, latency behavior, and IoT sensor data transmission under varying traffic periodicities and network conditions**.

---

## Experimental Setup

The system consists of:

- **Raspberry Pi** as the IoT data generator and sender  
- **DHT11 sensor** used to measure environmental parameters  
- **UE (User Equipment / Mobile Phone)** connected via USB tethering  
- **5G Core / MEC system** for processing and forwarding data  
- **Laptop receiver over Wi-Fi**  
- **External MQTT broker (cloud-based)** for internet-based message routing  

---

## Sensor Details

Environmental data is collected using the **DHT11 temperature and humidity sensor**:

- Temperature (°C)
- Humidity (%)

These values are embedded into each transmitted packet along with network performance metrics.

---

## Data Collection Scenarios

### 1. 5G Network Experiments (Pi → UE → 5G System)

- Data transmitted from Raspberry Pi to UE via USB tethering  
- UE forwards packets to 5G system  
- End-to-end transmission over 5G infrastructure  
- Each experiment run for **10 minutes**  

#### Periodicities Tested:

- 0.025 s  
- 0.05 s  
- 0.1 s  
- 0.2 s  
- 0.5 s  
- 1 s  
- 2 s  
- 5 s  
- 10 s  

Each periodicity corresponds to a separate dataset capturing network behavior under different traffic loads.

---

### 2. Wi-Fi Experiment (Pi → Laptop)

- Raspberry Pi transmits packets to a laptop over Wi-Fi  
- UDP communication with ACK-based RTT measurement  
- One-way latency computed using **RTT/2 method**  
- Metrics include latency, throughput, and PRR  
- Single continuous log file generated  

---

### 3. MQTT-Based Cloud Communication

- Raspberry Pi publishes sensor data to an **external MQTT broker over the internet**  
- Data is routed from broker to:
  - 5G MEC system  
  - Monitoring/analytics nodes  
- Used to evaluate **cloud-to-edge latency and reliability**

---

## Parameters Captured

Across datasets, the following metrics are recorded:

- Packet ID  
- Timestamp  
- Temperature (°C) *(from DHT11 sensor)*  
- Humidity (%) *(from DHT11 sensor)*  
- Packet Size (bytes)  
- One-way Latency (computed using RTT/2 where applicable)  
- Throughput (bits/s or kbps depending on experiment)  
- Packet Reception Ratio (PRR)  
- PRB utilization (for 5G experiments)  

---
