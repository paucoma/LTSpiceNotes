====================
Two port parameters
====================

The **.net** Spice function can be used to calculate two port parameters such as Z, Y, H and S parameters.  Zin and Zout can also be calculated.

  1.  Create an input port V1 with a series resistance. 

    - The series resistance will typically be 50 Ω for S-parameters.  
    - This resistance will not influence the Z, Y, H parameters or Zin.  
    - It will influence the value of Zout. 
    - You can choose this value as 0 Ω for an ideal source.

  2.  Create an output port with a load resistance R1. 

    - The load resistance will typically be 50 Ω for S-parameters.
    - This resistance will not influence the Z, Y, H parameters or Zout. 
    - It will influence the value of Zin. 
    - You can choose this value very high if you don't have a load.

  3.  Use the function :code:`.net I (R1) V1` to be able to plot the two port parameters.
  4.  Run the simulation.  
  5.  Plot the parameters of interest by using PlotSettings/AddTrace (or **CTRL-A**) while in the Plot screen.

`source <http://courses.ee.sun.ac.za/HFTegniek_414/JB/notas/Two%20port%20parameters%20in%20LTSPICE.pdf>`_
