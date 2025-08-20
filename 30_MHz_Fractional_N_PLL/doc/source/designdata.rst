Design Data and Design Process Description
##########################################

The design is primarily implements a charge-pump (CP) based **Type-II Phase-Locked Loop (PLL)** designed to generate programmable output frequencies from a stable ``10 MHz`` reference input. The architecture uses a Voltage-Controlled Oscillator (VCO) together with two 3-bit programmable Frequency Dividers (FDs) to achieve a tunable output frequency.

Architecture
------------

- **Feedback Divider (M):**  
  Divides the VCO output by a 3-bit integer input ``M``. This allows the PLL to lock the VCO frequency at an integer multiple of the reference input:  
  :math:`f_{vco} = M \times f_{ref}`

- **Output Divider (N):**  
  Divides the VCO output by a 3-bit integer input ``N`` to produce the final output:  
  :math:`f_{out} = \dfrac{f_{vco}}{N}`

Frequency Relationship
----------------------

By configuring **M** and **N** via six digital I/O control pads (3 bits each), the system achieves a fractional multiplication of the reference input:

:math:`f_{out} = \left(\dfrac{M}{N}\right) \times f_{ref}`

Since both ``M`` and ``N`` can be varied between ``1`` and ``7``, the **theoretical frequency range** spans from ``1.428 MHz`` to ``70 MHz``, based on the 3-bit divider limits. However, due to VCO constraints, the **practical output frequency range** is limited to approximately ``1.428 MHz`` to ``30 MHz``. This design demonstrates a compact, digitally controlled fractional frequency synthesizer suitable for clock generation and frequency scaling applications.

Circuit Design
##############

Phase-Locked Loop (PLL)
-----------------------

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Phase-Frequency Detector (PFD)
------------------------------

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Charge Pump (CP)
----------------

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Loop Filter
-----------

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Bias Generator
--------------

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Voltage-Controlled Oscillator (VCO)
-----------------------------------

Inverter for VCO
~~~~~~~~~~~~~~~

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

11-Stage Ring VCO
~~~~~~~~~~~~~~~~~

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Frequency Divider (FD)
----------------------

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Frequency Divider Cell
~~~~~~~~~~~~~~~~~~~~~~

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Half Adder for Divider
~~~~~~~~~~~~~~~~~~~~~~

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

DFF with Inverterd CLK for Divider
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: _static/.PNG
    :align: center
    :alt: IHP Logo Image.
    :width: 800

Simulation Results (Pre-Layout)
###############################

Output Waveform of the VCO
--------------------------

VCO Output Waveform at Control Voltage = 1V
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

VCO Output Frequency Spectrum at Control Voltage = 1V
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

VCO Oscillation Frequency vs Control Voltage
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Operation of the Charge Pump
----------------------------

Frequency Divider Output Waveform for a Divider Ratio = 7
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Layout Design
#############

Charge Pump Layout
------------------

Loop Filter Layout
------------------

Bias Generator Layout
---------------------

VCO Layout
----------

Frequency Divider Layout
------------------------

Integrated PLL Layout (without fillers)
---------------------------------------

Integrated PLL Layout (with fillers)
------------------------------------

PLL Pinout
----------

Layout Information
------------------

Physical Verification (DRC, LVS)
################################

Design Rule Check (DRC) Results
-------------------------------

Layout vs. Schematics (LVS) Results
-----------------------------------

Post-layout Verification after PEX
##################################

Simulation a division ratio of 1 (M = 1 and N = 1)
--------------------------------------------------

Simulation a division ratio of 1/7 (M = 1 and N = 7)
----------------------------------------------------

Simulation a division ratio of 3 (M = 3 and N = 1)
--------------------------------------------------