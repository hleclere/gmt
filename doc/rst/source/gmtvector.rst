.. index:: ! gmtvector
.. include:: module_core_purpose.rst_

*********
gmtvector
*********

|gmtvector_purpose|

Synopsis
--------

.. include:: common_SYN_OPTs.rst_

**gmt vector** [ *table* ]
[ |-A|\ **m**\ [*conf*]\|\ *vector* ]
[ |-C|\ [**i**\|\ **o**] ]
[ |-E| ]
[ |-N| ]
[ |-S|\ *vector* ]
[ |-T|\ **a**\|\ **d**\|\ **D**\|\ **p**\ *azim*\|\ **r**\ [*arg*]\|\ **R**\|\ **s**\|\ **t**\ [*arg*]\|\ **x** ]
[ |SYN_OPT-V| ]
[ |SYN_OPT-b| ]
[ |SYN_OPT-d| ]
[ |SYN_OPT-e| ]
[ |SYN_OPT-f| ]
[ |SYN_OPT-g| ]
[ |SYN_OPT-h| ]
[ |SYN_OPT-i| ]
[ |SYN_OPT-j| ]
[ |SYN_OPT-o| ]
[ |SYN_OPT-q| ]
[ |SYN_OPT-s| ]
[ |SYN_OPT-:| ]
[ |SYN_OPT--| ]

|No-spaces|

Description
-----------

**vector** reads either (x, y), (x, y, z), (r, theta) or (lon, lat)
[or (lat,lon); see **-:**] coordinates from the first 2-3 columns on
standard input [or one or more tables]. If **-fg** is selected and only two items
are read (i.e., lon, lat) then these coordinates are converted to
Cartesian three-vectors on the unit sphere. Otherwise we expect (r,
theta) unless **-Ci** is in effect. If no file is found we expect a
single vector to be given as argument to **-A**; this argument will also
be interpreted as an x/y[/z], lon/lat, or r/theta vector. The input
vectors (or the one provided via **-A**) are denoted the prime
vector(s). Several standard vector operations (angle between vectors,
cross products, vector sums, and vector rotations) can be selected; most
require a single second vector, provided via **-S**. The output vectors
will be converted back to (lon, lat) or (r, theta) unless **-Co** is set
which requests (x, y[, z]) Cartesian coordinates.

Required Arguments
------------------

*table*
    One or more ASCII [or binary, see **-bi**]
    file containing lon,lat [lat,lon if **-:**] values in the first 2
    columns (if **-fg** is given) or (r, theta), or perhaps (x, y[, z])
    if **-Ci** is given). If no file is specified, **vector**, will
    read from standard input.

Optional Arguments
------------------

.. _-A:

**-A**\ **m**\ [*conf*]\|\ *vector*
    Specify a single, primary vector instead of reading data table(s); see
    *table* for possible vector formats. Alternatively, append **m**
    to read *table* and set the single, primary vector to be the mean
    resultant vector first. We also compute the confidence ellipse for
    the mean vector (azimuth of major axis, major axis, and minor axis;
    for geographic data the axes will be reported in km). You may
    optionally append the confidence level in percent [95]. These three
    parameters are reported in the final three output columns.

.. _-C:

**-C**\ [**i**\|\ **o**]
    Select Cartesian coordinates on input and output. Append **i** for
    input only or **o** for output only; otherwise both input and output
    will be assumed to be Cartesian [Default is polar r/theta for 2-D
    data and geographic lon/lat for 3-D].

.. _-E:

**-E**
    Convert input geographic coordinates from geodetic to geocentric and
    output geographic coordinates from geocentric to geodetic. Ignored
    unless **-fg** is in effect, and is bypassed if **-C** is selected.

.. _-N:

**-N**
    Normalize the resultant vectors prior to reporting the output [No
    normalization]. This only has an effect if **-Co** is selected.

.. _-S:

**-S**\ [*vector*]
    Specify a single, secondary vector in the same format as the first
    vector. Required by operations in **-T** that need two vectors
    (average, bisector, dot product, cross product, and sum).

.. _-T:

**-T**\ **a**\|\ **d**\|\ **D**\|\ **p**\ *azim*\|\ **s**\|\ **r**\ [*arg*]\|\ **R**\|\ **s**\|\ **t**\ [*arg*]\|\ **x**
    Specify the vector transformation of interest. Append **a** for
    average, **b** for the pole of the two points bisector, **d** for
    dot product (use **D** to get angle in degrees between the two
    vectors), **p**\ *azim* for the pole to the great circle specified by
    input vector and the circle's *azim* (no second vector used), **s** for vector sum,
    **r**\ *par* for vector rotation (here, *par* is a single
    angle for 2-D Cartesian data and *lon/lat/angle* for a 3-D rotation
    pole and angle), **R** will instead rotate the fixed secondary vector
    by the rotations implied by the input records, **t** to translate
    the input point by *distance* in the *azimuth* direction (append *azimuth*/*distance*\ [*unit*]
    for the same translation for all input points, or just append
    *unit* to read *azimuth* and *distance* (in specified *unit* [**e**])
    from the third and fourth data column in the file, and **x** for cross-product.
    If **-T** is not given then no transformation takes place; the
    output is determined by other options such as **-A**, **-C**,
    **-E**, and **-N**. **Note**: For **-Tt** and geographic coordinates we will
    perform a great circle calculation unless **-je** is selected.

.. |Add_-V| replace:: |Add_-V_links|
.. include:: explain_-V.rst_
    :start-after: **Syntax**
    :end-before: **Description**

.. |Add_-bi| replace:: [Default is 2 or 3 input columns].
.. include:: explain_-bi.rst_

.. |Add_-bo| replace:: [Default is same as input].
.. include:: explain_-bo.rst_

.. |Add_-d| unicode:: 0x20 .. just an invisible code
.. include:: explain_-d.rst_

.. |Add_-e| unicode:: 0x20 .. just an invisible code
.. include:: explain_-e.rst_

.. |Add_-f| unicode:: 0x20 .. just an invisible code
.. include:: explain_-f.rst_

.. |Add_-g| unicode:: 0x20 .. just an invisible code
.. include:: explain_-g.rst_

.. |Add_-h| unicode:: 0x20 .. just an invisible code
.. include:: explain_-h.rst_

.. include:: explain_-icols.rst_

.. include:: explain_distcalc.rst_

.. include:: explain_-ocols.rst_

.. include:: explain_-q.rst_

.. include:: explain_colon.rst_

.. include:: explain_help.rst_

.. include:: explain_precision.rst_

Examples
--------

.. include:: explain_example.rst_

To determine the mean location of all points in the remote geographic file @ship_15.txt
as well as the 95% confidence ellipse around that point, try::

    gmt vector @ship_15.txt -Am -fg

Suppose you have a file with lon, lat called points.txt. You want to
compute the spherical angle between each of these points and the
location 133/34. Try::

    gmt vector points.txt -S133/34 -TD -fg > angles.txt

To rotate the same points 35 degrees around a pole at 133/34, and output
Cartesian 3-D vectors, use::

    gmt vector points.txt -Tr133/34/35 -Co -fg > reconstructed.txt

To rotate the point 65/33 by all rotations given in file rots.txt, use::

    gmt vector rots.txt -TR -S64/33 -fg > reconstructed.txt

To compute the cross-product between the two Cartesian vectors 0.5/1/2
and 1/0/0.4, and normalizing the result, try::

    gmt vector -A0.5/1/2 -Tx -S1/0/0.4 -N -C > cross.txt

To rotate the 2-D vector, given in polar form as r = 2 and theta = 35,
by an angle of 120, try::

    gmt vector -A2/35 -Tr120 > rotated.txt

To find the mid-point along the great circle connecting the points 123/35 and -155/-30, use::

    gmt vector -A123/35 -S-155/-30 -Ta -fg > midpoint.txt

To find the mean location of the geographical points listed in
points.txt, with its 99% confidence ellipse, use::

    gmt vector points.txt -Am99 -fg > centroid.txt

To find the pole corresponding to the great circle that goes through
the point -30/60 at an azimuth of 105 degrees, use::

    gmt vector -A-30/60 -Tp105 -fg > pole.txt

To translate all locations in the geographic file points.txt
by 65 km to the NE on a spherical Earth, try::

    gmt vector points -Tt45/65k -fg > shifted.txt


To determine the point that is 23 nautical miles along a geodesic
with a bearing of 310 degrees from the origin at (8E, 50N), try::

    echo 8 50 | gmt vector -Tt310/23n -je

Rotations
---------

For more advanced 3-D rotations as used in plate tectonic
reconstructions, see the GMT "spotter" supplement.

See Also
--------

:doc:`gmt`, :doc:`project`, :doc:`mapproject`
