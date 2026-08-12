# Alcohol Detection and Vehicle Locking System

**Internet of Things Project**

## Abstract

Alcohol-related accidents and injuries have become a growing concern in
recent years, leading to a significant number of premature deaths
worldwide. This project presents an approach to enhance alcohol detection
in an automobile ignition locking system using Arduino. The system
incorporates the MQ-3 sensor to detect the alcohol concentration in the
surrounding breath sample. A microcontroller is utilised to convert the
sensor output into a reading that determines the driver's alcohol level.
This analysis is an integral part of an automobile ignition-locking
system that prevents the car from starting when the driver is
intoxicated. By implementing this alcohol detection system, the aim is to
reduce the occurrence of alcohol-related accidents and promote safer
driving practices.

**Key Words:** Arduino UNO, MQ-3 Sensor, LED, DC Motor, Relay.

## Introduction

Drunk driving has emerged as a significant cause of road accidents.
Drivers under the influence of alcohol often find themselves in an
unstable condition, leading to reckless driving and posing a risk to
themselves and other road users. Laws prohibiting drinking and driving
exist, but enforcing them is difficult since authorities cannot be
present everywhere at once. This creates a need for an alcohol detection
system that transcends the constraints of space and time.

India has set a legal blood alcohol concentration (BAC) limit of
30mg/100mL. Any level above this threshold is unlawful, and elevated BAC
levels progressively impair a driver's mental, physical, and sensory
functions. By addressing alcohol detection in vehicles directly, this
project aims to contribute to road safety and reduce the consequences of
drunk driving.

## Methodology

The Alcohol Detection with Engine Locking system uses an MQ-3 sensor,
which detects the presence of alcohol in the surrounding environment and
provides an output signal based on the concentration present. When the
alcohol concentration exceeds a threshold, the conductivity of the MQ-3
sensor increases, and this reading is relayed to the Arduino
microcontroller.

Upon receiving the sensor reading, the Arduino compares it against a
predetermined threshold. If the reading surpasses the threshold, the
microcontroller activates the relay, which cuts power to the DC motor —
preventing the vehicle from moving — and switches the red LED on as a
visual alert. If the reading is within the safe range, the green LED
stays on and the motor remains powered.

## Components

| Component | Role |
|---|---|
| **Arduino Uno** | Reads the sensor, applies threshold logic, and drives the relay/LEDs |
| **MQ-3 Alcohol Sensor** | Detects alcohol vapor and outputs an analog signal proportional to concentration |
| **Relay** | Switches power to the DC motor based on the Arduino's decision, isolating the low-voltage Arduino circuit from the motor circuit |
| **DC Motor** | Represents the vehicle's engine — stops when alcohol is detected, simulating engine lock |
| **Breadboard** | Used for prototyping and circuit connections |
| **Green / Red LED** | Visual indicators — green for safe, red for alcohol detected |

## Working

The MQ-3 sensor continuously outputs an analog value read on Arduino pin
`A0`. The Arduino compares this value against a threshold of **350**:

- **Below 350** → green LED on, red LED off, motor (via relay) powered on
  — engine enabled.
- **350 or above** → red LED on, green LED off, motor (via relay) powered
  off — engine locked.

Sensor readings are printed continuously over Serial at 115200 baud for
monitoring.

## Results

- **MQ-3 Alcohol Sensor:** produces an analog reading that varies with
  alcohol concentration, allowing the system to gauge intoxication level.
- **Arduino Uno:** processes the sensor reading and decides whether to
  enable or lock the engine based on the threshold; also handles serial
  communication for monitoring.
- **Relay + DC Motor:** when the threshold is exceeded, the relay cuts
  power to the motor, physically representing the engine being locked.
- **LED:** the red LED lighting up gives a clear visual indication that
  the alcohol level has exceeded the safe threshold; the green LED
  confirms normal operation.

Each component works together to detect alcohol levels, simulate engine
locking, and provide a clear visual warning.

## Conclusion

The alcohol detection system, built from the MQ-3 sensor, Arduino Uno,
relay, DC motor, and LEDs, effectively detects alcohol levels and
prevents a drunk driver from starting the vehicle. The MQ-3 sensor
provides reliable detection of alcohol vapor, the Arduino processes this
data and makes threshold-based decisions, and the relay-controlled DC
motor demonstrates engine locking in response. The LED gives a clear,
immediate visual signal of the vehicle's status.

By combining these components, the system aims to discourage drunk
driving and reduce the number of alcohol-related accidents on the roads —
serving as a proactive, low-cost measure to enhance road safety.

## Repository structure

```
alcohol-detection-vehicle-locking/
├── README.md
├── .gitignore
├── arduino/
│   └── alcohol_detection_vehicle_locking.ino
└── docs/
    └── project_report.docx
```

## Setup

1. Open `arduino/alcohol_detection_vehicle_locking.ino` in the Arduino
   IDE.
2. Wire the MQ-3 sensor output to `A0`, the relay (motor control) to pin
   `7`, the green LED to pin `8`, and the red LED to pin `9`.
3. Upload to an Arduino Uno.
4. Open the Serial Monitor at **115200 baud** to view live sensor
   readings.

## References

1. IJETA — Volume 2, Issue 2
2. IJARIIE — Automatic Alcohol Detection in Vehicle
3. Lee, *Assessing the Feasibility of Vehicle-Based Sensors To Detect
   Alcohol Impairment*, 2010, National Highway Traffic Safety
   Administration
4. SSRN — Paper ID 4232102
5. IEEE Xplore — Document 8405475
6. JETIR — 2204460
7. AIP Conference Proceedings — Automatic engine locking system for
   drunken driving prevention
8. PNR Journal — Article 6911
9. IJEAST — pp. 142–144
10. IRJMETS — Volume 2, Issue 7, July 2020

Full reference links are available in
[`docs/project_report.docx`](docs/project_report.docx).
