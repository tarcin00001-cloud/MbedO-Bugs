# Bug Submission Guide

## Purpose

This document defines the standard process for reporting, documenting, and tracking defects identified within the Mbed0 Simulation Platform.

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

# Search Existing Issues

Before creating a new issue:

1. Open the **Issues** page.
2. Search using relevant keywords.
3. Check both Open and Closed issues.
4. If a matching issue exists, add comments or additional evidence instead of creating a new report.

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

## Step 2: Create a Meaningful Title

GitHub automatically assigns issue numbers.

Use a descriptive title that clearly explains the issue.

### Good Examples

```text
LCD Works in C++ but Not in MicroPython

Push Button Counter Does Not Increment

RGB LED Brightness Decreases During Color Cycling

Buzzer Does Not Activate Below Distance Threshold
```

### Bad Examples

```text
Not Working

Error

Problem Found

LCD Issue
```

---

# Required Information

Every bug report must contain the following sections.

---

## Environment Information

### Simulator Version

```text
v1.0.0
```

### Board

Examples:

```text
Raspberry Pi Pico
ESP32
Arduino UNO
Arduino Nano
Arduino Mega
```

### Runtime

Examples:

```text
MicroPython
C++
```

### Component

Examples:

```text
LCD
Push Button
Buzzer
Servo
RGB LED
Sensor
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

## Impact

Describe how the issue affects users.

### Examples

```text
Prevents project execution.

Produces incorrect simulation results.

Affects all LCD projects using MicroPython.

Causes simulator instability.
```

---

## Reproducibility

Select one:

* [ ] Always reproducible
* [ ] Sometimes reproducible
* [ ] Rarely reproducible
* [ ] Unable to reproduce consistently

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

## Attachments

Attach any relevant evidence:

* Screenshots
* Videos
* Project files
* Circuit diagrams
* Console logs
* Error messages

---

## Screenshots

Attach screenshots showing:

* Circuit setup
* Runtime output
* Error messages
* Unexpected behavior

Screenshots significantly improve issue investigation.

---

## Video Evidence (Optional)

Attach a short screen recording if the issue involves:

* Timing problems
* Animation issues
* UI behavior
* Sensor updates
* Intermittent failures

---

# Severity Classification

## Critical

Platform functionality is unusable.

Examples:

* Simulator crashes
* Runtime crashes
* Project cannot execute
* Data corruption

---

## High

Major functional failure.

Examples:

* GPIO not working
* LCD not displaying
* Sensor values incorrect
* Communication failure

---

## Medium

Partial feature failure.

Examples:

* Delayed response
* Incorrect timing behavior
* Display glitches

---

## Low

Minor issue.

Examples:

* UI alignment
* Documentation issue
* Label mismatch
* Cosmetic defects

---

# Labels

Apply appropriate labels where possible.

## Board

```text
board:pico
board:esp32
board:arduino
```

## Runtime

```text
runtime:micropython
runtime:cpp
```

## Component

```text
component:lcd
component:button
component:buzzer
component:servo
component:rgb-led
component:sensor
```

## Priority

```text
priority:critical
priority:high
priority:medium
priority:low
```

---

# Root Cause Analysis Process

Once investigation begins, the issue should be updated with:

## Root Cause

Example:

```text
LCD initialization sequence differs between C++ and MicroPython runtime implementation.
```

## Impact Analysis

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
* [ ] Evidence updated
* [ ] Verification completed

---

# Issue Workflow

Every issue progresses through the following stages:

```text
Backlog
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

## Title

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

### Impact

Users cannot execute LCD-based MicroPython projects successfully.

### Reproducibility

Always reproducible.

### Steps to Reproduce

1. Connect LCD.
2. Upload code.
3. Start simulation.
4. Observe LCD output.

### Severity

High

### Status

Backlog

```
```
