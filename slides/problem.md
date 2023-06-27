<section>

## Problem and Motivation
</section>


<section>

## Core libraries are geared toward gridded data

* Core Python numerical libraries used in geosciences (NumPy, Xarray, etc.)
  designed for Eulerian (i.e. gridded) data analysis

<img src="assets/xarray-datastructure.png" width="100%"></img>

Image credit: <a href="https://xarray.dev">xarray.dev</a>
</section>


<section>

## Lagrangian data are _not_ gridded

* Unlike Eulerian data, Lagrangian data
  * may vary in length for each contiguous segment
  * may not conform to a regular sampling interval
  * is intrinsically sparse
* For example, oceanographic drifters
  * are released at different times and have varying lifetimes
  * may be sampling data at different times and intervals

<p class="fragment">
  $\rightarrow$ Lagrangian data are intrinsically unstructured.
</p>
</section>


<section>

## We need to solve the User Experience (UX) problem of Lagrangian data analysis

* Earth scientists who use Python rely heavily on NumPy, Xarray, Pandas, and Matplotlib.
* They write a lot of low-level boilerplate code to process and analyze Lagrangian data.
* There is no convention for a Lagrangian data structure and format.

<p class="fragment">
  $\rightarrow$ <b>Our challenge</b>: Can we make the UX of Lagrangian data analysis
  on par with that of Xarray for gridded data?
</p>
</section>

<section>

## Can we make the UX of Lagrangian data analysis on par with that of Xarray for gridded data?

<ol>
<li class="fragment">Choose a suitable data structure that is compute-, access-, and storage-efficient.</li>
<li class="fragment">Provide convenience functions for lazy access to cloud-optimized data.</li>
<li class="fragment">Provide domain-specific, easy-to-use, high-level analysis functions that operate on this structure.</li>
<li class="fragment">Leverage the existing ecosystem (e.g. NumPy, Xarray, Pandas) whenever possible.</li>
</ol>
</section>

<section>

## Ragged arrays, illustrated

<img src="assets/ragged_array.png" width="100%"></img>
</section>

