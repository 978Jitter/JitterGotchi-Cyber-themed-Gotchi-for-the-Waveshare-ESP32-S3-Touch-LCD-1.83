# JitterGotchi — Cyber-Themed LVGL Virtual Pet & HUD for Waveshare ESP32-S3-Touch-LCD-1.83

A matte-black, brushed-steel, and crimson (`#E11D2E`) cyber-pet and pocket telemetry interface built with **LVGL 8.4** and **Arduino** for the **Waveshare ESP32-S3-Touch-LCD-1.83** (`240×284` IPS, **ST7789P** display driver, **CST816D** capacitive touch, **PCF85063** RTC, and **AXP2101** power management). Styled with square geometry, red corner brackets, JetBrains Mono typography, and **JitterTech** icon plates.

## Features
- **Boot Splash:** Jitter emblem, wordmark, spinning ring, and progress bar.
- **Interactive Cyber-Pet HUD:** Real-time `CST816D` touch tracking—JitterGotchi actively chases your finger across the screen alongside animated moods, live status bars, a red sweep-second ring clock, `PCF85063` RTC time/date, and a terminal prompt with a blinking cursor.
- **Action & App Grid:** Touch-responsive menu of **JitterTech** icon plates for interacting with your pet, running maintenance/status actions, and opening hardware views.
- **Wi-Fi Scanner:** Nearby 2.4 GHz network scan with live signal strength indicators.
- **System & Battery Monitor:** Chip info, CPU load, heap, OPI PSRAM, uptime, and `AXP2101` battery telemetry.

## Hardware Target
- **Board:** Waveshare `ESP32-S3-Touch-LCD-1.83` (`ESP32-S3R8`, 16MB Flash, OPI PSRAM)
- **Display & Touch:** 1.83" `240×284` IPS (`ST7789P`) + capacitive touch (`CST816D`)
- **Timing & Power:** `PCF85063` RTC, `AXP2101` PMU

## Requirements & Setup
1. Install **Arduino IDE** with the **ESP32** board package.
2. Pull in Waveshare's bundled libraries from [`waveshareteam/ESP32-S3-Touch-LCD-1.83`](https://github.com/waveshareteam/ESP32-S3-Touch-LCD-1.83) (`examples/arduino/libraries`): **LVGL 8.4**, **GFX Library for Arduino**, **Arduino_DriveBus**, **SensorLib**, and **Mylibrary**.
3. Point Arduino IDE at Waveshare's bundled libraries folder and replace its `lv_conf.h` with this project's `JitterGotchi/lv_conf.h` (FPS overlay off, UNSCII fonts on, LVGL memory pool set to 64K).
4. Configure **Tools**:
   - **Board:** `ESP32S3 Dev Module`
   - **USB CDC On Boot:** `Enabled`
   - **PSRAM:** `OPI PSRAM`
   - **Flash Size:** `16MB (128Mb)`
5. Open `JitterGotchi/JitterGotchi.ino` and upload to the board.

## Usage & Customization
- **Navigation:** Boot into the splash and home HUD; drag your finger across the screen to have JitterGotchi follow your touch, tap or swipe up for action/menu plates, and use the red `<` header control to return. The `PCF85063` RTC initializes from build time when first found unset.
- **Colors & Layout:** Adjust palette defines and screen parameters in `JitterGotchi/jitter_gotchi_ui.cpp` (or `jitter_palette.h`).
- **Assets & Fonts:** Regenerate icons/emblems with `python3 tools/gen_assets.py` and fonts with `python3 tools/gen_fonts.py`.

> **Note:** IMU tilt reactions, SD Card, and Audio screens are planned for future releases.
