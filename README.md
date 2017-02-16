DieBieMS - Hardware
===
# Introduction
My personal transportation environment is becoming more and more electrical. All vehicles so far contain Lithium based batteries and need some form of automated management to be utilized in a save and easy way. All affordable alternatives that I could find were either to dangerous(extreme cell voltage limits), couldn't carry the desired current (>70A), not compact enough or were not customizable. with this fully opensource project I would like to contribute to a more save and affordable Lithium based electric vehicle (or possible other usage) future.

![alt text](Binaries/Images/DieBieMSV0_4TOP.png "DieBieMS V0.4 TopView")

![alt text](Binaries/Images/DieBieMSV0_4BOTTOM.png "DieBieMS V0.4 BottomView")


### Latest hardware release (production files)
There have been two hardware realisations so far, not all design revisions make it to the real world. Sometimes a version is skipped when hardware errors are fixxed but also significant fuctionality is added:

* V0.1 Initial hardware
   This version has a few design flaws:
   * To small capacitor C7, this makes that the LOAD+ output sometimes fail to enable.
   * Components C37 and the 0R jumper resistor (removed in V0.3) are to close to U1 (LTC6803) making it difficult to assemble.
   * Pre-charge resistor R33 to low (will burn if load capacitance is to high)
   
* V0.3 Fixxed version of V0.1 with added functionality ( current version)
   This version has some added functionallity:
   * SDCard for logging (to develop a SoC and SoH algorithm)
   * An extra safety feature that disables the charge input and load output when the communication to the LTC6803 is halted.
   * A serial port connector for an external OpenLOG logger (if fast SDCard implementation is not as trivial as I thought).
   * An option to bypass the charge input diode allowing higher charge currents.
   * An option to add an extra shunt resistor to allow for higher measurable battery current.
   
* V0.4
   * Improved charge diode bypass current carrying capabillity (in devellopment)
   
Production data for most recent version can be found [here](Project%20Outputs%20for%20DB10005_DieBieMS). The initial project blog/log can be found [here](http://www.electric-skateboard.builders/t/diy-6s-to-12s-bms-with-can/2639).

### Features
This BMS is an all in one solution, combined with a lithium battery it is possible to replace an existing lead based battery pack (ideal for upgrading a bulky and heavy electric scooter with a much lighter li-polymer pack). In order to be a plug and play system the BMS carries all power electronics and controller systems to switch the main power path and communicate with external interfaces (displays, buttons or anything else you adapt to it). A small list of features:

* Soft power switch input with LED (LOAD) on/off + charge indicator.
* High side power switching to allow all grounds to remain connected at all times.
* Charge input -> switched (high side) -> to charger output (to disable charger if a cell reaches the max cell voltage).
* Charge input has optional input diode to eliminate current leakage or power on exposed pins (like the male charge connector).
* Discharge input -> switched (high side)-> to LOAD e.i. motor controller / VESC (to disable the load when a cell reaches the min voltage).
* Isolated CAN bus interface for cell voltage monitoring and charger detection, status monitoring + much more with future updates (like state of charge / state of health).
* Pack current sensing (bi-directional).
* Pre charge for high capacitive load (with shortcircuit detection, in case the motor controller is shorted / dead / wrong polarity).
* USB interface for serial communication and firmware upgrades (no need for a programmer -> HW serial bootloader is used).
* Buzzer to indicate possible Error state.
* Compact footprint

### Electrical specifications
* Max load current +/- 100A (both directions, theoratically it's 140A but this is still untested).
* Max charge current 10A (with diode) or 30A (with diode bypass).
* Cell voltage range 2.5V to 4.5V
* Pack voltage 12V to 54V

# Realisation
Of the many ways to realise an all in one BMS I choose the more simple but maybe more expensive way. Since there is a lot of desired functionallity and the need for a small footprint many features are realised by a complex chip. 

#### Power-on state management

#### Cell voltage measurement

#### Pack current / voltage measurement

#### Output voltage measurement

#### Main power patch switching

##### Output switching

##### Pre-charging

##### Charger switching

# Example usage
#### Electric skateboard
#### Electric scooter
