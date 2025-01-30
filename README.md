# Voron-Lineux-TC Configuration & Macros.

## Slicer Configuration.

### PrusaSlicer

#### Start G-Code
```
PRINT_START HOTEND={first_layer_temperature[initial_tool]} BED=[first_layer_bed_temperature] IS_MM_MODE=1 INITIAL_EXTRUDER=[initial_tool] IS_PS=1 {if is_extruder_used[0]}T0_TEMP_INITIAL={first_layer_temperature[0]} T0_TEMP={temperature[0]}{endif} {if is_extruder_used[1]}T1_TEMP_INITIAL={first_layer_temperature[1]} T1_TEMP={temperature[1]}{endif} {if is_extruder_used[2]}T2_TEMP_INITIAL={first_layer_temperature[2]} T2_TEMP={temperature[2]}{endif} {if is_extruder_used[3]}T3_TEMP_INITIAL={first_layer_temperature[3]} T3_TEMP={temperature[3]}{endif}{if is_extruder_used[4]}T4_TEMP_INITIAL={first_layer_temperature[4]} T4_TEMP={temperature[4]}{endif} {if is_extruder_used[5]}T5_TEMP_INITIAL={first_layer_temperature[5]} T5_TEMP={temperature[5]}{endif}
```

#### End G-Code
```
print_end UNLOAD_AT_END=1;end script from macro
```

#### After layer change G-Code
```
LIFTBAR_LAYER_CHANGE
```

#### Tool Change G-Code
```
# BEFORE_TOOL_CHANGE CURRENT_EXTRUDER=[current_extruder] NEXT_EXTRUDER=[next_extruder] OLD_FILAMENT_TEMP={temperature[current_extruder]} NEW_FILAMENT_TEMP={temperature[next_extruder]}
T[next_extruder]
# AFTER_TOOL_CHANGE CURRENT_EXTRUDER=[current_extruder] NEXT_EXTRUDER=[next_extruder] OLD_FILAMENT_TEMP={temperature[current_extruder]} NEW_FILAMENT_TEMP={temperature[next_extruder]}
```

### OrcaSlicer

#### Start G-Code
```
PRINT_START HOTEND=[nozzle_temperature_initial_layer] BED=[bed_temperature_initial_layer_single] Chamber=[chamber_temperature]  IS_MM_MODE=1 INITIAL_EXTRUDER=[initial_extruder] IS_OS=1 {if is_extruder_used[0]}T0_TEMP_INITIAL={nozzle_temperature_initial_layer[0]} T0_TEMP={nozzle_temperature[0]}{endif} {if is_extruder_used[1]}T1_TEMP_INITIAL={nozzle_temperature_initial_layer[1]} T1_TEMP={nozzle_temperature[1]}{endif} {if is_extruder_used[2]}T2_TEMP_INITIAL={nozzle_temperature_initial_layer[2]} T2_TEMP={nozzle_temperature[2]}{endif} {if is_extruder_used[3]}T3_TEMP_INITIAL={nozzle_temperature_initial_layer[3]} T3_TEMP={nozzle_temperature[3]}{endif} {if is_extruder_used[4]}T4_TEMP_INITIAL={nozzle_temperature_initial_layer[4]} T4_TEMP={nozzle_temperature[4]}{endif}
```

#### End G-Code
```
PRINT_END UNLOAD_AT_END=1
```

#### After layer change G-Code
```
LIFTBAR_LAYER_CHANGE
```

#### Tool Change G-Code
```
# BEFORE_TOOL_CHANGE CURRENT_EXTRUDER=[current_extruder] NEXT_EXTRUDER=[next_extruder] OLD_FILAMENT_TEMP={old_filament_temp} NEW_FILAMENT_TEMP={new_filament_temp} LAYER_NUM={layer_num}
T[next_extruder]
# AFTER_TOOL_CHANGE CURRENT_EXTRUDER=[current_extruder] NEXT_EXTRUDER=[next_extruder] OLD_FILAMENT_TEMP={old_filament_temp} NEW_FILAMENT_TEMP={new_filament_temp} LAYER_NUM={layer_num}

```
