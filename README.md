# Exoskeleton Arm — B.Tech Major Project

**Design and Fabrication of Exoskeleton Arm for Biomedical Use**  
Authors: Daksh Sharma, Navneet Kumar, Mayank Awasthi  
Supervisor: Prof. Arshad Hussain Khan, ZHCET (AMU)  
Year: 2023–24

## Abstract
This project presents the design, fabrication and control of a wearable exoskeleton arm intended for biomedical and augmentation use. The device augments lifting capability (~12.5 kg estimated), uses a linear actuator (700 N) driven by an Arduino-controlled relay interface, and relies on EMG sensors for muscle-activity-based control. Mechanical components are fabricated from EN24 (AISI 4340) flats; structural validation is performed using SolidWorks stress simulation. The system is intended to be lightweight, cost-effective, and suitable for rehabilitation/industrial augmentation.

## Key features
- Electric linear actuator (700 N) for assisted arm motion  
- EMG-based control using Muscle BioAmp and Arduino Uno  
- Relay-driven actuator direction control (optically isolated relay module)  
- SolidWorks mechanical design and stress validation (hook, bolts, welds)  
- Compact electronics pack (12 V battery + 9 V for Arduino) in a wearable backpack

## System specifications (summary)
- Actuator: 12 VDC linear actuator, 700 N, 15 mm/s  
- Battery: 12 V, 7.5 Ah lead-acid (prototype)  
- Controller: Arduino Uno (analog EMG read on A0; relay pins 2 & 3)  
- Sensor: Muscle BioAmp Candy (EMG)  
- Relay: Opto-isolated 2-channel relay (5 V input, 10 A)  
- Material: EN24 (AISI 4340) steel flats (20 mm × 2.5 mm)  
- Estimated lifting capacity (safe): ~12.5 kg (after design safety factor)

## Files & folders
- `firmware/exo_control.ino` — Arduino firmware (EMG read → envelope → counters → relay control)  
- `hardware/mechanical_drawings/` — SolidWorks exported drawings (STEP/PNG/DXF)  
- `hardware/stress_simulation/` — FEA screenshots (hook, bolts) and mesh settings  
- `hardware/BOM.csv` — Bill of Materials and costs  
- `electrical/wiring_diagram.png` — wiring schematic for EMG→Arduino→relay→actuator  
- `docs/Project_Report.pdf` — Full project report (thesis)

## Firmware (control) summary
- Read EMG analog input (`A0`), apply filtering and envelope detection.  
- Maintain `up_counter` / `down_counter` based on envelope vs threshold.  
- If `up_counter` ≥ N → activate relay to move actuator 'up'; if `down_counter` ≥ N → move 'down'.  
- Relay outputs toggle polarity to change actuator direction.  
- Serial output for debugging and watchdog reset to prevent system hangs.

## Bill of Materials (high-level)
See `hardware/BOM.csv` for full table. Key items:
- Linear actuator (700 N)
- EN24 steel strips (20 mm × 2.5 mm)
- Arduino Uno
- Muscle BioAmp EMG sensor
- Opto-isolated 2-channel relay
- 12 V battery, wiring, switches

## How to run (quick)
1. Load `firmware/exo_control.ino` onto an Arduino Uno via Arduino IDE.  
2. Connect EMG sensor `OUT` → `A0`, `VCC`→5V, `GND`→GND.  
3. Connect relay `IN1`/`IN2` to Arduino digital pins (as in code), and relay outputs to linear actuator and battery as per `electrical/wiring_diagram.png`.  
4. Power Arduino (9 V) and actuator battery (12 V). Monitor serial at 115200 baud for envelope/debug values.  
**Warning:** Prototype is experimental; test with low loads and ensure safety connections and limit switches are in place.

## Validation & results
- Structural checks (bending, weld, bolt shear) performed using hand calculations and SolidWorks stress simulation.  
- Actuator sizing and lever calculations show an operational lifting capability near 12.5 kg (with chosen safety factor).  
- Prototype demonstrates EMG-triggered motion (up/down) with relay-controlled actuator; full clinical validation beyond scope.

## License
- MIT License

## Citation
If you use this work, please cite:  
Awasthi, M., Sharma, D., Kumar, N., *Design and Fabrication of Exoskeleton Arm for Biomedical Use*, B.Tech Project Report, ZHCET AMU, 2023–24.

