Notebooks with Pre-Defined Experiments

In Example_SpeedyLongClimate.ipynb the ocean albedo is set to 0.3 that helps to run a stable climate simulation up to 30 years. With realistic albedo the model warm tropical ocean too much.
Simulation with albedo with latitudinal dependency is unstable even with value much higher then the real one (0.06-0.1):
```julia
#Set up albedo component
#Create a ManualAlbedo object
manual = ManualAlbedo(spectral_grid)
#Create the composite albedo object
albedo = Albedo(manual, manual)
#1.Manual albedo for the ocean
#manual_ocean_albedo = ManualAlbedo(spectral_grid)
set!(albedo.ocean, (λ, φ) -> 0.3 + 0.04 * abs(φ)/90)
#2.Use existing climatology for land
land_clim_albedo = AlbedoClimatology(spectral_grid)
#3.Combine them
albedo = Albedo(manual, land_clim_albedo)
```

