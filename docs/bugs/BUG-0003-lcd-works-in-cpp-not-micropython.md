# BUG-0003: I2C LCD Displays Output in C++ but Remains Blank in MicroPython

## Summary

The I2C LCD module functions correctly when executed using the C++ runtime but fails to display any output when executed using the MicroPython runtime under identical hardware configuration.

This indicates a possible compatibility issue between the simulator's MicroPython runtime and the LCD driver implementation.

---

## Severity

High

---

## Priority

P1

---

## Status

Open

---

## Environment

### Platform

Tarcin Simulation Platform

### Board

Raspberry Pi Pico

### Runtime

MicroPython

### Component

I2C LCD (16x2)

### I2C Address

0x27

---

## Expected Behavior

The LCD should initialize successfully and display:

```text
Hello World
```

The behavior should match the C++ runtime implementation.

---

## Actual Behavior

The program executes successfully without errors.

However:

* LCD remains blank.
* No characters are displayed.
* No initialization error is reported.
* Serial output indicates code execution continues normally.

---

## Wiring Configuration

```text
LCD SDA → GPIO0
LCD SCL → GPIO1
LCD VCC → 5V
LCD GND → GND
```

---

## Reproduction Steps

1. Create a Raspberry Pi Pico project.
2. Connect an I2C LCD module.
3. Configure LCD address as 0x27.
4. Upload the MicroPython code below.
5. Execute simulation.
6. Observe LCD display.

---

## Test Code

```python
from machine import Pin, I2C
from pico_i2c_lcd import I2cLcd

i2c = I2C(0, sda=Pin(0), scl=Pin(1))

lcd = I2cLcd(i2c, 0x27, 2, 16)

lcd.putstr("Hello World")
```

---

## Observed Results

| Test               | Result  |
| ------------------ | ------- |
| Program executes   | PASS    |
| I2C initialization | PASS    |
| LCD initialization | UNKNOWN |
| Text display       | FAIL    |
| Runtime stability  | PASS    |

---

## Comparison Test

### C++ Runtime

Result:

```text
LCD displays expected output.
```

Status:

PASS

### MicroPython Runtime

Result:

```text
LCD remains blank.
```

Status:

FAIL

---

## Business Impact

* LCD-based educational projects cannot be executed correctly.
* Student learning experience is affected.
* Inconsistent behavior between supported runtimes.
* Increased support and debugging effort.

---

## Suspected Root Cause

Potential causes include:

1. MicroPython LCD driver not supported.
2. Incomplete I2C emulation.
3. Incorrect LCD initialization sequence.
4. Unsupported LCD command implementation.
5. Runtime-to-component communication issue.

Root cause currently under investigation.

---

## Required Investigation

* Verify I2C transaction logs.
* Compare C++ and MicroPython LCD initialization sequences.
* Validate LCD command handling.
* Confirm simulator support for pico_i2c_lcd library.

---

## Acceptance Criteria

The issue will be considered resolved when:

* LCD displays text correctly in MicroPython.
* Behavior matches C++ implementation.
* No runtime errors occur.
* Regression tests pass for all LCD examples.

---

## Labels

```text
bug
high
pico
micropython
lcd
i2c
display
simulator-engine
```

---

## Attachments

* Circuit screenshot
* Runtime screenshot
* Reproduction code
* Validation report

---

## Reported By

Engineering Validation Team

## Assigned To

Unassigned

## Date Reported

YYYY-MM-DD
