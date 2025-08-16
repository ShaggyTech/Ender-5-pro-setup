# Ender-5-pro-setup Changelog

## Marlin 2.0.8.2

### v1.0

Commit: [config customization 06-03-21 2:30pm](https://github.com/ShaggyTech/Ender-5-pro-setup/commit/f2537baa6ecca22639c22557e3a88ce66699bc90)

* `turned ON / turned OFF` = has no explicit value, comment or uncomment the setting or add as a new line to turn it on or off

#### **`Configuration.h`**

| Setting                                                              | Value                                            | Units       | Description                                                                                                                                                              |
| :------------------------------------------------------------------- | :----------------------------------------------- | :---------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MACHINE_UUID                                                         | `"1e5540b4-a5b7-41ec-aa53-3f4586587722"`         | string      |                                                                                                                                                                          |
| PIDTEMPBED                                                           | turned ON                                        | on/off      | note: this was turned off in newer commit as it caused problems                                                                                                          |
| DEFAULT_AXIS_STEPS_PER_UNIT                                          | `{ 80, 80, 800, 93 }` ->  `{ 80, 80, 800, 100 }` | dict        |                                                                                                                                                                          |
| S_CURVE_ACCELERATION                                                 | turned ON                                        | on/off      |                                                                                                                                                                          |
|                                                                      |                                                  |             |                                                                                                                                                                          |
| **# BLTOUCH**                                                        |                                                  |             |                                                                                                                                                                          |
| Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN                                   | turned ON                                        | on/off      | The probe replaces the Z-MIN endstop and is used for Z homing.                                                                                                           |
| USE_PROBE_FOR_Z_HOMING                                               | turned ON                                        |             | Force the use of the probe for Z-axis homing                                                                                                                             |
| BLTOUCH                                                              | turned ON                                        | on/off      | The BLTouch probe uses a Hall effect sensor and emulates a servo.                                                                                                        |
| NOZZLE_TO_PROBE_OFFSET ***(adjusted in 2.0)***                       | `{ -40.28, -8, 0 }`                              | dict        | Nozzle-to-Probe offsets { X, Y, Z } Postive: Back and Right \| Negative: Front and Left                                                                                  |
| PROBING_MARGIN ***(reverted in 2.0)***                               | `10` -> `20`                                     | number (mm) | Most probes should stay away from the edges of the bed, but with NOZZLE_AS_PROBE this can be negative for a wider probing area.                                          |
| Z_MIN_PROBE_REPEATABILITY_TEST                                       | turned ON                                        | on/off      | Enable the M48 repeatability test to test probe accuracy                                                                                                                 |
| DELAY_BEFORE_PROBING                                                 | `200`                                            | number (ms) | To prevent vibrations from triggering piezo sensors                                                                                                                      |
| PREHEAT_BEFORE_PROBING ***(reverted in 2.0)***                       | turned ON                                        | on/off      | Require minimum nozzle and/or bed temperature for probing                                                                                                                |
| __ PROBING_NOZZLE_TEMP 210   // (°C) Only applies to E0 at this time | `120` -> `210`                                   | number (°C) | Only applies to E0 at this time                                                                                                                                          |
| __ PROBING_BED_TEMP                                                  | `50` -> `70`                                     | number (°C) |                                                                                                                                                                          |
| DISABLE_REDUCED_ACCURACY_WARNING                                     | turned ON                                        | on/off      | Turn off the display blinking that warns about possible accuracy reduction                                                                                               |
| AUTO_BED_LEVELING_UBL                                                | turned ON                                        | on/off      |                                                                                                                                                                          |
| RESTORE_LEVELING_AFTER_G28                                           | turned ON                                        | on/off      | Normally G28 leaves leveling disabled on completion. Enable one of these options to restore the prior leveling state or to always enable leveling immediately after G28. |
| PREHEAT_BEFORE_LEVELING                                              | turned ON                                        | on/off      | Auto-leveling needs preheating                                                                                                                                           |
| __ LEVELING_NOZZLE_TEMP                                              | `120` -> `210`                                   | number (°C) | Only applies to E0 at this time                                                                                                                                          |
| __ LEVELING_BED_TEMP                                                 | `50` -> `70`                                     | number (°C) |                                                                                                                                                                          |
| G26_MESH_VALIDATION                                                  | turned ON                                        | on/off      | Enable the G26 Mesh Validation Pattern tool.                                                                                                                             |
| MESH_EDIT_GFX_OVERLAY                                                | turned ON                                        | on/off      | Display a graphics overlay while editing the mesh                                                                                                                        |
| MESH_INSET                                                           | `1` -> `35`                                      | number      | Set Mesh bounds as an inset region of the bed                                                                                                                            |
| UBL_MESH_WIZARD                                                      | turned ON                                        | on/off      | Run several commands in a row to get a complete mesh                                                                                                                     |
| LCD_BED_LEVELING                                                     | turned ON                                        | on/off      | Add a bed leveling sub-menu for ABL or MBL. Include a guided procedure if manual probing is enabled.                                                                     |
| __ MESH_EDIT_Z_STEP                                                  | `0.025` -> `0.02`                                | number (mm) | Step size while manually probing Z axis.                                                                                                                                 |
| LEVEL_BED_CORNERS                                                    | turned ON                                        | on/off      | Add a menu item to move between bed corners for manual bed adjustment                                                                                                    |
| LEVEL_CORNERS_INSET_LFRB                                             | `{ 30, 30, 30, 30 }` -> `{ 51, 51, 51, 51 }`     | number (mm) | Left, Front, Right, Back insets                                                                                                                                          |
| Z_SAFE_HOMING                                                        | turned ON                                        | on/off      | Move the Z probe (or nozzle) to a defined XY point before Z Homing. Prevent Z homing when the Z probe is outside bed area.                                               |
|                                                                      |                                                  |             |                                                                                                                                                                          |
| PREHEAT_2_TEMP_BED                                                   | `70` -> `100`                                    | number (°C) | ABS Preheat Constants                                                                                                                                                    |

---

#### **`Configuration_adv.h`**

| Setting                                    | Value                   | Units       | Description                                                                                                                     |
| :----------------------------------------- | :---------------------- | :---------- | :------------------------------------------------------------------------------------------------------------------------------ |
| HOTEND_IDLE_TIMEOUT                        | turned ON               | on/off      |                                                                                                                                 |
| __ HOTEND_IDLE_TIMEOUT_SEC                 | `(5\*60)` -> `(10\*60)` | number (s)  | Time without extruder movement to trigger protection                                                                            |
| BLTOUCH_HS_MODE                            | turned ON               | on/off      |                                                                                                                                 |
| **BABYSTEP_INVERT_Z** -- **Revert this??** | `false` -> `true`       | boolean     | Change if Z babysteps should go the other way                                                                                   |
| MOVE_Z_WHEN_IDLE                           | `false` -> `true`       | boolean     | Jump to the move Z menu on doubleclick when printer is idle.                                                                    |
| BABYSTEP_ZPROBE_OFFSET                     | turned ON               | on/off      | Combine M851 Z and Babystepping                                                                                                 |
| BABYSTEP_ZPROBE_GFX_OVERLAY                | turned on               | on/off      | Enable graphical overlay on Z-offset editor                                                                                     |
| PROBING_MARGIN                             | `20` -> `10`            | number (mm) | Most probes should stay away from the edges of the bed, but with NOZZLE_AS_PROBE this can be negative for a wider probing area. |

-----

### v2.0

Commit: [small config changes/tweaks](https://github.com/ShaggyTech/Ender-5-pro-setup/commit/c9156853b68124e16fc0b7a063f3bbfcbb31afb1)

* PID Hotend Kp/Ki/Kd: updated
* PID Bed Heating: turned OFF
* bed leveling: nozzle to probe offset updated
* bed leveling: probing margin updated, probing fans off, preheat before probing off
* bed leveling: preheat before leveling bed and nozzle temp changed
* bed leveling: max grid points increase from 3 to 5
* bed leveling: turn on ABL BILINEAR SUBDIVISION

## **`Configuration.h`**

| Setting                    | Value                                           | Units       | Description                                                                                                                                      |
| :------------------------- | :---------------------------------------------- | :---------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| PID_PARAMS_PER_HOTEND      |                                                 |             |                                                                                                                                                  |
| __ DEFAULT_Kp              | `21.73` -> `19.72`                              | number      |                                                                                                                                                  |
| __ DEFAULT_Ki              | `1.54` -> `1.40`                                | number      |                                                                                                                                                  |
| __ DEFAULT_Kd              | `76.55` -> `69.54`                              | number      |                                                                                                                                                  |
| PIDTEMPBED                 | turned OFF                                      | on/off      | PID Bed Heating                                                                                                                                  |
|                            |                                                 |             |                                                                                                                                                  |
| **# BLTOUCH**              |                                                 |             |                                                                                                                                                  |
| NOZZLE_TO_PROBE_OFFSET     | `{ -40.28, -8, 0 }` -> `{ -41.9, -4.9, -1.92 }` | dict        | Nozzle-to-Probe offsets { X, Y, Z } Postive: Back and Right \| Negative: Front and Left                                                          |
| PROBING_MARGIN             | `20` -> `10`                                    | number (mm) | Most probes should stay away from the edges of the bed, but with NOZZLE_AS_PROBE this can be negative for a wider probing area.                  |
| PROBING_FANS_OFF           | turned ON                                       | on/off      | Turn fans off when probing                                                                                                                       |
| PREHEAT_BEFORE_PROBING     | turned OFF                                      | on/off      | Require minimum nozzle and/or bed temperature for probing                                                                                        |
| AUTO_BED_LEVELING_BILINEAR | turned ON                                       | on/off      | Probe several points in a grid. You specify the rectangle and the density of sample points. The result is a mesh, best for large or uneven beds. |
| PREHEAT_BEFORE_LEVELING    |                                                 |             |                                                                                                                                                  |
| __ LEVELING_NOZZLE_TEMP    | `210` -> `0`                                    | number (°C) | Only applies to E0 at this time                                                                                                                  |
| __ LEVELING_BED_TEMP       | `70` -> `80`                                    | number (°C) |                                                                                                                                                  |
| GRID_MAX_POINTS_X          | `3` -> `5`                                      | number      | Set the number of grid points per dimension.                                                                                                     |
| ABL_BILINEAR_SUBDIVISION   | turned ON                                       | on/off      | Experimental Subdivision of the grid by Catmull-Rom method. Synthesizes intermediate points to produce a more detailed mesh.                     |

---

### v3.0 (maybe never uploaded to printer?)

Commit: [config: bed temp and other small changes](https://github.com/ShaggyTech/Ender-5-pro-setup/commit/bbdc58daf76936f1930a08b3883ab003ec182ba3)

* preheat: change PLA preheat beed temperature from 80 to 60
* bed leveling: level center and add 1mm to LEVEL_CORNERS_Z_HOP
* bed leveling: bed temp during bed mesh level test: 80 to 60
* bed leveling: MESH_TEST_HOTEND_TEMP: temp: 205 to 195

## `Configuration.h`

| Setting               | Value      | Units       | Description |
| :-------------------- | :--------- | :---------- | ----------- |
| **# BLTOUCH**         |            |             |             |
| LEVELING_BED_TEMP     | 80 -> 60   | number (°C) |             |
| MESH_TEST_HOTEND_TEMP | 205 -> 195 | number (°C) |             |
| LEVEL_CORNERS_Z_HOP   | 4.0 -> 5.0 | number (mm) |             |
| PREHEAT_1_TEMP_BED    | 45 -> 60   | number (°C) |             |
| LEVEL_CENTER_TOO      | turned ON  | on/off      |             |

---

## Current Settings Overview

---

### PIDs

#### Hot End

Marlin 2.0.8.2

In order of changes, oldest to most recent:

v1.0
`DEFAULT_Kp  21.73`
`DEFAULT_Ki   1.54`
`DEFAULT_Kd  76.55`

v2.0
`DEFAULT_Kp  19.72`
`DEFAULT_Ki   1.40`
`DEFAULT_Kd  69.54`

#### Heated Bed

PID turned off for bed heating, maybe not compatible, uses Bang Bang just fine

---

### Misc

Nozzle Probe Offset:

* `NOZZLE_TO_PROBE_OFFSET { -41.9, -4.9, -1.92 }`