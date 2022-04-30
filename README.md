# Input_data

This directory provides the input data used for the test system of the research project on the multi-stage charging station and distributed generation capacity planning with coupled power and transportation systems.

IEEE 33-node test system is used as the power distribution test system, and origin-destination (OD) travel demand from the 2020 Central Florida Regional Planning Model (CFRPM) is used as the transportation network input.


![GitHub Logo](/Images/test_systems.png)


The excel file in the directory includes all the input parameters of the project with different sheets for different parameters.
The system pu is based on $S^\mathrm{base} = 100$ MVA, and the discount factor is assumed to be $\alpha$ = 90\%.

## Sheets names and descriptions

* DG parameters:
	This sheet includes all the parameters relating to DGs on each column. The cost functions defined of DGs are assumed to be linear, and the upgrade costs of DGs are proportional to their average construction cost from [1]. The cost coefficients for different DG nodes are calculated following the procedure presented in [2].
 	i. Nodes: Distribution nodes with DGs.
	ii. up_cost: Cost of upgrading the DG capacity in \$/pu.
	iii. maint_cost: Maintenance cost of the DG in \$/pu.
	iv. gen_cost: Hourly generation cost coefficient in \$/pu.h.
	v. min_p: Minimum active power generation of DG in pu.
	vi. init_s: Initial total capacity of DGs in pu.
	vii. budget: Yearly capacity upgrade budget for each DG in \$/pu.
	
* Load:
In the distribution test system, nodes 8, 13, and 30 are the generation nodes, and the feeder is connected to the main grid at node 1. The cost functions defined of DGs are assumed to be linear, and the upgrade costs of DGs are proportional to their average construction cost from [1]. The cost coefficients for different DG nodes are calculated following the procedure presented in [2]. The system pu is based on $S^\mathrm{base} = 100$ MVA, and the discount factor is assumed to be $\alpha$ = 90\%. 

To model the base power demand (i.e., loads excluding the EV charging demand), we use the demand data from PJM Interconnection [3]. Hourly historical load forecast data was collected for a representative date (March 31) from 2012 (initial year $y=0$) to 2021 (final year $y=9$), specifically for the American Electric Power (AEP) area. To project this load demand on the DS test system, we first normalized the data such that the maximum load demand of the first year would be equal to the maximum total load demand of the 33-node test system (337.9 MW). Then, we converted them to the pu format with $S^\mathrm{base} = 100$. The load demand was distributed among all the nodes of the area studied, where each node was allocated a fraction of the load demand based on the assumptions made on the user types, i.e., commercial, industrial, and household users, as shown in Appendix Table \ref{T:syst_params}. This load demand is used in addition to the CS energy requirements to model the total power demand in the DS.

To model the traffic distribution in Orlando metropolitan area, origin-destination (OD) travel demand from the 2020 Central Florida Regional Planning Model (CFRPM) was used. This data includes daily traffic counts between origin and destination (OD) TAZs in Orange County, Florida in April 2015. In order to match the IEEE 33-node distribution system, 33 TAZs with the most trips were used for modeling the transportation system, with 35 $\%$ of these vehicles are assumed to be EVs. The travel demand from CFRPM generated from the origin nodes is treated as the initial EV travel demand ($\bar{\mathcal{Q}}^\mathrm{Init}$). For the years after, a base growth factor ($\omega^y$), which is estimated from global outlooks on EV growth from the International Energy Agency \cite{outlook2020electric} (see { Appendix, Table \ref{T:syst_params}}), was applied to simulate EV growth.