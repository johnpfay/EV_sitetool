```
Title: EV Site Tool
Author: John Fay
Date: Spring 2020
```

# EV Siting Tool

This tool presents a workflow for creating an optimized EV charging network across North Carolina. Optimization is based on the following factors: 

* Reducing "range anxiety" by creating a constellation of charging locations that enable electric cars maximal coverage across the state. 
* Favoring charging locations that offer amenities such as restaurants, cafes, entertainment.
* Minimizing costs by reducing redundant sites, minimizing up-front infrastructure needs, and avoiding hazards. 

---

<u>Objective</u>: Create a constellation of charging sites such that all sections of interstate are within `50 miles` of a charger. 

<u>Data needs</u>:

* Locations of operational DCFC chargers (NREL API)
* NC Highway network, as a graph (OSM)

<u>Workflow</u>: 

* Identify all currently "safe" areas: all areas within a 50 mile drive to existing DCFC charger
* Identify viable extension areas: areas within 50 miles of edge of "safe" areas
* Identify all candidate locations (exits) within these areas:
  * Minimum # of amenities
  * Minimum distance from power substations
  * Outside of flood risk areas
  * Minimum distance from existing infrastructure
* Weight considerations
* Select optimal site within expansion zone and add to network
* Repeat until all of NC is covered

---

#### Notebooks

* `Range-Anxiety-1-GetData`
  * Fetch NREL DCFC location data
  * Fetch OSM major roads network
* `Range-Anxiety-2-Analyze-Data`
  * Read in saved data (DCFC sites and road network)
  * Identify "safe" areas, i.e. areas within 50 miles of an existing charger, and "anxious" areas beyond 50 miles. 