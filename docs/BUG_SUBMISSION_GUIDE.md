# Bug Submission Guide

## Purpose

This document defines the standard process for reporting, documenting, and tracking defects identified within the Tarcin Simulation Platform.

Following a consistent bug reporting process helps engineers:

* Reproduce issues quickly
* Identify root causes efficiently
* Prioritize fixes appropriately
* Reduce duplicate reports
* Improve validation and testing quality

---

# Before Creating a Bug

Before submitting a new bug report, verify the following:

## Checklist

* [ ] Issue is reproducible
* [ ] Latest simulator version is being used
* [ ] Connections are verified
* [ ] Code has been reviewed
* [ ] Existing issues have been searched
* [ ] Screenshots have been collected
* [ ] Logs or error messages have been captured

If the issue already exists, add information to the existing report instead of creating a duplicate.

---

# Bug Creation Process

## Step 1: Create a New Issue

Navigate to:

```text
Issues → New Issue
```

Select:

```text
Bug Report
```

---

## Step 2: Assign Issue ID

Use the format:

```text
BUG-0001
BUG-0002
BUG-0003
```

Issue IDs must be unique.

---

## Step 3: Write a Clear Title

### Good Examples

```text
BUG-0042: LCD Display Remains Blank in MicroPython

BUG-0043: Push Button Counter Does Not Increment

BUG-0044: RGB LED Brightness Reduces After Second Cycle
```

### Bad Examples

```text
LCD Problem

Not Working

Error Found
```

---

# Required Information

Every bug report must contain the following sections.

---

## Environment Information

### Simulator Version

```text
v1.5.2
```

### Board

```text
Raspberry Pi Pico
ESP32
Arduino UNO
```

### Runtime

```text
MicroPython
C++
```

### Component

```text
LCD
Push Button
Buzzer
Servo
RGB LED
```

---

## Expected Behavior

Describe what should happen.

### Example

```text
The LCD should display "Hello World" immediately after execution.
```

---

## Actual Behavior

Describe what actually happens.

### Example

```text
Program executes successfully but LCD remains blank.
```

---

## Steps to Reproduce

Provide exact reproduction steps.

### Example

```text
1. Create a new Pico project.
2. Connect LCD to I2C.
3. Upload provided code.
4. Execute simulation.
5. Observe LCD output.
```

---

## Code Sample

Attach the smallest possible code required to reproduce the issue.

### Example

```python
from machine import Pin, I2C

i2c = I2C(0, scl=Pin(1), sda=Pin(0))

print(i2c.scan())
```

---

## Wiring Details

Document all connections.

### Example

```text
LCD SDA → GPIO0
LCD SCL → GPIO1
LCD VCC → 5V
LCD GND → GND
```

---

## Screenshots

Attach screenshots showing:

* Circuit setup
* Runtime output
* Error messages
* Unexpected behavior

Required whenever possible.

---

## Video Evidence (Optional)

Attach a short screen recording if the issue involves:

* Timing problems
* Animation issues
* UI behavior
* Sensor updates

---

# Severity Classification

## Critical

Platform functionality is unusable.

Examples:

* Simulator crashes
* Runtime crashes
* Project cannot execute

---

## High

Major functional failure.

Examples:

* GPIO not working
* LCD not displaying
* Sensor values incorrect

---

## Medium

Partial feature failure.

Examples:

* Delayed response
* Incorrect timing behavior

---

## Low

Minor issue.

Examples:

* UI alignment
* Documentation issue
* Label mismatch

---

# Labels

Apply appropriate labels.

## Board

```text
pico
esp32
arduino
```

## Component

```text
lcd
button
buzzer
servo
rgb-led
sensor
```

## Runtime

```text
micropython
cpp
```

## Severity

```text
critical
high
medium
low
```

---

# Root Cause Analysis Process

Once investigation begins, update the issue with:

## Root Cause

Example:

```text
LCD initialization sequence differs between C++ and MicroPython runtime implementation.
```

## Impact

Example:

```text
All I2C LCD projects using MicroPython are affected.
```

## Resolution

Example:

```text
Updated LCD driver initialization sequence.
```

---

# Verification Process

Before closing an issue:

## Validation Checklist

* [ ] Issue reproduced
* [ ] Root cause identified
* [ ] Fix implemented
* [ ] Fix tested
* [ ] Regression tests passed
* [ ] Screenshots updated
* [ ] Verification completed

---

# Issue Status Workflow

```text
Open
  ↓
Investigating
  ↓
Root Cause Identified
  ↓
Fix In Progress
  ↓
Ready For Testing
  ↓
Verified
  ↓
Closed
```

---

# Definition of Done

A bug can only be marked as Closed when:

* Root cause is documented
* Fix is implemented
* Validation is completed
* Regression testing passes
* Evidence is attached
* Reviewer approval is received

---

# Example Bug Report

## BUG-0051

### Title

LCD Works in C++ but Not in MicroPython

### Board

Raspberry Pi Pico

### Runtime

MicroPython

### Component

LCD I2C

### Expected Behavior

LCD should display "Hello World".

### Actual Behavior

LCD remains blank.

### Steps to Reproduce

1. Connect LCD.
2. Upload code.
3. Start simulation.
4. Observe LCD output.

### Severity

High

### Status

Open
