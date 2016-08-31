=================
Defining Diodes
=================

Often you will find diodes which are not in the library and you search online for the model.

------------------------------
Include directly on the sheet
------------------------------
  - From the Edit menu or the toolbar icon select the |SpiceDirective|
  - write/copy the .model definition Spice Directive and place it on the sheet somewhere.
    + The .model must be a D(...) to be accepted by the diode sheet symbol
  - Cntrl + Right click on the Diode symbol on the sheet --> Change the name to your model name

----------------------------
Include as an external file
----------------------------
If the model is defined in a text file for example you can do the following
  - From the Edit menu or the toolbar icon select the |SpiceDirective|
  - write :code:`.include file.txt` in the directive
    + *file.txt* should reside in the same directory as the spice **.asc** file
  - Cntrl + Right click on the Diode symbol on the sheet --> Change the name to your model name

.. |SpiceDirective| image:: img/iconSpiceDirective.png


-----------------
Model definition
-----------------

D. Diode
 
Symbol Names: DIODE, ZENER, SCHOTTKY, VARACTOR.
 
Netlist Syntax: 

::

  Dnnn anode cathode <model> [area] 
  + [off] [m=<val>] [n=<val>] [temp=<value>]
 
Examples:

::
  
  D1 SW OUT MyIdealDiode
  .model MyIdealDiode D(Ron=.1 Roff=1Meg Vfwd=.4)


There are **two** types of diode models available:
  * a conduction region-wise linear model (idealized model)
  * the standard Berkeley SPICE semiconductor diode

The idealized model is used if any of the following is specified in the model:
  * Ron 
  * Roff 
  * Vfwd 
  * Vrev 
  * Rrev 

Idealized model parameters
---------------------------

+------------+-----------------------------------------------+-------+---------+
|  Name      |              Description                      | Units | Default |
+============+===============================================+=======+=========+
|  Ron       | Resistance in forward conduction              | Ohms  |    1.   |
+------------+-----------------------------------------------+-------+---------+
|   Roff     | Resistance when off                           | Ohms  | 1./Gmin |
+------------+-----------------------------------------------+-------+---------+
|   Vfwd     | Forward threshold voltage to enter conduction |  V    |    0.   |
+------------+-----------------------------------------------+-------+---------+
|  Vrev      |  Reverse breakdown voltage                    |  V    | Infin.  |
+------------+-----------------------------------------------+-------+---------+
|  Rrev      |  Breakdown impedance                          | Ohms  |   Ron   |
+------------+-----------------------------------------------+-------+---------+
| Ilimit     |  Forward current limit                        |  A    | Infinit |
+------------+-----------------------------------------------+-------+---------+
| Revilimit  |  Reverse current limit                        |  A    | Infinit |
+------------+-----------------------------------------------+-------+---------+
| Epsilon    |  Width of quadratic region                    |  V    |  0.     |
+------------+-----------------------------------------------+-------+---------+
| Revepsilon |  Width of reverse quadratic region            |  V    |  0.     |
+------------+-----------------------------------------------+-------+---------+


Berkeley model parameters
--------------------------

+------------+-----------------------------------------------+-------+---------+---------+
|  Name      |              Description                      | Units | Default | Example |
+============+===============================================+=======+=========+=========+
|   Is       |  Saturation current                           |   A   | 1e-14   |  1e-7   |
+------------+-----------------------------------------------+-------+---------+---------+
|   Rs       |  Ohmic resistance                             | Ohms  |  0.     |  10.    |
+------------+-----------------------------------------------+-------+---------+---------+
|   N        |  Emission coefficient                         |  -    |  1      |    1.   |
+------------+-----------------------------------------------+-------+---------+---------+
|   Tt       |  Transit-time                                 | sec   |   0.    |    2n   |
+------------+-----------------------------------------------+-------+---------+---------+
|   Cjo      |  Zero-bias junction capacitance               | Farrad|   0     |    2p   |
+------------+-----------------------------------------------+-------+---------+---------+
|    Vj      |  Junction potential                           |  V    |   1.    |    .6   |
+------------+-----------------------------------------------+-------+---------+---------+
|    M       | Grading coefficient                           |  -    |   0.5   |   0.5   |
+------------+-----------------------------------------------+-------+---------+---------+
|    Eg      | Activation energy (1.11 Si, 0.69 Sbd,0.67 Ge) |  eV   |  1.11   |  0.67   |
+------------+-----------------------------------------------+-------+---------+---------+
|    Xti     | Saturation-current temp. exp (3.0 jn, 2.0 Sbd)|   -   |   3.0   |  2.0    |
+------------+-----------------------------------------------+-------+---------+---------+
|    Kf      |   Flicker noise coefficient                   |   -   |    0    |         |
+------------+-----------------------------------------------+-------+---------+---------+
|    Af      |   Flicker noise exponent                      |   1   |    1    |         |
+------------+-----------------------------------------------+-------+---------+---------+
|    Fc      | Coeff. for fwd-bias depletion cap. formula    |   -   |   0.5   |         |
+------------+-----------------------------------------------+-------+---------+---------+
|    BV      | Reverse breakdown voltage                     |   V   |  Infin. |   40.   |
+------------+-----------------------------------------------+-------+---------+---------+
|    Ibv     | Current at breakdown voltage                  |   A   |  1e-10  |         |
+------------+-----------------------------------------------+-------+---------+---------+
|   Tnom     | Parameter measurement temp.                   |  ºC   |   27    |   50    |
+------------+-----------------------------------------------+-------+---------+---------+
|   Isr      | Recombination current parameter               |   A   |    0    |         |
+------------+-----------------------------------------------+-------+---------+---------+
|    Nr      |  Isr emission coefficient                     |  -    |    2    |         |
+------------+-----------------------------------------------+-------+---------+---------+
|   Ikf      |  High-injection knee current                  |   A   |  Infin. |         |
+------------+-----------------------------------------------+-------+---------+---------+
|   Tikf     |  Linear Ikf temp coeff.                       |  /ºC  |    0    |         |
+------------+-----------------------------------------------+-------+---------+---------+
|   Trs1     |  linear Rs temp coeff.                        |  /ºC  |    0    |         |
+------------+-----------------------------------------------+-------+---------+---------+
|   Trs2     |  Quadratic Rs temp coeff.                     | /ºC/ºC|    0    |         |
+------------+-----------------------------------------------+-------+---------+---------+

Dissipation ratings for a model
--------------------------------
These model parameters do not affect the electrical behavior. They allow LTspice to check if the diode is being used beyond its rated capability.

+------+-------------------------------------+-------+
| Name |      Description                    | Units |
+======+=====================================+=======+
|  Vpk |   Peak voltage rating               |  V    |
+------+-------------------------------------+-------+
|  Ipk |   Peak current rating               |  A    |
+------+-------------------------------------+-------+
| Iave |  Average current rating             |  A    |
+------+-------------------------------------+-------+
| Irms |  RMS current rating                 |  A    |
+------+-------------------------------------+-------+
| diss | Maximum power dissipation rating    |  W    |
+------+-------------------------------------+-------+

`Information source <http://ltwiki.org/LTspiceHelp/LTspiceHelp/D_Diode.htm>`_



