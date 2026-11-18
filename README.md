# OpenRobot ST-Link Tool

> English | **[한국어](README_ko.md)**

Production tool for OpenRobot motor controllers (STM32F405): one button flashes the bootloader and
firmware over SWD, runs the inspection and calibration steps over CAN, and writes a PDF test report
for each unit.

## Download

Download the latest version from **[Releases](https://github.com/dongilc/openrobot-stlink-tool/releases/latest)**:

- **Windows**: `OpenRobot_STLink_Tool_v1.5.zip`

Unzip and run `OpenRobot_STLink_Tool_v1.5.exe`. No installation required: OpenOCD is built in, and the
production firmware for each product is in the `production_fw` folder next to the program.

## Features

- **Production tab**: flash (bootloader + app + EEPROM erase), connect, health check, motor config,
  winding R/L, motor NTC, encoder offset, FOC no-load quality, output encoder calibration and check,
  rated / no-load speed, torque ripple, inertia tune with position-loop frequency response, output backlash.
  Steps a product does not have are skipped.
- **Firmware check before flashing**: the board name compiled into the ELF and the sha256 in
  `manifest.txt` must match the selected product.
- **Test report**: PDF per unit plus a CSV log line, in the `[성적서]` folder next to the program.
- **Debug tabs**: live variable watch, health check, threads and peripherals over SWD without
  resetting the target.

## Products in v1.5

| Product folder | Models |
|---|---|
| `SPN-MC_V2` | GIM8108, RMD-X6-6, SDD09-PS6 / PS8 / PS9 |
| `SPN-MC_D17_D20` | FL7016, GIM8108 |
| `VESCAT_HIGH_V2R3` / `VESCAT_HIGH_V2R4` | RV10C_27, RV6E_43 |
| `SPN-MC_D14` | firmware and bootloader only |

## System Requirements

- **OS**: Windows 10/11 (64-bit)
- **ST-Link V2 or V3** (SWD). If Windows does not recognise it, install the ST-Link USB driver (STSW-LINK009).
- **USB-to-CAN adapter**: PCAN-USB (PEAK driver) or CANable 2.0 (slcan). Default `PCAN_USBBUS1`, 1 Mbps.

## Quick Start

1. Download and unzip `OpenRobot_STLink_Tool_v1.5.zip`.
2. Connect ST-Link (SWD) and the CAN adapter to the board, power the board.
3. Run the exe, open the production tab, pick the product and model, press start.

> The motor turns from step 5 on. Keep the shaft area clear and check the mounting and the supply
> before starting. Only step 15 (backlash) needs the output shaft clamped.

## License

Proprietary — see [LICENSE](LICENSE). The firmware images in `production_fw` are GPLv3 (VESC based);
the corresponding source is available on request.
