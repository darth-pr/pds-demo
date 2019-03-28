# Cassini Magnetometer - Planetary Data System User’s Guide

# 1. Introduction
## 1.1 Purpose
The Cassini Magnetometer Planetary Data System User’s Guide describes the Cassini magnetometer data available from the Planetary Data System (PDS) and how to use them for
scientific research. The guide is divided into seven sections, which include the following:

1. an introduction to the Cassini magnetometer instrument and datasets available from PDS,
2. an explanation of the calibrations of the instrument data and calibration tools on PDS,
3. a description of the Cassini magnetometer data sets archived with PDS,
4. detailed instructions on how to search for and obtain Cassini magnetometer data from PDS,
5. examples with step-by-step instructions on how to use the data for scientific research, and
6. additional useful information, web sources and external tools that a user may need when using the data

The examples in sections 6 demonstrate the following:
- how to find and use the calibrated data for studying the Saturnian magnetosphere
- how to transfer the data into a moon interaction coordinate system for studying moonmagnetosphere interactions
- how to use the calibration tools to process the raw data on PDS.
These examples will be most useful to those who already have some knowledge of the Cassini
magnetometer instrument, but would like to learn how to use the data.

# 2. The Cassini magnetometer instrument
## 2.1 Instrument overview
Magnetometers are direct-sensing instruments that detect and measure the strength and orientation of magnetic fields. The Cassini Dual Technique Magnetometer (MAG) measures magnetic fields in the vicinity of the Cassini obiter during its mission. The MAG instrument consists of two independent magnetometers, a common data processing unit, three power supplies, and associated operating software and electronics.

The first magnetometer, the vector/scalar helium magnetometer (V/SHM), is capable of two modes of operation. In vector mode, it measures three orthogonal components of the magnetic field, allowing determination of the field magnitude and direction. Using two dynamically selectable ranges of operation, vector fields up to ±256 nT may be measured. In scalar mode, in which only the field magnitude is measured, the magnetometer is capable of measuring fields in the range 256 to 16384 nT. The V/SHM and its electronics have been provided for the Cassini mission by the Jet Propulsion Laboratory (JPL).

The second magnetometer, the fluxgate magnetometer (FGM), uses three orthogonal ringcore fluxgate sensors to make vector field measurements. This magnetometer operates in one of four dynamically selectable ranges, allowing the measurement of fields up to ±44000 nT. The FGM and its electronics have been provided for the mission by Imperial College, London.

The instrument data processing unit (DPU) interfaces with the spacecraft Command and Data Subsystem through the JPL-designed bus interface unit (BIU). All commands, data, and processor program changes are received or transmitted through the BIU. Three power supplies and the 28 V spacecraft bus power the MAG components. Power supply 0 powers the BIU and the DPU core. Power supplies 1 and 2 are redundant and power the remainder of the instrument.

The magnetometers are sensitive to field distortions caused by electric currents and ferrous components onboard the spacecraft. To minimize these spurious effects the sensors are located on an 11 m boom which was deployed from the spacecraft before the first magnetic-field measurements were made. For the Cassini mission, the FGM sensor is located midway along the magnetometer boom and the V/SHM sensor is at the end of the boom.

## 2.2 Instrument modes

The vector helium magnetometer (V/SHM) can operate in both the vector mode (VHM) and the scalar mode (SHM), which have two and one dynamic ranges respectively. The fluxgate magnetometer (FGM) has four dynamic ranges. All these ranges and the corresponding sensor
resolutions are listed in Table 2.1.

|Sensor | Range Label | Range (nT) | Resolution (nt) |
|---  |--- |--- |--- |
| VHM | R0 | ±32 | 0.0039 |
| VHM | R1 | ±256 | 0.0312 |
| SHM | - | 256-16384 | 0.036 |
| FGM | R0 | ±40 | 0.004 |
| FGM | R1 | ±400 | 0.048 |
| FGM | R2 | ±10000 | 1.2 |
| FGM | R3 | ±44000 | 5.4 |

Switching between ranges in normal operations is automatic, controlled by the Data Processing Unit (DPU). The DPU monitors each component field value. If the magnitude of any component exceeds an upper threshold for greater than a specified number of samples, the DPU will switch the instrument to a higher range. Similarly, if the magnitudes of all three components fall below a lower threshold for more than a specified number of samples, the DPU will switch the instrument to a lower range (Dougherty et al., 2004).

## 2.3 Scientific objectives of Cassini MAG instrument

The primary objectives of the Cassini MAG instruments are to determine the detailed structure of the planetary magnetic field and to study the physical processes in the planetary system that are associated with the magnetic field. In particular, the MAG instruments will endeavor to:

- determine the internal magnetic field of Saturn
- develop a three-dimensional model of Saturn's magnetosphere
- determine the magnetic state of Titan and its atmosphere
- derive an empirical model of the Titan electromagnetic environment
- investigate the interactions of Titan with the magnetosphere, magnetosheath, and solar wind
- survey the ring and dust interactions with the electromagnetic environment
- study the interactions of the icy satellites with the magnetosphere of Saturn
- investigate the structure of the magnetotail and the dynamic processes at the icy satellites

## 2.4 Strategies behind the planning and implementation of observation patterns

The MAG instruments are sensitive to field distortions caused by electric currents and ferrous components onboard the spacecraft. To minimize these spurious effects, the sensors are located on an 11 m boom which was deployed from the spacecraft before the first magnetic-field measurements were made. The two FGM sensors are mounted midway along the magnetometer boom (5.814 m from the spacecraft centre) and the V/SHM sensor is mounted at the end of the boom (11.015 m from the spacecraft centre). Spacing the FGM and V/SHM at different distances along the boom allows the spacecraft-generated field to be better characterized and removed from the observations during calibration process. 

The advantage of having both FGM and V/SHM measurements is to improve the accuracy during high field operation of the instrument. In the past, a problem with achieving high accuracy from vector measurements has been the precise attitude knowledge required. The FGM has a large dynamic range and shortcomings in deriving accurate estimates of weak field components in a strong field. But with the SHM, this problem is avoided by measuring the field magnitude directly by way of a resonance magnetometer. This improved accuracy of the SHM is especially important for determining the 4th and 5th order moments of Saturn’s internal field because the SHM measurements close to the planet have better accuracy than those from the FGM. More details of this strategy are discussed in Dougherty et al. (2004). The V/SHM failed on 17 November 2005, and thereafter cross-calibration between FGM and V/SHM was no longer possible. In addition, the VHM optimizes low frequency vector measurements in low fields, and the FGM operates best at high frequency and over an extremely wide dynamic range. The twin sensor configuration of FGM also contributes to overall instrument reliability. If one sensor fails, field measurements can be made with the other sensor, with sufficient performance to achieve many of the major objectives of the investigation. Reliability has been further increased by the provision of redundant instrument power supplies and data processing units and by careful selection of electronic components which can survive the radiation environments encountered during the long cruise phase of the mission and in the Saturnian system.

## 2.5 Instrument limitations and factors affecting instrument data

As discussed above, the MAG instrument is mounted on a boom to minimize the interference from the spacecraft-generated fields. However, the mounting of the sensors on a boom could result in their orientation with respect to the spacecraft axes changing from time to time, especially after spacecraft maneuvers. Thus a means of sensor alignment determination has been provided by the Cassini project, the Science Calibration Subsystem (SCAS). The SCAS consists of two coils rigidly mounted on the spacecraft body with a known alignment to the spacecraft axes. These produce well-defined magnetic fields on command which can be detected by the sensors and used to correct for any changes in sensor orientation. 
An implicit feature of the SHM is the null zone which arises if the ambient field falls outside a cone of 45 degree half angle with respect to the optical axis of the magnetometer. This results in the signal being dramatically weakened and the absolute accuracy of the instrument will suffer. Thus a requirement has been placed on the Cassini mission to avoid spacecraft orientations inside of 4 Saturn radii which will cause the planetary field to lie within the null zones of the scalar device.