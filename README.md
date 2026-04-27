# Python-script-for-load-transient-test

Automated Load Transient Testing of Power Distribution Network

📌 Overview

This repository contains a Python‑based automated test framework developed to perform load transient testing of a Power Distribution Network (PDN) used in satellite payload electronics.
The objective of this project is to demonstrate how automated hardware testing can be implemented using SCPI commands and PyVISA to control laboratory instruments, execute test sequences, capture measurements, evaluate acceptance criteria, and generate structured test outputs suitable for qualification and production environments.
This project was developed as part of a Junior Hardware Test Engineer assessment and follows standard hardware validation and automation practices used in aerospace and embedded systems industries.

🎯 Test Objective

The Load Transient Test evaluates the ability of the PDN to maintain output voltage regulation when subjected to sudden changes in load current.
Specifically, the script verifies:  

1. Voltage undershoot during a load step‑up  
2. Voltage overshoot during a load step‑down  
3. Compliance with predefined acceptance limits  
4. Repeatability and traceability of results

⚡ Power Distribution Network Under Test  
1. Input Voltage: +5 V (regulated)  
2. Output Rails:  
+3.6 V  
+3.3 V  
+2.5 V  
+1.8 V  
3. Regulators Used:  
  A. DC‑DC Buck Converters  
  B. LDO  
4. Power Sequencing: PGood‑based daisy chain

🧪 Test Methodology

The automated test sequence follows these steps:

1. Initialize and configure laboratory instruments  
2. Apply nominal input voltage using a programmable power supply  
3. Program an electronic load to apply a fast current step:
  Low load → High load → Low load  
  4. Capture output voltage response using an oscilloscope  
  5. Measure:  
  A. Voltage undershoot  
  B. Voltage overshoot  
  6. Compare measurements against acceptance criteria  
  7. Log results with timestamp and Pass/Fail status  
  8. Save data to CSV for further analysis  
  9. Generate a basic test summary

🛠️ Test Instrumentation

The script communicates with instruments using SCPI commands via PyVISA.
**Required Equipment**  
1. Programmable Power Supply  
2. Electronic Load (Constant Current mode)  
3. Digital Oscilloscope  
4. PC with Python and PyVISA installed  
Communication Interfaces
USB / LAN / GPIB (instrument dependent)

✅ Acceptance Criteria

## ✅ Acceptance Criteria

| Parameter           | Limit        |
|--------------------|--------------|
| Voltage Undershoot | ≤ 200 mV     |
| Voltage Overshoot  | ≤ 200 mV     |
| Test Result        | Pass / Fail  |

Parameter LimitMaximum Undershoot≤ 200 mVMaximum Overshoot≤ 200 mVTest ResultPASS if both limits are satisfied

📁 Repository Structure  
Automated-Load-Transient-Testing/  
│  
├── load_transient_test.py     # Main automation script  
├── results/  
│   └── load_transient_results.csv  
├── README.md                  # Project documentation  
└── requirements.txt           # Python dependencies


📊 Output Data  

The script generates a CSV log file containing:  

1.Timestamp of test execution  
2.Measured voltage undershoot  
3.Measured voltage overshoot  
4.Pass / Fail status

This format ensures:  

1.Traceability  
2.Production readiness  
3.Ease of debugging and reporting

📈 Statistics & Reporting

The framework is designed to be extensible, allowing future additions such as:  

1.Multiple test iterations  
2.Min / Max / Average calculations  
3.HTML or PDF test reports  
4.Board‑to‑board comparison during production testing

🧠 Design Philosophy

This project emphasizes:  

1.Clear and readable automation code  
2.Deterministic and repeatable test execution  
3.Separation of test parameters and test logic  
4.Hardware‑focused validation rather than software complexity

The implementation intentionally avoids advanced Python constructs to remain accessible to engineers with a C/embedded background.

🚀 How to Run  

1.Install dependencies:  
A.pip install pyvisa pyvisa-py  
 2.Connect instruments and update VISA addresses in the script  
 3.Power on the PDN hardware  
 4.Run:  
 A.python load_transient_test.py

📌 Notes & Assumptions  

1.Instrument SCPI command sets may vary by manufacturer  
2.Voltage measurements are taken on the selected oscilloscope channel  
3.Proper probing techniques are assumed (short ground leads, bandwidth limit enabled)

🔮 Future Improvements  

1.Multi‑rail automated testing  
2.Temperature‑based testing  
3.PGood timing verification  
4.Database‑based result storage  
5.CI‑style regression testing for hardware
