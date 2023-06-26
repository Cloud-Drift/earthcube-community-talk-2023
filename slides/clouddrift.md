<section>

## CloudDrift: A Python library for Lagrangian data analysis
</section>

<section>

## CloudDrift: A Python library for Lagrangian data analysis

* Accelerate the use of Lagrangian data in atmospheric, oceanic, and climate sciences by providing:
  1. Easy access to cloud-ready Lagrangian datasets
  2. Common Lagrangian analysis functions
  3. A framework to package custom Lagrangian data into a cloud-ready format
</section>

<section>

## Available from PyPI and Conda-Forge


pip:

```bash
$ pip install clouddrift
```

Conda:

```bash
$ conda install -c conda-forge clouddrift
```
</section>


<section>

## Easy access to cloud-ready Lagrangian data


```python
>>> from clouddrift.datasets import gdp1h
>>> ds = gdp1h()  # Lazy-loaded xarray.Dataset from a Zarr store on AWS
>>> ds
<xarray.Dataset>
Dimensions:                (traj: 17324, obs: 165754333)
Coordinates:
    ids                    (obs) int64 ...
    lat                    (obs) float32 ...
    lon                    (obs) float32 ...
    time                   (obs) datetime64[ns] ...
Dimensions without coordinates: traj, obs
Data variables: (12/55)
    BuoyTypeManufacturer   (traj) |S20 ...
    BuoyTypeSensorArray    (traj) |S20 ...
    CurrentProgram         (traj) float64 ...
    DeployingCountry       (traj) |S20 ...
    DeployingShip          (traj) |S20 ...
    DeploymentComments     (traj) |S20 ...
    ...                     ...
    sst1                   (obs) float64 ...
    sst2                   (obs) float64 ...
    typebuoy               (traj) |S10 ...
    typedeath              (traj) int8 ...
    ve                     (obs) float32 ...
    vn                     (obs) float32 ...
Attributes: (12/16)
    Conventions:       CF-1.6
    acknowledgement:   Elipot, Shane; Sykulski, Adam; Lumpkin, Rick; Centurio...
    contributor_name:  NOAA Global Drifter Program
    contributor_role:  Data Acquisition Center
    date_created:      2022-12-09T06:02:29.684949
    doi:               10.25921/x46c-3620
    ...                ...
    processing_level:  Level 2 QC by GDP drifter DAC
    publisher_email:   aoml.dftr@noaa.gov
    publisher_name:    GDP Drifter DAC
    publisher_url:     https://www.aoml.noaa.gov/phod/gdp
    summary:           Global Drifter Program hourly data
    title:             Global Drifter Program hourly drifting buoy collection
```

</section>


<section>

## Common Lagrangian analysis functions

* Computing per-trajectory statistics such as velocity, rotation, etc.
* Subsetting the data based on time, space, or other criteria
* Casting to an Eulerian reference frame, i.e. geographical binning or temporal binning
</section>


<section>

## Example: Obtaining ocean currents from drifter positions

* Velocity from position:
$
\mathbf{u} = \dfrac{d\mathbf{x}}{dt}
$

```python
from clouddrift.analysis import velocity_from_position
...
u, v = velocity_from_position(lon, lat)
```

<!--
TODO plots:

Left: trajectories spaghetti; Right: velocity map
-->

</section>


<section>

## Applying arbitrary functions to entire ragged arrays

* Some functions need to respect the trajectory boundaries.
* `apply_ragged()` takes an arbitrary function that works on contiguous arrays
  and applies it on all contiguous segments of a ragged array.
</section>


<section>

## Let's chunk a contiguous array into equal-sized chunks

<img src="assets/chunk.png" width="100%"></img>
</section>


<section>

## Now let's chunk an entire ragged array

<img src="assets/chunk_ragged.png" width="100%"></img>
</section>

<section>

## `apply_ragged()` can run arbitrary functions on ragged arrays

* Not only the analysis functions provided by CloudDrift any user-defined function
* `apply_ragged()` as a higher-order function thus provides a framework to extend
  CloudDrift to with arbitrary analysis functions.

</section>

<section>

## A CloudDrift analysis pipeline in action

* To learn how most of CloudDrift's functions come together
  in a comprehensive, oceanographic end-to-end analysis pipeline,
  please see Shane Elipot's live demo this afternoon.🤓
</section>
