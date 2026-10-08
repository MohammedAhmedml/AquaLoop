# AquaLoop — Intelligent Water & Energy Recovery for Sustainable Data-Centre Cooling

> A circular water-recovery and micro-energy-harvesting system for sustainable data-centre cooling infrastructure.

---

## Problem Statement

Modern high-density data centres and AI compute clusters generate immense thermal loads requiring continuous, large-scale cooling. Evaporative cooling towers and once-through liquid cooling loops demand millions of litres of freshwater daily. This operational model leads to two major inefficiencies:

1. **Water Consumption & Waste:** Vast quantities of freshwater are continuously consumed, contaminated with dissolved solids, thermal pollution, or biological agents, and discharged into wastewater streams rather than being continuously recirculated.
2. **Uncaptured Parasitic Energy:** Significant kinetic energy within high-velocity cooling water conduits, as well as acoustic energy from high-decibel environmental and equipment noise (fans, chillers, pumps), dissipates uncaptured into the surrounding environment.

There is a critical need for an integrated, closed-loop cooling infrastructure capable of recovering waste cooling water for re-use while harvesting ambient kinetic and acoustic energy to power low-power monitoring electronics.

---

## Why This Problem Matters

* **Resource Scarcity:** Data centres are increasingly located in water-stressed regions, where high freshwater abstraction places strain on local municipal supplies and ecosystems.
* **Environmental & Regulatory Pressure:** Stricter environmental regulations and ESG mandates require data centre operators to lower Water Usage Effectiveness (WUE) and overall carbon intensity.
* **Operational Resilience:** On-site water treatment and circular recovery reduce dependency on external water utilities, mitigating risks associated with supply disruption or municipal restrictions.
* **Parasitic Load Offsetting:** Harvesting residual hydraulic and acoustic kinetic energy allows auxiliary monitoring and telemetry systems to operate with reduced dependence on primary grid power.

---

## Proposed Solution

**AquaLoop** is an integrated, bench-scale proof-of-concept system designed to demonstrate circular water recovery and micro-energy harvesting for data-centre cooling environments. 

The system implements a dual-stage water-energy recovery path, a multi-barrier physical and optical water treatment loop, and a piezoelectric acoustic energy harvesting circuit. Real-time system diagnostics are managed via an embedded microcontroller network that aggregates sensor telemetry (flow, temperature, water quality, and power output) for local control and remote dashboard monitoring.

```
       +-----------------------------------------------------------------------+
       |                                                                       |
       v                                                                       |
[Fresh/Makeup Water] ---> [Stage 1 Energy Harvest] ---> [Cooling Load Sim]     |
                                                               |               |
                                                               v               |
[Recovered Water Reuse] <-- [UV] <-- [RO] <-- [Carbon] <-- [Stage 2 Energy Harvest]
```

---

## Key Features

* **Multi-Stage Circular Water Recovery:** Sequential mechanical carbon filtration, Reverse Osmosis (RO) separation, and Ultraviolet (UV) disinfection to condition discharged cooling water for continuous reuse within the secondary cooling loop.
* **In-Line Hydraulic Micro-Energy Harvesting:** Dual mini-turbine installations positioned prior to the thermal exchange interface and post-discharge to convert fluid kinetic energy into electrical energy.
* **Acoustic / Environmental Noise Harvesting:** Piezoelectric transducer array with dedicated rectification and passive voltage conditioning designed to harvest parasitic acoustic energy from high-decibel cooling fans and ambient equipment noise.
* **Embedded Telemetry & Operational Control:** Sensor-driven embedded telemetry platform monitoring system hydraulics, thermal parameters, power generation, and water quality parameters.
* **Telemetry Dashboard:** Remote data visualization interface displaying real-time sensor metrics, power harvesting outputs, and system operating states.

---

## Innovation and Novelty

* **Dual-Domain Energy Harvesting Integration:** Unifies fluid kinetic energy capture (hydraulic micro-turbines) and ambient structural/acoustic energy capture (piezoelectric arrays) into a single auxiliary power conditioning bus.
* **Closed-Loop Hydraulic Architecture:** Integrates energy harvesting hardware directly into the fluid circuit without causing severe head loss that would compromise primary cooling function.
* **Integrated Process Diagnostics:** Combines physical water treatment with multi-point sensor telemetry (turbidity, TDS, flow, temperature) at a bench-scale proof-of-concept level.

---

## Complete System Workflow

1. **Hydraulic Conditioning & Initial Harvesting:** Water enters the cooling loop and passes through the Stage 1 hydraulic micro-turbine, driving an inline generator to harvest kinetic energy prior to entering the heat absorption interface.
2. **Thermal Exchange Simulation:** Water passes across the thermal exchange load (simulated data-centre heat load), absorbing thermal energy.
3. **Post-Discharge Recovery & Stage 2 Harvesting:** Heated discharge water flows through Stage 2 hydraulic harvesting to capture residual fluid kinetic energy.
4. **Physical & Chemical Water Treatment:** Water flows sequentially through a granular activated carbon filter to remove organics and chlorine, an RO membrane for dissolved solids filtration, and a UV sterilization chamber for biological decontamination.
5. **Acoustic Energy Harvesting (Parallel Path):** Ambient acoustic noise generated by cooling equipment vibrates a piezoelectric transducer matrix; output AC voltage is rectified, conditioned, and routed to an energy management unit.
6. **Sensing & Telemetry Logging:** Inline sensors continuously sample process parameters (flow rate, temperature, TDS/turbidity, voltage/current) and stream data to the microcontroller for process monitoring and telemetry upload.
7. **Recirculation:** Purified water is routed back to the primary supply reservoir for continuous closed-loop reuse.

---



## Technology Stack

### Hardware
* **Microcontrollers:** ESP32 / Arduino Uno
* **Sensors:** Hall-effect flow sensors (YF-S201), DS18B20 digital temperature sensors, analog TDS sensor module, analog turbidity sensor, analog pH sensor, INA219 current/voltage monitor.
* **Fluid Handling:** 12V DC diaphragm/submersible pump, food-grade silicone tubing, mini hydraulic turbine units with DC generators.
* **Water Treatment:** Inline activated carbon cartridge, low-pressure RO membrane filter housing, 12V mini UV-C LED sterilization module.
* **Energy Harvesting & Circuitry:** Piezoelectric ceramic discs (27mm), MB10F bridge rectifiers, LM2596 / TP4056 buck-boost & charge controller modules, storage capacitors.

### Software
* **Embedded Firmware:** C / C++ (Arduino IDE / PlatformIO framework)
* **IoT Protocols:** MQTT / HTTP REST APIs
* **Dashboard / Visualization:** Node-RED / Grafana / Web Dashboard (HTML5, CSS3, JavaScript, Chart.js)
* **Version Control:** Git & GitHub

---

## Hardware Components

| Component | Function / Purpose | Specifications / Details | Status |
| :--- | :--- | :--- | :--- |
| **ESP32 Microcontroller** | System control, sensor data acquisition, Wi-Fi telemetry | Dual-core 240MHz, 3.3V logic, integrated Wi-Fi/BLE | Implemented |
| **DC Water Pump** | Drives fluid circulation across treatment stages | 12V DC, 3-5 L/min flow capacity | Implemented |
| **Hall-Effect Flow Sensor** | Measures volumetric fluid flow rate | YF-S201, 1-30 L/min range, pulse output | Implemented |
| **DS18B20 Temp Sensor** | Measures inlet, heat-load, and discharge temperatures | OneWire digital interface, -55°C to +125°C range | Implemented |
| **Analog TDS Sensor** | Monitors total dissolved solids in water loop | 0-1000 ppm detection range, 0-2.3V output | Prototype Demonstration |
| **Analog Turbidity Sensor**| Detects suspended particulates in discharge water | Optical light disruption detection module | Prototype Demonstration |
| **Mini Water Turbines** | Converts water flow kinetic energy to electricity | Inline 12V DC mini hydro-generator units | Implemented |
| **Piezoelectric Transducers**| Harvests ambient acoustic/vibration energy | 27mm ceramic piezoelectric discs arranged in array | Prototype Demonstration |
| **Power Conditioning Board**| Rectifies, filters, and regulates harvested micro-power| Bridge rectifier + step-up/down buck-boost board | Implemented |
| **Activated Carbon Filter** | Removes organic contaminants and chlorine | In-line mini filter cartridge | Implemented |
| **RO Membrane Module** | Filtration of dissolved ions and fine particulates | Bench-scale low-pressure membrane element | Prototype Demonstration |
| **UV-C Sterilization Module**| Neutralizes biological contaminants | 254nm UV-C LED / low-voltage module | Prototype Demonstration |
| **I2C OLED Display** | Local visual monitoring of sensor readouts | 0.96-inch 128x64 OLED display screen | Implemented |

---

## Software Components

| Component / Library | Function / Purpose | Tech Stack / Dependencies | Status |
| :--- | :--- | :--- | :--- |
| **Embedded Control Firmware** | Sensor polling, GPIO management, safety cut-off logic | C++ / Arduino Framework | Implemented |
| **WiFi / Network Manager** | Handles network connectivity and reconnection routines | `WiFi.h` / `PubSubClient.h` | Implemented |
| **Sensor Processing Engine** | Filters ADC noise, calculates calibrated metrics | Custom C++ DSP functions | Implemented |
| **Local Web Server** | Serves real-time status page over local IP | `ESPAsyncWebServer.h` | Prototype Demonstration |
| **Telemetry Dashboard** | Visualizes historical and real-time process data | HTML5 / JavaScript / Chart.js | Prototype Demonstration |
| **MQTT Broker Integration** | Transmits telemetry payloads to cloud/local broker | MQTT protocol, JSON payload formatting | Proposed / Future Enhancement |
| **Predictive Optimization Engine**| AI-driven dynamic flow & power balancing | Python / Scikit-Learn (Planned) | Proposed / Future Enhancement |

---

## Water Treatment Methodology

The AquaLoop water recovery platform utilizes a multi-barrier treatment system engineered for bench-scale cooling water recovery:

1. **Granular Activated Carbon (GAC) Filtration:** Serves as primary physical treatment. Water passes through a bed of activated carbon to adsorb dissolved organic compounds, residual chlorine, and large particulate impurities that could foul downstream membranes.
2. **Reverse Osmosis (RO) Separation:** Water is driven under low pressure through a semi-permeable membrane, rejecting dissolved inorganic salts, heavy ions, and micro-contaminants, preventing scale accumulation within data-centre heat exchangers.
3. **Ultraviolet (UV-C) Disinfection:** The final polishing stage exposes the treated water to ultraviolet light at a wavelength of approximately 254 nm, disrupting micro-organism DNA and preventing bio-fouling in storage reservoirs.

> **Operational Note:** Water recovered through this bench-scale prototype system is intended exclusively for secondary industrial cooling recirculation. *It is NOT tested, certified, or claimed to be safe for human consumption or potable use.*

---

## Energy Harvesting Methodology

### Water Flow Energy Harvesting
In-line fluid micro-turbines are strategically placed at two points along the hydraulic loop:
* **Stage 1 (Pre-Cooling):** Captures kinetic energy generated by high pressure at the pump outlet.
* **Stage 2 (Post-Discharge):** Captures residual velocity from gravity-assisted or pressure-driven discharge lines.

The rotation of the internal turbine impellers drives small DC permanent magnet generators. The resulting variable DC voltage output passes through a voltage regulation and power-conditioning circuit (incorporating smoothing capacitors and a buck-boost converter) to provide a regulated DC rail capable of trickle-charging a storage capacitor or powering low-power telemetry sensors.

### Noise Energy Harvesting
High-decibel acoustic noise (produced by cooling fans, air handlers, and pumps) induces structural micro-vibrations in attached surfaces.
* **Transducer Array:** Ceramic piezoelectric discs (PZT) are mounted near simulated high-noise sources.
* **Acoustic-to-Electrical Conversion:** Mechanical strain on the piezoelectric substrate yields an alternating current (AC) voltage output proportional to acoustic intensity and frequency.
* **Signal Conditioning:** The low-power AC waveform is routed through a full-wave Schottky bridge rectifier and a smoothing capacitor matrix to produce a low-current DC voltage suitable for micro-energy management circuits.

---

## Monitoring and Intelligent Control

The prototype incorporates an embedded microcontroller (ESP32) running an event-driven control loop:

```
+-------------------------------------------------------------------------------+
|                        EMBEDDED CONTROL LOOP                                  |
+-------------------------------------------------------------------------------+
|                                                                               |
|   +---------------------+       +--------------------+       +------------+   |
|   | Read Sensors        | ----> | Compare Thresholds | ----> | Execute    |   |
|   | (Flow, Temp, TDS, V)|       | (Safety & Limits)  |       | Control    |   |
|   +---------------------+       +--------------------+       +------------+   |
|             ^                                                      |          |
|             |                                                      v          |
|             +---------------- Stream Telemetry <-------------------+          |
|                                                                               |
+-------------------------------------------------------------------------------+
```

* **Thermal Thresholding:** If simulated heat-sink temperatures exceed defined operating thresholds, pump control signals scale up circulation rates.
* **Quality Interlocking:** If inline TDS or turbidity readings exceed baseline recovery limits, a solenoid valve redirect (simulated via LED indication) routes fluid back for re-filtration.
* **Power Monitoring:** Dedicated current and voltage sensing chips (INA219) measure electrical power harvested by both hydraulic and acoustic circuits.

---



## Repository Structure

```
AquaLoop/
├── README.md
├── LICENSE
├── docs/
│   ├── hardware_schematic.pdf
│   └── images/
│       ├── system-architecture.png
│       ├── water-flow-diagram.png
│       ├── energy-flow-diagram.png
│       ├── circuit-diagram.png
│       ├── prototype.jpg
│       └── dashboard.png
├── firmware/
│   ├── platformio.ini
│   └── src/
│       ├── main.cpp
│       ├── sensors.cpp
│       ├── sensors.h
│       ├── display.cpp
│       └── display.h
├── hardware/
│   ├── schematics/
│   │   └── aqualoop_circuit_diagram.png
│   └── cad/
│       └── turbine_enclosure_mount.stl
├── dashboard/
│   ├── index.html
│   ├── css/
│   │   └── style.css
│   └── js/
│       ├── app.js
│       └── chart_config.js
└── data/
    └── sample_telemetry.csv
```

---

## Setup Instructions

### Hardware Assembly Setup
1. Mount the DC pump, water reservoir, carbon filter housing, and micro-turbines securely on the bench-scale testing rig frame.
2. Interconnect fluid conduits using silicone tubing, ensuring leak-free hose barb connections between the pump outlet, Stage 1 turbine, heat load block, Stage 2 turbine, carbon filter, RO housing, and UV module.
3. Wire sensors (YF-S201 flow sensor, DS18B20 temperature probe, TDS, and turbidity modules) to the designated GPIO pins on the ESP32 microcontroller board as per `docs/images/circuit-diagram.png`.
4. Connect the power-conditioning circuit outputs from the micro-turbines and the piezoelectric bridge rectifier to the voltage/current sensor module and low-power load bus.


---



---


## Results and Observations

```
+---------------------------------------------------------------------------+
|               BENCH-SCALE EXPERIMENTAL DATA PLACEHOLDER                    |
+---------------------------------------------------------------------------+
| Parameter                         | Measured Baseline Value               |
+-----------------------------------+---------------------------------------+
| Fluid Flow Rate                   | [TO BE UPDATED BY TEAM] L/min         |
| Stage 1 Turbine Output Voltage    | [TO BE UPDATED BY TEAM] V DC          |
| Stage 2 Turbine Output Voltage    | [TO BE UPDATED BY TEAM] V DC          |
| Piezoelectric Array Peak Voltage  | [TO BE UPDATED BY TEAM] mV AC / V DC  |
| Raw Input Turbidity               | [TO BE UPDATED BY TEAM] NTU           |
| Post-Filtration Turbidity         | [TO BE UPDATED BY TEAM] NTU           |
| Pre-Treatment TDS                 | [TO BE UPDATED BY TEAM] ppm           |
| Post-Treatment TDS                | [TO BE UPDATED BY TEAM] ppm           |
| Total Circuit Power Consumption   | [TO BE UPDATED BY TEAM] W             |
+---------------------------------------------------------------------------+
```

---

## Limitations

* **Bench-Scale Hardware Constraints:** The physical prototype operates using low-cost sub-12V DC micro-turbines and pumps, which exhibit higher friction losses relative to industrial scale equipment.
* **Micro-Energy Output Scale:** Energy harvested from both small hydraulic turbines and piezoelectric transducers is in the milliwatt to low-watt range—sufficient only for low-power sensor node operation, not for powering primary pumps.
* **Simplified Thermal Representation:** The heat source in this proof of concept is simulated using an inline low-wattage heat load rather than an operational high-density server cold plate.
* **Budget Constraints:** Built within a bench-scale hackathon prototype budget (under ₹5000), using hobbyist-grade sensor modules and recycled hardware components.

---

## Sustainability Impact

* **Water Waste Mitigation Concept:** Demonstrates how closed-loop recovery can drastically lower freshwater intake requirements for evaporative and liquid cooling systems in compute facilities.
* **Parasitic Load Offset Concept:** Validates the feasibility of capturing localized waste kinetic and acoustic energy to power decentralized IoT health-monitoring nodes.
* **Circular Resource Model:** Supports the transition of data centre infrastructure toward circular operational frameworks where resource streams (water and energy) are repeatedly recovered and reused.

---

## Scalability

While the current deliverable is a bench-scale proof of concept constructed within hackathon constraints, the underlying operational framework is conceptually scalable:

* **Industrial Scale Design:** In a commercial data centre installation, bench-scale micro-turbines would be replaced by industrial in-line hydro-turbines designed for minimal head-loss, integrated into high-volume chiller return lines.
* **Industrial Filtration Arrays:** Multi-stage filtration would scale to commercial high-pressure industrial RO and automated backwash sand/carbon media beds.
* **Distributed Sensor Mesh:** Microcontroller nodes would be expanded into an industrial telemetry array utilizing protocols such as Modbus, BACnet, or MQTT over industrial Ethernet.

*(Note: Scalability concepts described above represent theoretical engineering pathways and have not been validated in large-scale production environments).*

---

## Team

* Arsalur Saadi — Systems Engineer / Water Treatment Architecture
* Mohammed Ahmed Iqbal — Software Engineer / Dashboard Developer
* Khagesh Kumar Sharma — Mechanical Design & Fabrication

---

## AI Tools Used

In compliance with hackathon transparency guidelines, the following disclosure details the usage of AI tools during project development:

| AI Tool Name | Purpose / Area of Application | Description of Output Used |
| :--- | :--- | :--- |
| **ChatGPT / Claude** | Code Refactoring & Logic Review | Assisted in optimizing embedded sensor filtering routines and C++ boilerplate |
| **Mermaid.js Generator**| Architectural Diagraming | Used to format text-based system flowcharts and architecture diagrams |
| **GitHub Copilot** | Firmware & Dashboard Development | Provided code completion suggestions for JavaScript chart rendering |

---

## API Documentation

State: **Not Applicable**

*(The current prototype relies on direct embedded sensor reading acquisition and local network dashboard rendering; no external third-party web APIs or cloud endpoints are exposed in this build).*

---

## License

This project is open-source and released under the [MIT License](LICENSE).

```
MIT License

Copyright (c) 2026 AquaLoop Team

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom it is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## References and Acknowledgements

1. **U.S. Department of Energy (DOE):** Guidance on Data Center Energy and Water Efficiency.
2. **ASHRAE Technical Committee 9.9:** *Thermal Guidelines for Data Processing Environments*.
3. **Arduino & ESP32 Open-Source Ecosystems:** Open-source hardware sensor libraries and reference documentation.
4. **Hackathon Mentors & Organizers:** For providing guidance and evaluation during the event.

---

## Hackathon Compliance Notes

* **Proof of Concept Context:** This project was conceptualized, built, and tested as a functional prototype during a hackathon event under a strict budget constraint (< ₹5000).
* **Data Integrity:** All performance metrics, energy output numbers, and water quality values are explicitly marked as `[TO BE UPDATED BY TEAM]` pending empirical logging on calibrated hardware test benches.
* **Safety & Regulatory Compliance:** Recovered cooling water is processed purely for recirculated industrial heat-exchange demonstration; no claims regarding drinkability, safety for consumption, or municipal certification are made.
