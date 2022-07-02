# :chart_with_upwards_trend: risk-br

## Author & Date 

Emilio Maddalena, July 2022.

## Citing our Work

This dataset was gathered for the RISK project (SNF grant number 200021 17562). If you use of it for your own research, remember to cite

```
@misc{maddalena2021,
author = {Maddalena, Emilio T and Muller, Silvio A and Santos, Rafael M dos and Salzmann, Christophe and Jones, Colin N},
title = {Experimental Data-Driven Model Predictive Control of a Hospital HVAC System During Regular Use},
year = {2021},
journal = {arXiv preprint arXiv:2112.07323}
}
```

## Brief Description 

HVAC system data (7k+ points) from an industrial plant located in Campo Grande, Brazil. The time-series dataset is composed mainly of continuous features, with only a few exceptions. The sampling period is 10 mins.

## Long Description 

These are data from a hospital HVAC system composed of 3 Air-Handling Units (AHUs) and 3 thermal zones (rooms). The AHUs collect air from the external environment and reduce its temperature before pumping it into the rooms. Each AHU is responsible for a single room. The AHUs receive chilled water from a central chiller and can control the flow of water running through their cooling coils by means of valves. The air blowers are operated at constant speed. In principle, the HVAC system can only cool down the environment. No air-recirculation in the AHUs is permitted.

Rooms 1 and 3 are operating theaters, while room 2 is an intermediate room in which patients have to stay before being operated. Room 1 is only connected to room 2. Room 3 is only connected to room 2. Room 2 is connected to the rest of the surgery center. People are constantly entering and exiting these rooms, and doors are at times open, at times closed. 

A local weather station, located on the rooftop of the surgery center, measures and reports the current outdoor temperature and solar radiation.

The supply water temperature dynamics depends on external, exogenous factors. The chiller has also a cold water setpoint, which is manually set by the plant operators. The chiller internal control loop then regulates the water temperature around this value (probably with a simple hysteresis band).

**From a control perspective**: The system inputs are ``AHU_1_valve_POS``, ``AHU_2_valve_POS`` and ``AHU_3_valve_POS``. The outputs are ``room_1_temp``, ``room_2_temp``, ``room_3_temp``. The disturbances are ``OUT_ws_radiation``, ``OUT_ws_temperature``, ``AHU_1_waterIn_TEMP``, ``AHU_2_waterIn_TEMP`` and ``AHU_3_waterIn_TEMP``. Since the 3 AHUs are very close to each other and the water pipes are short, we expect that ``AHU_1_waterIn_TEMP`` = ``AHU_2_waterIn_TEMP`` = ``AHU_3_waterIn_TEMP`` at all times.

In principle, the HVAC system can only cool down the environment. However, if the external temperature is higher than the indoor one and the AHU water valves are completely closed, then hot air will be blown into the rooms, causing the indoor temperature to increase. Recall that the fans are operated at constant speed.

**When was it collected?** From July 7, 2021 to November 12, 2021. The supervisory system was not always ON throughout this period, and so the data are not one long time-series, but several smaller ones (see ``batch``).

**Sampling period**: 10 minutes.

## Folders

:file_folder: **data**: contains the data file ``riskbr_data.csv``.

:file_folder: **misc**: contains additional diagrams and pictures the cooling system and the hospital rooms.

## Measurements

``time`` \[GMT-4\]: date and time of the current measurements.

``AHU_1_air_FLOW`` \[m^3/min\]: the airfow rate inside AHU 1.

``AHU_2_air_FLOW`` \[m^3/min\]: the airfow rate inside AHU 2.

``AHU_3_air_FLOW`` \[m^3/min\]: the airfow rate inside AHU 3.

``AHU_1_valve_POS`` \[degs\]: the angular position (from 0 to 90) of AHU 1 three-way valve. 0 = min water flow, 90 = maximum water flow.

``AHU_2_valve_POS`` \[degs\]: the angular position (from 0 to 90) of AHU 2 three-way valve. 0 = min water flow, 90 = maximum water flow.

``AHU_3_valve_POS`` \[degs\]: the angular position (from 0 to 90) of AHU 3 three-way valve. 0 = min water flow, 90 = maximum water flow.

``AHU_1_waterIn_TEMP`` \[deg Celsius\]: supply water temperature for AHU 1.

``AHU_2_waterIn_TEMP`` \[deg Celsius\]: supply water temperature for AHU 2.

``AHU_3_waterIn_TEMP`` \[deg Celsius\]: supply water temperature for AHU 3.

``AHU_1_waterOut_TEMP`` \[deg Celsius\]: return water temperature for AHU 1.

``AHU_2_waterOut_TEMP`` \[deg Celsius\]: return water temperature for AHU 2.

``AHU_3_waterOut_TEMP`` \[deg Celsius\]: return water temperature for AHU 3.

``AHU_1_water_FLOW`` \[l/min\]: water flow rate inside the AHU 1 cooling coil.

``AHU_2_water_FLOW`` \[l/min\]: water flow rate inside the AHU 2 cooling coil.

``AHU_3_water_FLOW`` \[l/min\]: water flow rate inside the AHU 3 cooling coil.

``OUT_ws_radiation`` \[W/m^2\]: solar radiation measured by the local weather station.

``OUT_ws_temperature`` \[deg Celsius\]: outdoor temperature measured by the local weather station.

``room_1_temp`` \[deg Celsius\]: temperature inside room 1.

``room_2_temp`` \[deg Celsius\]: temperature inside room 2.

``room_3_temp`` \[deg Celsius\]: temperature inside room 3.

``room_1_supplyAir_temp`` \[deg Celsius\]: temperature of the air supplied to room 1.

``room_2_supplyAir_temp`` \[deg Celsius\]: temperature of the air supplied to room 2.

``room_3_supplyAir_temp`` \[deg Celsius\]: temperature of the air supplied to room 3.

``batch`` \[-\]: dataset subdivisions, indicating when the time-series were interrupted.
















