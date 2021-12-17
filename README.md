## Paper code of "Strategies for COVID-19 vaccination  under a shortage scenario: a geo-stochastic modelling approach."
#### authors: N. L. Barreiro, C. I. Ventura, T. Govezensky, M. Núñez, P. G. Bolcatto, and R. A. Barrio
#### code author: Dr. Nadia Barreiro

For questions please contact nadus.barreiro@gmail.com

### General Ideas of the model

In order to implement the model, a geographical map of the region of interest is divided into square cells with coordinates (i,j), covering the whole region.  Roads between cities were used to allow short or long distance travelling within the grid.
The maps and roads arrays of each country were uploaded in csv format.

The present  model includes the virus spreading at two levels: 
(i) Local dynamics: consisting of a compartmental model whose constant parameters are related to the specific disease agent and the host’s immune response
(ii) Global dynamics of geographical disease spreading: involving mobility parameters related to social habits of the country and affected, at different times, by different non-pharmaceutical interventions by the  different governments.

The local dynamics within each cell is calculated using a SEIRs type model adding and extra comparment for vaccination. A local stochasticity is also added in order to consider that people sometimes move locally in non-predictable ways. 
Global dynamics is ruled by three different mechanisms: movement to neighbor cells, long distance travelling, and seemingly random trips (noise). All three propagation methods depend on MonteCarlo Algorithms. 
A more detailed explanation could be found in the manuscript together with the model equations. 

### The code

The code was written in python with Jupyter using known libraries like numpy, pandas, and matplotlib. It is separated in three main cells that must be executed in order. The first one is used to import libraries, load maps and configure parameters. The second cell runs the main core of the simulation. keep in mind that this cell saves the results of the simulation in .csv and/or .mat files when it finishes (not after), so it could not be stopped during simulation. Moreover, the files will be saved in the same folder as the code. The third cell loads and plots the results. Use a computer connected to the Internet to download updated covid-19 information. 

Several parameters could be changed in the beggining of the code. For instance, three countries can be chosen: Argentina, Spain and mexico.
The simulation time interval T could be set to any integer value greater than 3 and the number "prom" sets the number of averages (should be set in 2 or more). Keep in mind that a large number of averages will take more time. A higher value of T also implies longer simulation times and larger matrices. For this reason, in order to run the code it is recommended to use a computer with 16GB RAM or more. Most simulations were done using 100 averages and a time interval of 1000 taking between 1 and 4 hours depending of the computer and the country. 

Other parameters that could be easily changed are delta and densfilt. The first one accounts for the vaccine immunity duration. The second one is related with the vaccination strategy: homogeneous distribution (densfilt=0) or vaccination only in high population density areas (densfilt=1).

Vaccine distribution was set using three kind of parameters: tvac* , the moment a vaccination stage starts, rat*, the vaccination rate in each stage and Ndosis* the number of doses in each stage. These numbers could be fitted to the actual vaccination rate of the country over time. 

All the other parameters in the model (with exception of mobility and noise) were fixed for all the countries. For instance, the epidemiological parametrs alpha, beta, omega and sigma are the same for all the countries during the whole simulation since they depend only on the virus. These parameters may change only if we consider a different virus variant. 

Some output files are provided as examples.

cite the code with:
[![DOI](https://zenodo.org/badge/438028998.svg)](https://zenodo.org/badge/latestdoi/438028998)








