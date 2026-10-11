# Rev.A14 UNO R4 custom hardware – manufacturing files

This folder contains the **Gerber manufacturing package only** for the Rev.A14 custom PCB used with the Arduino UNO R4 WiFi version of the NZHS Annealer firmware.

The editable KiCad PCB source is intentionally not included here.

## Manufacturing package

- `MGNZ_UNO_R4_RevA14_Gerber.zip`
- Generated with KiCad 10.0.6
- 2-layer FR-4
- Board size: 170 x 120 mm
- Thickness: 1.6 mm
- Outer copper: 1 oz / 35 µm
- Four 3.2 mm NPTH mounting holes
- Includes front/back copper, solder mask and silkscreen, Edge.Cuts, PTH and NPTH drill files, and Gerber job file

This is the same native KiCad Gerber package used for the Rev.A14 production order.

## Rev.A14 firmware pin map

| Function | UNO R4 pin |
|---|---|
| START button | D2 |
| MODE button | D3 |
| START LED | D4 |
| Feeder ENA | D5, active-low |
| Annealer / ZVS SSR | D6 |
| Cooling | D7 |
| DS18B20 | D8 |
| Drop servo | D9 |
| Drop solenoid | D10 |
| MODE LED | D11 |
| Feeder STEP | D12 |
| Feeder DIR | D13 |
| ACS712 current sensor | A0 |
| TIME / UP button | A2 |
| OLED SDA | A4 |
| OLED SCL | A5 |

## Firmware differences for Rev.A14

The fork firmware keeps `#define SERVO` enabled by default.

- With `SERVO` defined, D9 controls the servo and D10 is not actuated by gate open/close commands.
- With `SERVO` undefined, D10 controls the solenoid and the R4 servo backend is not required.
- Feeder enable on D5 is active-low and is driven HIGH immediately during startup so the feeder starts disabled.

Hardware and firmware should still be bench-tested with the high-current annealing supply disconnected before first live operation.
