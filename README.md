# PLC-Scrap-Metal-Sorting
PLC-based automated scrap metal sorting system using sensors, Delta PLC, conveyor belt, and pneumatic pusher to separate ferrous and non-ferrous metals.

Overview
Prototype concept for sorting scrap into ferrous (iron/steel) and non-ferrous (aluminium/copper) groups using a conveyor, validated sensors, a Delta DVP-14SS2 PLC, and a pneumatic pusher. Optional monitoring uses one ESP32, RS485/MAX485, and a 20x4 I2C LCD.


ENGINEERING AND SAFETY NOTES 
• Test the selected sensors with real iron. steel aluminium, and copper samples at the intended gap and conveyor speed. An inductive sensor may detect multiple metal types; do not assume it uniquely identifies ferrous metals
• A precision eddy-current displacement sensor is not automatically a complete scrap-classification sensor Validate the exact sensor/probe and calibration experimentally.
• Use suitable relays/contactors/ drivers for motors and solenoids; never exceed PLC output ratings. Emergency stop must use a suitable hard wired safety circuit, not only a PLC program.
• Mains and pneumatic work must be supervised by a qualified person.

TEST PLAN
1. Check start/ stop and hardwired E-stop safely.
2. Test each sensor separatelv on representative samples.
3. Run one piece at a time at low conveyor speed.
4. Record true detections, missed detections, false detections, sensor gap, and material
5. Calibrate pusher timing and confirm bin destination 6. Test iam handling and safe restart.
7. Add only measured results to project reports

SYSTEM ARCHITECTURE 
Hopper -> Vibratorv feeder -> Conveyor -> Validated sensors -> Delta PLC
  |            |

Classification +-> Motor relay. contactor
+-> Relay/driver -> 5/2 valve
             |
      Pneumatic pusher
        /       \
Ferrous bin    Non-ferrous bin

Optional monitoring: PLC <-> RS485/MAX485 <-> ESP32 -> 20x4 I2C LCD

CONCEPTUAL SEQUENCE 
1. Operator starts the svstem
2. Convevor carries a separated piece past the sensing point.
3. Sensors send signals to the PLC.
4. PLC applies experimentally validated classification logic.

 ESP32 MONITORING 
Use one ESP32 to receive PLC status/count data over RS485 via a compatible MAX485 interface and show it on a 20x4 12C LCD.

Before coding:
Define the serial protocol and baud rate.
• Verify RS485 A/B wiring and electrical reference/isolation.
• Never connect 24 V PLC signals directly to ESP32 • Confirm LCD I2C address and library.
Add firmware and test results only after bench testing.
ESP32 monitoring must not replace the hardwired emergency-stop circuit.

PLC PROGRAM
Target: Delta DVP-14SS2; confirm exact model/output variant.
This repository does not include unverified ladder logic as ready-to-run code. Create and test the final program in the suitable Delta programming software using the actual wiring
Checklist:
1. Confirm PLC model/output type and termina diagram.
2. Confirm sensor NPN/PNP. NO/NC behavior. and voltage.
3. Implement start/stop, interlocks, validated sensor logic, pusher timing, iam handling, and fault recovery.
4. Test with outputs disconnected or safely simulated first.
5. Add the tested program export and ladder diagram here.

REPOSITORY STATUS 
Starter documentation only. Add the tested PLC ladder program, wiring diagram, ESP32 firmware, and actual test results when available. This repository does not claim the prototype has already been built or tested.
