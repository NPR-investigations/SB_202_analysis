# SB_202_analysis
SB 202 is the bill passed by Georgia's legislature in 2021 that made major changes to how elections are run in the state. NPR parntered with WABE and Georgia Public Broadcasting to quantify how these changes affect different groups of voters.<br>

The first measure we focus on is drop boxes. First came into use in the 2020 general election, drop boxes was an important way to vote for Georgians and also has been the  subject of much controversy and conspiracy theories. SB 202 limited how many drop boxes each county can deploy as well as the hours they are available. This analysis focuses on geographical access - specifically, for all registered voters in 2022, how much time are they taking to travel to a drop box in 2022 versus 2020?<br>

Data Sources:<br>
- Addresses of drop boxes in 2020 general election, acquired through going through ballot transfer forms; address of drop boxes in 2021 primary election and 2022 primary election, shared by Georgia's Secretary of State;
- Georgia voter rolls, purchased from Georgia's Secretary of State

Analysis process<br>
- Cleaning and geocoding addresses of drop boxes - we used Geocod.io and ArcGIS geocoder (shoutout to ESRI's media program)
- Cleaning and geocoding addresses of voters - we used Census Batch Geocoder, and then Geocodio and ArcGIS to fill in the blanks. [Markdown note explaining the process here](https://github.com/NPR-investigations/SB_202_analysis/blob/main/geocoding_code_notes.md)
- [generate transit isochrones](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220607_SB_202_transit_isochrone_generation_using_TravelTime-Copy1.ipynb)
- [generate driving isochrones](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220607_driving_isochrone-Copy1.ipynb)
- [compiling transit and driving isochrones and solve for shortest travel time for each voter address](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220513_SB_202_demographic_location_data_assembly.ipynb)
- [stitching the above address-level data up with individual voter and voter characteristics](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220607_SB_202_all_variable_assembly-cleanup.ipynb)
- [generate voter_race_location](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220512_SB_202_voter_address_cleanup.ipynb)
- [analysis and fact check](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220603_SB_202_demographic_location_analysis-Copy1.ipynb)
