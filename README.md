# Input_data

This directory provides the input data used for the test system of the research project on the multi-stage charging station and distributed generation capacity planning with coupled power and transportation systems.

IEEE 33-node test system is used as the power distribution test system, and origin-destination (OD) travel demand from the 2020 Central Florida Regional Planning Model (CFRPM) is used as the transportation network input.


![GitHub Logo](/Images/test_systems.png)


The excel file in the directory includes all the input parameters of the project with different sheets for different parameters.
The system pu is based on 100 MVA, and the discount factor is assumed to be &alpha = 90\%.

## Sheets names and descriptions

* DG parameters:

	This sheet includes all the parameters relating to DGs on each column. The cost functions defined of DGs are assumed to be linear, and the upgrade costs of DGs are proportional to their average construction cost from [1]. The cost coefficients for different DG nodes are calculated following the procedure presented in [2].

 	* Nodes: Distribution nodes with DGs.
	* up_cost: Cost of upgrading the DG capacity in \$/pu.
	* maint_cost: Maintenance cost of the DG in \$/pu.
	* gen_cost: Hourly generation cost coefficient in \$/pu.h.
	* min_p: Minimum active power generation of DG in pu.
	* init_s: Initial total capacity of DGs in pu.
	* budget: Yearly capacity upgrade budget for each DG in \$/pu.
	
* Load demand:

	This sheet provides the hourly historical load forecast (i.e., loads excluding the EV charging demand) collected from PJM Interconnection [3] for a representative date (March 31) from 2012 (initial year $y=0$) to 2021 (final year $y=9$), specifically for the American Electric Power (AEP) area. We first normalized the data such that the maximum load demand of the first year would be equal to the maximum total load demand of the 33-node test system (337.9 MW). Then, we converted them to the pu format. 

	The load demand for each year has been presented in two columns one in kW and pu format.


* Nodal load: 

	The load demand in the previous sheet was distributed among all the nodes of the area studied, where each node was allocated a fraction of the load demand based on the assumptions made on the user types, i.e., commercial, industrial, and household users.

	This sheet provides the ratio of the total load demand that has been assigned on each node.

* EV growth:

	This sheet provides the growth rate of EVs for each year extracted from [4].

* CS_cap:
	This sheet provides the initial charging capacity for each charging station node.



## General considerations
 
According to [5], the average cost of installing a commercialized level 2 charger for a large scale CS is 3,840 \$, with an average capacity of  12.75 kW for each charger. Accordingly, we set the upgrade cost for each CS to be 50.19 \$/kW, and the maintenance cost coefficients are assumed to be 1 $\%$ of the upgrade cost. Using the procedure introduced in [2] we calculated the projected CS upgrade costs in system pu, and the charging cost for EVs is considered to be 0.15 \$/kW based on the levelized cost of charging reported in [6].



[1] EIA, “2019 annual electric generator report,” U.S. Energy Information Administration, Tech. Rep., 2019. \[Online\]. Available: [https://www.eia.gov/electricity/generatorcosts/](https://www.eia.gov/electricity/generatorcosts/)

[2] L. J. Vimmerstedt, C. R. Augustine, P. C. Beiter, W. J. Cole, D. J. Feldman, P. Kurup, E. J. Lantz, R. M. Margolis, T. J. Stehly, C. S. Turchi et al., “2018 annual technology baseline (atb),” National Renewable Energy Lab.(NREL), Golden, CO (United States), Tech. Rep., 2018.

[3] “PJM Market Data,” [https://dataminer2.pjm.com/list, 2021](https://dataminer2.pjm.com/list, 2021).

[4] IEA, “Global EV outlook 2020, entering the decade of electric drive,” IEA: Paris, Tech. Rep., 2020. [Online].
Available: [https://www.iea.org/reports/global-ev-outlook-2020](https://www.iea.org/reports/global-ev-outlook-2020)

[5] C. Nelder and E. Rogers, “Reducing ev charging infrastructure costs,” Rocky Mountain Institute, Dec. 2019.

[6] B. Borlaug, S. Salisbury, M. Gerdes, and M. Muratori, “Levelized cost of charging electric vehicles in the united
states,” Joule, vol. 4, no. 7, pp. 1470–1485, Jul. 2020.