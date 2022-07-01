# :chart_with_upwards_trend: risk-br

## Author & Date 

Emilio Maddalena, September 2021.

## Brief Description 

HVAC system data (4.5k+ points) from an industrial plant located in Campo Grande, Brazil. The time-series dataset is composed mainly of continuous features, with only a few exceptions.

## Long Description 

These are data from a hospital HVAC system composed of 3 Air-Handling Units (AHUs) and 3 thermal zones (rooms). The AHUs collect air from the external environment and reduce its temperature before pumping it into the rooms. Each AHU is responsible for a single room. The AHUs receive chilled water from a central chiller and can control the flow of water running through their cooling coils by means of three-way valves. The air blowers are operated at constant speed. In principle, the HVAC system can only cool down the environment. No air-recirculation in the AHUs is permitted.

Rooms 1 and 3 are operating theaters, while room 2 is an intermediate room in which patients have to stay before being operated. Room 1 is only connected to room 2. Room 3 is only connected to room 2. Room 2 is connected to the rest of the surgery center. People are constantly entering and exiting these rooms, and doors are at times open, at times closed. 

A local weather station, located on the rooftop of the surgery center, measures and reports the current outdoor temperature and solar radiation.

The cold water supplied by the chilled receives thermal energy not only from the 3 aforementioned AHUs, but also from 4 additional larger AHUs responsible for cooling the rest of the surgery center; these are not controlled, nor monitored. As a result, the supply water temperature dynamics depends on external, exogenous factors. The chiller has also a cold water setpoint, which is manually set by the plant operators. The chiller internal control loop then regulates the water temperature around this value (probably with a simple hysteresis band).

**From a control perspective**: The system inputs are ``AHU_1_valve_POS``, ``AHU_2_valve_POS`` and ``AHU_2_valve_POS``. The outputs are ``room_1_temp``, ``room_2_temp``, ``room_3_temp``. The disturbances are ``OUT_ws_radiation``, ``OUT_ws_temperature``, ``AHU_1_waterIn_TEMP``, ``AHU_2_waterIn_TEMP`` and ``AHU_3_waterIn_TEMP``. Since the 3 AHUs are very close to each other and the water pipes are short, we expect that ``AHU_1_waterIn_TEMP`` = ``AHU_2_waterIn_TEMP`` = ``AHU_3_waterIn_TEMP``.

In principle, the HVAC system can only cool down the environment. However, if the external temperature is higher than the indoor one and the AHU water valves are completely closed, then hot air will be blown into the rooms, causing the indoor temperature to increase. Recall that the fans are operated at constant speed.

**When was it collected?** From July 7, 2021 to August 12, 2021. The supervisory system was not always ON throughout this period, and so the data are not one long time-series, but several smaller ones (see ``batch``).

**Sampling period**: 10 minutes.

## Folders/Files

:file_folder: **data**: contains the data files.

``raw_2021-07-07_2021-08-12.csv``: Original dataset as extracted from the local database.

``clean_2021-07-07_2021-08-12.csv``: A pre-processed version of the latter file, better suited to system identification. The time-series cleaning stage consisted of excluding outliers, imputing new (sensible) values, removing unimportant measurements and relabling some signals. Finally, the column ``batch`` was added, indicating the time discontinuities in the dataset, as can be also inferred from the ``time`` column.

:file_folder: **docs**: contains additional diagrams to better illustrate the system architecture as well as some nice pictures :).

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
















