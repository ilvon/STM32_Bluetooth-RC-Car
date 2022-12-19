# STM32_Bluetooth-RC-Car
## Component
1. STM32F103VETx MCU Development Board
2. L298N Motor Driver(or L293D)
3. HC05 Bluetooth Module
4. Battery(s)
5. Android Phone

## Feature
- onboard LED indicator
  - Forward: Red
  - Backward: White
  - Left/Right: Green
- 5 levels speed control
- onboard LCD screen for showing informations (e.g. QR code in `qrcode_data.h`, list in `main.c`)
- control via Android app by Bluetooth (`Project.apk`)

## Remarks
### L298N Connections
| L298N Pin |    Connections     |
|:---------:|:------------------:|
|   OUT 1   |      Left +ve      |
|   OUT 2   |      Left -ve      |
|   OUT 3   |     Right +ve      |
|   OUT 4   |     Right -ve      |
|    Vcc    |        +9V         |
|    GND    | +9V GND, STM32 GND |
|    ENA    |   `PA6` / `PB6`    |
|    ENB    |   `PA6` / `PB6`    |
|    IN1    |       `B13`        |
|    IN2    |       `B12`        |
|    IN3    |        `C9`        |
|    IN4    |        `C8`        |
### Motor Directions
| Direction | IN1 / IN3 | IN 2 / IN 4 |
|:---------:|:---------:|:-----------:|
|  FORWARD  |     1     |      0      |
| BACKWARD  |     0     |      1      |
### Generation of `qrdata[50][50]` in `qrcode_data.h`
```c
const unsigned char qrdata[50][50] = {...};
```
1. Using online tool [decode.fr](https://www.dcode.fr/binary-image)
	1. resize image resolution to $50\times50$
	2. generate data 
2. Using **Matlab**
	1. using `imread()` & `imbinarize()`
	2. copy data in the image data matrix
