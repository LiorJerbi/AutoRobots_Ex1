# GNSS Raw Measurements Processing

## Overview

This project provides a solution for processing GNSS (Global Navigation Satellite System) raw measurements. It includes functionalities to parse raw measurement log files, compute positioning using a naive algorithm, and generate visualization outputs in KML format.

The algorithm implements the process of computing satellite positions from orbital parameters and transmission time. The results provide the x, y, and z coordinates of each satellite at the given transmission time. the position of the receiver is estimated using pseudorange measurements from multiple satellites, with the least squares approach we iteratively refine the estimate by minimizing the difference between predicted and measured pseudoranges, and clock bias estimates, while minimizing the impact of unusually differnt satellite readings.

## Requirements

To run this project, you need:

- Python 3.x
- pandas
- numpy
- navpy
- gnssutils
- simplekml
- georinex
- unlzw3

You can install the dependencies using pip:

```bash
pip install pandas numpy navpy gnssutils simplekml georinex unlzw3
```

## Usage
- 1. Clone this repository:
```bash
git clone https://github.com/LiorJerbi/AutoRobots_Ex1
```
- 2. Navigate to the project directory:
```bash
cd AutoRobots_Ex1
```

## How to run
```bash
put your gnss raw measurments txt files in the main folder(AutoRobots_Ex1)
```
- open the "GnssToPosition.py" file and change the input file at the beginning of the code
```bash
###################################################################################
################################ CHANGE FILE NAME #################################

input_filepath = os.path.join('gnss_log_2024_04_13_19_51_17.txt')

################################ CHANGE FILE NAME #################################
###################################################################################
```
- run cmd in the main folder and write the next code:
```bash
python GnssToPosition.py
```

## Output
The script generates the following outputs:
1. GnssToRoute.kml: KML file containing the computed path with timestamps for each position.
2. GNSStoPosition.csv: CSV file with the computed positions and additional columns (Pos.X, Pos.Y, Pos.Z, Lat, Lon, Alt).

## Results
here is a part example of the driving measurement (gnss_log_2024_04_13_19_51_17.txt) of the nmea file

![alt text](https://i.imgur.com/dkPXB3F.jpeg)

and this is after our algorithm

![alt text](https://i.imgur.com/unRZKFd.jpeg)

the results are quite similar and on average difference is around 30 meters at most, using the Haversine Formula to calculate.


## Contributors
- Yael Rosen - 209498211
- Tomer Klugman - 312723612
- Hadas Evers - 206398984
- Lior Jerbi - 314899493
