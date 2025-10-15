# Overview

This project demonstrates the use of Message Passing Interface (MPI) and OpenMP to perform distributed environmental data analysis.
The system analyzes large-scale pollution datasets to identify:
1. Major Contributing Pollutants responsible for wildfire-prone conditions
2. Hotspot Regions with high pollution or environmental stress, based on spatial clustering
By combining parallel data loading, filter-based pollutant analysis, and geospatial hotspot detection, this project showcases how high-performance computing can accelerate environmental data analytics.

# Key Features

MPI-based Parallelization – Distributes workload across multiple processes for faster computation
OpenMP Support – Enables shared-memory parallelism within each MPI process
Automated Data Loading – Recursively reads CSV datasets organized by date folders using Windows API
Pollutant-Specific Filtering – Analyzes OZONE, NO₂, SO₂, CO, PM₂.₅, and PM₁₀ pollutants
Hotspot Detection – Identifies clusters of pollution intensity using geospatial proximity thresholds

# Build Steps

# Compile Analysis 1
```
mpic++ -O3 -fopenmp loadData.cpp analyzeData.cpp analyzeHotspot.cpp main.cpp -o main.exe
```

# Compile Analysis 2
```
mpic++ -O3 -fopenmp loadDataHotspot.cpp analyzeHotspot.cpp main2.cpp -o main2.exe
```

# Run with multiple processes
```
mpirun -np 4 ./main.exe
mpirun -np 4 ./main2.exe
```
# Output
Analysis 1: Major Pollutant
Displays pollutant-wise record counts and identifies the most frequent pollutant associated with wildfire events.
Example Output:
```
Total records processed: 54231
Total from pollutant OZONE: 15421
Total from pollutant PM2.5: 23987
Pollutant with maximum count: PM2.5 (23987)
Elapsed time: 3045 ms

```
Analysis 2: Hotspot Detection
Displays number of detected hotspots and processing time.
Example Output:
```
Total number of distinct hotspots: 128
Elapsed time: 2750 ms
```
