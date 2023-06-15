<section>

## Data analysis tooling geared toward gridded data

* The scientific Python stack (NumPy, Xarray, etc.) was designed for
  gridded (Eulerian) data analysis.

<img src="assets/xarray-datastructure.png" width="100%"></img>

Image credit: <a href="https://xarray.dev">xarray.dev</a>
</section>


<section>

## Lagrangian data are not gridded

* In contrast to gridded data, Lagrangian data records vary in length
* For example, deployment times and life spans vary between drifters

$\rightarrow$ Lagrangian data are best represented as ragged arrays

TODO: diagram showing the "raggedness" of a Lagrangian dataset
</section>


<section>

## Common Lagrangian analysis tasks

* Casting to an Eulerian reference frame, i.e. geographical binning or temporal binning
* Slicing the trajectories based on time, space, or other criteria
* Computing per-trajectory statistics and higher-order quantities (velocity, divergence, vorticity, etc.)
</section>