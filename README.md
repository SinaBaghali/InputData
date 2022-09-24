# Input_data

This directory provides the input data used for the test system of a research project on the multi-stage charging station and distributed generation capacity planning with coupled power and transportation systems.

IEEE 33-node test system is used as the power distribution test system, and origin-destination (OD) travel demand from the 2020 Central Florida Regional Planning Model (CFRPM) is used as the transportation network input.


![GitHub Logo](/Images/test_systems.png)


The excel file in the directory includes all the input parameters of the project with different sheets for different parameters.
The system pu is based on 100 MVA, and the discount factor is assumed to be 90\%.

## Sheets names and descriptions

* DG parameters:

	This sheet includes all the parameters relating to DGsn. The cost functions defined for distributed generators (DGs) are assumed to be linear, and the upgrade costs of DGs are proportional to their average construction cost from [1]. The cost coefficients for different DG nodes are calculated following the procedure presented in [2]. The description of each column in this sheet is as follows:

 	* Nodes: Distribution nodes with DGs.
	* up_cost: Cost of upgrading the DG capacity in \$/pu.
	* maint_cost: Maintenance cost of the DG in \$/pu.
	* gen_cost: Hourly generation cost coefficient in \$/pu.h.
	* min_p: Minimum active power generation of DG in pu.
	* init_s: Initial total capacity of DGs in pu.
	* budget: Yearly capacity upgrade budget for each DG in \$/pu.
	
* Load demand:

	This sheet provides the hourly historical load forecast (i.e., loads excluding the EV charging demand) collected from PJM Interconnection [3] for a representative date (March 31) from 2012 (initial year $y=0$) to 2021 (final year $y=9$), specifically for the American Electric Power (AEP) area. We first normalized the data such that the maximum load demand of the first year would be equal to the maximum total load demand of the 33-node test system (337.9 MW). Then, we converted them to the pu format. 

	The load demand for each year has been presented in two columns one in kW and one in pu format.


* Nodal load: 

	The load demand on the "Load demand" sheet is distributed among all the load nodes of the test sytem, where each node was allocated a fraction of the load demand based on the assumptions made on the user types, i.e., commercial, industrial, and household users.

	This sheet provides the ratio of the total load demand that has been assigned on each node.

* EV growth:

	This sheet provides the growth rate of EVs for each year extracted from [4].

* CS_cap:

	This sheet provides the initial charging capacity for each charging station node.

* Traffic:

	This sheet provides the initial EV traffic generated from each origin node which is considered to be 35 \% of the totall traffic of each origin node extracted from CFRPM data set. 

* TT:
	
	This sheet provides the calculated travel time between origin and destinatio (charging station) nodes in minutes based on the travel time analysis from CFRPM.


* Arrival_T:
	
	This sheet provides the cumulative distribution function (CDF) of the considered arrival time of EVs during the day extracted from the arrival time of the National House Hold Travel Survey Data [7].

## General considerations
 
According to [5], the average cost of installing a commercialized level 2 charger for a large scale CS is 3,840 \$ , with an average capacity of  12.75 kW for each charger. Accordingly, we set the upgrade cost for each CS to be 50.19 \$ /kW, and the maintenance cost coefficients are assumed to be 1 \% of the upgrade cost. Using the procedure introduced in [2] we calculated the projected CS upgrade costs in system pu, and the charging cost for EVs is considered to be 150 \$ /\pu.h based on the levelized cost of charging reported in [6]. The yearly upgarde budget for each charging station is considered to be 100 \$.

Trips of EVs are equally divided into three groups, representing low, medium, and high initial SOC, with initial SOC sampled from uniform distributions [0, 0.3], [0.3, 0.6], and [0.6, 0.9], respectively.  We focus on destination charging in this study, which is the dominant charging types now. To calculate arrival times at CSs, we leveraged the 2017 National Household Travel Survey [7] to develop an hourly distribution of trip end times. According to this distribution, each set of trips was assigned a time to arrive at the charging stations. After the arrival time was determined, the departure time was calculated with dwelling time uniformly sampled between four to six hours (random seed = 1).

All EVs are considered to have battery capacity of 100 kW (0.001 pu) and and the coefficients used for EVs' utility functions are $b_0$ = 0, $b_1$ = 0.06, and $b_2$ = 0.05.

## References

[1] EIA, “2019 annual electric generator report,” U.S. Energy Information Administration, Tech. Rep., 2019. \[Online\]. Available: [https://www.eia.gov/electricity/generatorcosts/](https://www.eia.gov/electricity/generatorcosts/)

[2] L. J. Vimmerstedt, C. R. Augustine, P. C. Beiter, W. J. Cole, D. J. Feldman, P. Kurup, E. J. Lantz, R. M. Margolis, T. J. Stehly, C. S. Turchi et al., “2018 annual technology baseline (atb),” National Renewable Energy Lab.(NREL), Golden, CO (United States), Tech. Rep., 2018.

[3] “PJM Market Data,” [https://dataminer2.pjm.com/list,2021](https://dataminer2.pjm.com/list).

[4] IEA, “Global EV outlook 2020, entering the decade of electric drive,” IEA: Paris, Tech. Rep., 2020. [Online].
Available: [https://www.iea.org/reports/global-ev-outlook-2020](https://www.iea.org/reports/global-ev-outlook-2020)

[5] C. Nelder and E. Rogers, “Reducing ev charging infrastructure costs,” Rocky Mountain Institute, Dec. 2019.

[6] B. Borlaug, S. Salisbury, M. Gerdes, and M. Muratori, “Levelized cost of charging electric vehicles in the united states,” Joule, vol. 4, no. 7, pp. 1470–1485, Jul. 2020.

[7] United States Department of Transportation, “National Household Travel Survey 2017,” [https://nhts.ornl.gov/, 2019](https://nhts.ornl.gov/).
