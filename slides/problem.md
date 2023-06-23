<section>

## Problem and Motivation
</section>


<section>

## Data analysis tooling geared toward gridded data

* The scientific Python stack (NumPy, Xarray, etc.) was designed for
  gridded (Eulerian) data analysis.

<img src="assets/xarray-datastructure.png" width="100%"></img>

Image credit: <a href="https://xarray.dev">xarray.dev</a>
</section>


<section>

## Lagrangian data are not gridded

* Unlike gridded data, Lagrangian data
  * may vary in length for each contiguous segment
  * may not conform to a regular sampling interval
  * is intrinsically sparse
* For example, oceanographic drifters
  * are released at different times and have varying lifetimes
  * may be sampling data at different times and intervals

<p class="fragment">
  $\rightarrow$ Lagrangian data are best represented as ragged arrays.
</p>
</section>


<section>

## Ragged arrays, illustrated

<img src="assets/ragged_array.png" width="100%"></img>
</section>


<section>

## Common Lagrangian analysis tasks

* Casting to an Eulerian reference frame, i.e. geographical binning or temporal binning
* Slicing the trajectories based on time, space, or other criteria
* Computing per-trajectory statistics and higher-order quantities (velocity, divergence, vorticity, etc.)
</section>