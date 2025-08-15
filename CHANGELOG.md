# Ender-5-pro-setup Changelog

## Marlin 2.0.8.2

### Changelog

### FIRST

Configuration.h Changes:

- #define MACHINE_UUID "1e5540b4-a5b7-41ec-aa53-3f4586587722"
- #define PIDTEMPBED // uncommented
- #define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 800, 100 }
  - (factory: { 80, 80, 800, 93 } )
- #define S_CURVE_ACCELERATION // uncommented
- #define USE_PROBE_FOR_Z_HOMING
- #define BLTOUCH
- #define NOZZLE_TO_PROBE_OFFSET { -40.28, -8, 0 }
- #define PROBING_MARGIN 20
- #define Z_MIN_PROBE_REPEATABILITY_TEST
- #define DELAY_BEFORE_PROBING 200  // (ms) To prevent vibrations from triggering piezo sensors
- // Require minimum nozzle and/or bed temperature for probing
   #define PREHEAT_BEFORE_PROBING
   #if ENABLED(PREHEAT_BEFORE_PROBING)
   #define PROBING_NOZZLE_TEMP 210   // (°C) Only applies to E0 at this time
   #define PROBING_BED_TEMP     70
   #endif
  - factory: #define PROBING_NOZZLE_TEMP 120
               #define PROBING_BED_TEMP     50

- #define DISABLE_REDUCED_ACCURACY_WARNING
- #define AUTO_BED_LEVELING_UBL
- #define RESTORE_LEVELING_AFTER_G28
- #define PREHEAT_BEFORE_LEVELING
  #if ENABLED(PREHEAT_BEFORE_LEVELING)
  #define LEVELING_NOZZLE_TEMP 210   // (°C) Only applies to E0 at this time
  #define LEVELING_BED_TEMP     70
  #endif
  - factory:   #define LEVELING_NOZZLE_TEMP 120
                  #define LEVELING_BED_TEMP     50

- #define G26_MESH_VALIDATION
- #define MESH_EDIT_GFX_OVERLAY   // Display a graphics overlay while editing the mesh
- #define MESH_INSET 35             // Set Mesh bounds as an inset region of the bed
- #if ENABLED(LCD_BED_LEVELING)
  #define MESH_EDIT_Z_STEP  0.02 // (mm) Step size while manually probing Z axis.
  #define LCD_PROBE_Z_RANGE 4     // (mm) Z Range centered on Z_MIN_POS for LCD Z adjustment
  //#define MESH_EDIT_MENU        // Add a menu to edit mesh points
  #endif

- #define LEVEL_BED_CORNERS
- #define LEVEL_CORNERS_INSET_LFRB { 51, 51, 51, 51 } // (mm) Left, Front, Right, Back insets
- #define Z_SAFE_HOMING#define PREHEAT_2_TEMP_BED     100

-----

### SECOND

  // Creality Ender-5 Pro
  #if ENABLED(PID_PARAMS_PER_HOTEND)
    // Specify between 1 and HOTENDS values per array.
    // If fewer than EXTRUDER values are provided, the last element will be repeated.
    #define DEFAULT_Kp_LIST {  21.73,  21.73 }
    #define DEFAULT_Ki_LIST {   1.54,   1.54 }
    #define DEFAULT_Kd_LIST {  76.55,  76.55 }
  #else
    #define DEFAULT_Kp  19.72
    #define DEFAULT_Ki   1.40
    #define DEFAULT_Kd  69.54
  #endif
    - factory:
    #define DEFAULT_Kp  21.73
    #define DEFAULT_Ki   1.54
    #define DEFAULT_Kd  76.55

- #define PIDTEMPBED // commented out, disabled
- #define NOZZLE_TO_PROBE_OFFSET { -41.9, -4.9, -1.92 }
- #define PROBING_MARGIN 10
- #define PROBING_FANS_OFF          // Turn fans off when probing
- //#define PREHEAT_BEFORE_PROBING // disabled again
- #define AUTO_BED_LEVELING_BILINEAR
- #if ENABLED(PREHEAT_BEFORE_LEVELING)
  #define LEVELING_NOZZLE_TEMP  0   // (°C) Only applies to E0 at this time
  #define LEVELING_BED_TEMP     80
- #define GRID_MAX_POINTS_X 5
- #define ABL_BILINEAR_SUBDIVISION

-----

### THIRD and FINAL (never uploaded to printer) - plan to upgrade to 2.1.2.5

- #define LEVELING_BED_TEMP     60 // from 80
- #define MESH_TEST_HOTEND_TEMP  195    // from 205 (°C) Default nozzle temperature for G26.
- #define LEVEL_CORNERS_Z_HOP       5.0   // (mm) Z height of nozzle between leveling points
  #define LEVEL_CENTER_TOO  
- #define PREHEAT_1_TEMP_BED     60 // from 45

-----

Confirguration_adv.h

- #define HOTEND_IDLE_TIMEOUT
  - #define HOTEND_IDLE_TIMEOUT_SEC (10*60)
- #define BLTOUCH_HS_MODE
- #define MOVE_Z_WHEN_IDLE              // Jump to the move Z menu on doubleclick when printer is idle.
- #define BABYSTEP_ZPROBE_OFFSET          // Combine M851 Z and Babystepping
- #define BABYSTEP_ZPROBE_GFX_OVERLAY   // Enable graphical overlay on Z-offset editor
