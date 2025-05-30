Ongoing work to explore eddy dynamics using SWOT, PACE, and Argo.

Preliminary work. We are currently running this workflow on Cryocloud (NASA-supported): https://book.cryointhecloud.com/intro.html

We recommend that you do as well.

Current workflow:
- In each script, there may be data that needs to be manually downloaded and saved in the appropriate corresponding data folder. Each script will have directions on the top about ancillary datasets needed, or parameters to change in the script.

**Satellite visualizations and processing (get phytoplankton assemblages from PACE)**

*SWOT* 

1. *SWOT_velocities_maps*: Plot SWOT data, calculate geostrophic velocities, and compare to coarse geostrophic velocities from OSCAR and sea level anomaly from CMEMS.
2. *eddy_track_visualizations*: Plot time series of eddy amplitude and area from AVISO eddy trajectories. Plot eddy trajectory over its lifespan. Select some SWOT overpasses to plot at different points of the eddy's life.
3. *plot_all_SWOT_dates*: Plot all SWOT images (SLA + quick velocities overlain) for all dates of SWOT overpass over the eddy. Generate animation from pngs.
   
*PACE*

1. *run_moana_cryocloud*: Process one image in SeaDAS to get phytoplankton assemblages (prochlorococcus, picoeukaryotes, synechococcus) from PACE Level 1B imagery using the MOANA algorithm (https://www.earthdata.nasa.gov/apt/documents/moana/v1.0). Please see important note below.
2. *box_plots_PACE* Looking at distributions of variables chl-a, pico, pro, and syn inside vs. outside eddy. Caveat: 'Outside' eddy area needs to be further refined.
3. *plot_all_SWOT_dates*: Plot all PACE images (chl-a) for all dates of SWOT overpass over the eddy. Generate animation from pngs.
   
*SWOT and PACE*

1. *SWOT_over_PACE_maps*: Plot PACE chl-a and phytoplankton assemblages (generated from run_moana_cryocloud or on local machine) with SWOT streamlines overlain.
2. *compute_vorticity_strain*: Plot PACE chl-a and phytoplankton assemblage ratios in vorticity-strain space. Please interpret with care... SWOT velocities are preliminary, vorticity and strain are two levels of separation away from SLA...
3. *slices_through_eddy*: Take 1D slices through eddy of interest and plot data along those 'slices.' Plot phyto assemblages, SLA, chl-a, etc. 
   
**Times series**

1. *generate_PACE_time_series_data.ipynb*: Generate data of mean + standard deviations for PACE variables within the eddy. Generate data for time series plots, plotted in next script. Variables of interest include chl-a, POC, prochlorococcus, picoeukaryotes, and 
synechococcus changes within the eddy defined by AVISO contour bounds.
2. *plot_PACE_time_series.ipynb*: Plot time series. Means and error bars are standard deviations on time series plots. Data generated from code listed above.

**Argo**

1. *colocate_Argo_AVISO.py*: Co-locate Argo floats and Gulf Stream eddies. The script takes the locations of Argo floats and mesoscale eddy boundaries from AVISO (currently version nrt_3.2), and outputs a CSV of the floats within an eddy.

**Spatial Clustering**

1. *gulf_stream_satellite_clim.ipynb*: Process CHLA and SLA satellite data from 2000-2020, calculates monthly averages, crops to the Gulf Stream region, interpolates them to the same 1/4 degree grids, and saves the data as an xarray dataset.
2. *clustering_gulf_stream_clim.ipynb*: Using monthly avg chl, ADT (and temp) to get spatial clusters of the region with k-means.

<img width="776" alt="Screenshot 2025-04-18 at 1 17 34 PM" src="https://github.com/user-attachments/assets/a88cbb32-ea2c-4134-9d80-206ac7e31228" />

*Phytoplankton evolve over the course of this Gulf Stream eddy's life. The eddy is also associated with rich submesoscale structure, especially evident in the April 14th image which showcases submesoscale eddies peeling off the Gulf Stream ring.*

*** Note on run_moana_cryocloud:
To process in batch, you must define a smaller lat/lon box of interest. Instead of 50 minutes, images will take about 1 minute or so. Currently, there is a bug (I think?) so that N/S/E/W bounds cannot be defined when running SeaDAS through CryoCloud. Not sure why. So, you must run SeaDAS on your local computer to get MOANA phyto assemblages. Please see my repo, run_moana_seadas, in order to set up moana on your local drive. If it is not on Github yet, please email slang@uri.edu and I can help you. 
-Slang


<img width="779" alt="Screenshot 2025-04-18 at 1 24 24 PM" src="https://github.com/user-attachments/assets/8603d49d-6179-40f6-aae8-dc8fd81367de" />

*May 8, 2024 PACE phytoplankton ratios (from MOANA algorithm) with SWOT geostrophic velocity contours overlain.*

