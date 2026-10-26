# PLC-Scrap-Metal-Sorting
PLC-based automated scrap metal sorting system using sensors, Delta PLC, conveyor belt, and pneumatic pusher to separate ferrous and non-ferrous metals.

Overview
Prototype concept for sorting scrap into ferrous (iron/steel) and non-ferrous (aluminium/copper) groups using a conveyor, validated sensors, a Delta DVP-14SS2 PLC, and a pneumatic pusher. Optional monitoring uses one ESP32, RS485/MAX485, and a 20x4 I2C LCD.

Architecture
Hopper -> vibratory feeder -> conveyor -> sensors -> PLC -> conveyor relay/contactor and 5/2 solenoid valve -> two collection bins.
Optional: PLC <-> RS485/MAX485 <-> ESP32 -> 20x4 I2C LCD; Wi-Fi/cloud is optional.

Engineering and safety notes
• Test the selected sensors with real iron. steel aluminium, and copper samples at the intended gap and conveyor speed. An inductive sensor may detect multiple metal types; do not assume it uniquely identifies ferrous metals
• A precision eddy-current displacement sensor is not automatically a complete scrap-classification sensor Validate the exact sensor/probe and calibration experimentally.
• Use suitable relays/contactors/ drivers for motors and solenoids; never exceed PLC output ratings. Emergency stop must use a suitable hard wired safety circuit, not only a PLC program.
• Mains and pneumatic work must be supervised by a qualified person.

Test plan
1. Check start/ stop and hardwired E-stop safely.
2. Test each sensor separatelv on representative samples.
3. Run one piece at a time at low conveyor speed.
4. Record true detections, missed detections, false detections, sensor gap, and material
5. Calibrate pusher timing and confirm bin destination 6. Test iam handling and safe restart.
7. Add only measured results to project reports


