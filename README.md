Ongoing work to explore eddy dynamics using SWOT, PACE, and Argo.

Preliminary work. We are currently running this workflow on Cryocloud (NASA-supported): https://book.cryointhecloud.com/intro.html

We recommend that you do as well.

Current workflow:
- In each script, there may be data that needs to be manually downloaded and saved in the appropriate corresponding data folder. Each script will have directions on the top about ancillary datasets needed, or parameters to change in the script.

**Satellite visualizations**
1. *SWOT_velocities_maps*: Plot SWOT data, calculate geostrophic velocities, and compare to coarse geostrophic velocities from OSCAR and sea level anomaly from CMEMS.
2. *run_moana_cryocloud*: Process one image in SeaDAS to get phytoplankton assemblages (prochlorococcus, picoeukaryotes, synechococcus) from PACE Level 1B imagery using the MOANA algorithm (https://www.earthdata.nasa.gov/apt/documents/moana/v1.0). Please see important note below.
3. *SWOT_over_PACE_maps*: Plot PACE chl-a and phytoplankton assemblages (generated from run_moana_cryocloud or on local machine) with SWOT streamlines overlain.
4. *vort_strain_jpdfs*: Plot PACE chl-a and phytoplankton assemblage ratios in vorticity-strain space. Please interpret with care... SWOT velocities are preliminary, vorticity and strain are two levels of separation away from SLA...

**Times series**

[in progress]

**Argo**

[in progress]

*** Note on run_moana_cryocloud:
To process in batch, you must define a smaller lat/lon box of interest. Instead of 50 minutes, images will take about 1 minute or so. Currently, there is a bug (I think?) so that N/S/E/W bounds cannot be defined when running SeaDAS through CryoCloud. Not sure why. So, you must run SeaDAS on your local computer to get MOANA phyto assemblages. Please see my repo, run_moana_seadas, in order to set up moana on your local drive. If it is not on Github yet, please email slang@uri.edu and I can help you. -Slang
