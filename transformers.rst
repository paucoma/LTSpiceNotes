 Defining Transformers
=======================

----------
 Windings 
----------
 - defined by inductors

 Phase dot
-----------
 - right click on the inductor --> select show phase dot

 Turns Ratio
-------------
 - defined by the inductance ratio rather than turns ratio

e.g. 
  1:3 = N_1:N_2  -->  N_1^2 = L_1 , N_2^2 = L_2 --> N_1 = 1uH , N_2 = 9uH

-----------------
 Spice Directive
-----------------

`K L1 L2 <leakage>` , where <leakage> [0,1]

in the event of multiple windings, e.g. `K L1 L2 L3 1`
