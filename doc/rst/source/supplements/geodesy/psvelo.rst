.. index:: ! psvelo
.. include:: ../module_supplements_purpose.rst_

******
psvelo
******

|psvelo_purpose|

Synopsis
--------

.. include:: ../../common_SYN_OPTs.rst_

**gmt psvelo**
[ *table* ]
|-J|\ *parameters*
|SYN_OPT-R|
|-S|\ *format*\ [*scale*][/*args*][**+f**\ *font*]
[ |-A|\ *parameters* ]
[ |SYN_OPT-B| ]
[ |-C|\ *cpt*]
[ |-D|\ *scale* ]
[ |-E|\ *fill* ]
[ |-G|\ *fill* ]
[ |-H|\ [*scale*] ]
[ |-I|\ [*intens*] ]
[ |-K| ]
[ |-L|\ [*pen*\ [**+c**\ [**f**\|\ **l**]]] ]
[ |-N| ] [ |-O| ] [ |-P| ]
[ |SYN_OPT-U| ]
[ |SYN_OPT-V| ]
[ |-W|\ [*pen*][**+c**\ [**f**\|\ **l**]] ]
[ |SYN_OPT-X| ]
[ |SYN_OPT-Y| ]
[ |-Z|\ [**m**\|\ **e**\|\ **n**\|\ **u**\ ][**+e**] ]
[ |SYN_OPT-di| ]
[ |SYN_OPT-e| ]
[ |SYN_OPT-h| ]
[ |SYN_OPT-i| ]
[ |SYN_OPT-p| ]
[ |SYN_OPT-qi| ]
[ |SYN_OPT-tv| ]
[ |SYN_OPT-:| ]
[ |SYN_OPT--| ]

.. include:: velo.rst
    :start-after: .. module_common_begins
    :end-before: .. module_common_ends

.. include:: ../../common_classic.rst_

Examples
--------

The following should make big red arrows with green ellipses, outlined
in red. Note that the 39% confidence scaling will give an ellipse which
fits inside a rectangle of dimension Esig by Nsig::

    gmt psvelo << END -R-10/10/-10/10 -W0.25p,red -Ggreen -L -Se0.2i/0.39+f18p \
        -B1g1 -Jx0.4/0.4 -A1c+p3p+e -P -V > test.ps
    #Long. Lat. Evel Nvel Esig Nsig CorEN SITE
    #(deg) (deg) (mm/yr) (mm/yr)
    0. -8. 0.0 0.0 4.0 6.0 0.500 4x6
    -8. 5. 3.0 3.0 0.0 0.0 0.500 3x3
    0. 0. 4.0 6.0 4.0 6.0 0.500
    -5. -5. 6.0 4.0 6.0 4.0 0.500 6x4
    5. 0. -6.0 4.0 6.0 4.0 -0.500 -6x4
    0. -5. 6.0 -4.0 6.0 4.0 -0.500 6x-4
    END

This example should plot some residual rates of rotation in the Western
Transverse Ranges, California. The wedges will be dark gray, with light
gray wedges to represent the 2-sigma uncertainties::

    gmt psvelo << END -Sw0.4i/1.e7 -W0.75p -Gdarkgray -Elightgray -D2 -Jm2.2i \
        -R240./243./32.5/34.75 -Baf -BWeSn -P > test.ps
    #lon lat spin(rad/yr) spin_sigma (rad/yr)
    241.4806 34.2073 5.65E-08 1.17E-08
    241.6024 34.4468 -4.85E-08 1.85E-08
    241.0952 34.4079 4.46E-09 3.07E-08
    241.2542 34.2581 1.28E-07 1.59E-08
    242.0593 34.0773 -6.62E-08 1.74E-08
    241.0553 34.5369 -2.38E-07 4.27E-08
    241.1993 33.1894 -2.99E-10 7.64E-09
    241.1084 34.2565 2.17E-08 3.53E-08
    END

`Kurt L. Feigl <http://www.geology.wisc.edu/~feigl/>`_, Department of Geology and
Geophysics at University of Wisconsin-Madison, Madison, Wisconsin, USA

See Also
--------

:doc:`gmt </gmt>`, :doc:`psbasemap </psbasemap>`, :doc:`psxy </psxy>`
