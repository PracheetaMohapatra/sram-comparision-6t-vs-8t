# Sram Design of conventional 6T cell & comparing its cell stability with 8T cell
# Table Of Contents
- [Abstract](#Abstract)
- [Introduction](#Introduction)
- [6T Sram Design](#6T-Sram-Design)
    - [Technology](#Technology)
    - [System Specification](#System-Specification)
    - [Modes Of Sram Operation](#Modes-Of-Sram-Operation)
    - [Sram Block Diagram](#Sram-Block-Diagram)
    - [Sram Blocks](#Sram-Blocks)
        - [6T 1bit cell Sram](#6T-1bit-cell-Sram)
        - [Sense Amplifier](#Sense-Amplifier)
        - [Write Driver](#Write-Driver)
        - [Precharge Circuit](#Precharge-Circuit)
        - [D Flipflop](#D-Flipflop)
        - [Tristate Buffer](#Tristate-Buffer)
        - [Column Multiplexer](#Column-Multiplexer)
        - [Word Line Driver](#Word-Line-Driver)
    - [Prelayout Simulations](#Prelayout-Simulations)
        - [read SNM](#read-SNM)
        - [DC Simulation](#DC-Simulation)
        - [Transient 6T Simulations with related blocks](#Transient-6T-Simulations-with-related-blocks)
    - [Pvt Variation](#Pvt-Variation)
    - [Post layout 6T simulations](#Post-layout-simulations)
        - [6T cell](#6T-cell)
        - [Sense Amplifier](#Sense-Amplifier)
        - [Write Driver](#Write-Driver)
        - [D-Flipflop](#D-Flipflop)
        - [Tristate Buffer](#Tristate-Buffer)
        - [Precharge Circuit](#Precharge-Circuit)
    - [SNM 6T](#SNM-6T)
        - [Hold state](#Hold-state)
        - [Read snm](#Read-snm)   
- [Why 8T?](#Why-8T?)
    - [Read stability](#Read-stability)
    - [Read SNM 8T](#Read-SNM-8T)
    - [Comparison 6T vs 8T](#Comparison-6T-vs-8T)
    - [Prelayout 8T simulation](#Prelayout-8T-simulation)
    - [Postlayout 8T simulation](#Postlayout-8T-simulation)
    - [Future Works](#Future-Works)
    - [Acknowledgements](#Acknowledgements)
# Abstract
With the increasing competencies in semiconductor industry stability has become a prime concern.So enhanced solution for improving the stability is using 8T SRAM.It provides a better read stability with greater read noise margin, eliminates data flipping due to noise source during a read access.
# Introduction
As SRAM is scaled, so maintaining a sufficient Noise Margin is difficult due to both increase in variability and shifting of device characteristics from design targets. This work will somehow make strong signal to noise ratio which will improve the performance rate ,focusing on improvement of data stability in SRAM  by modifying it to a 8T from 6T.
# 6T Sram Design
This project is based on designing a 6t 1 bit _fast parasitic_ cell to work as a sram and its related blocks and compiling it using [OpenRAM] [OpenRAMpaper] compiler.
## Technology
**MOSIS** scalable CMOS ([SCMOS]) technology , a scalable 0.5 _u_ CMOS technology.
[SCMOS] is a *lambda-based* scalable design rules that can be interfaced to many CMOS fabrication process available at MOSIS.
## System Specification
### - Typical MOS parameters:
##### **NMOS**: tox=7.6nm , nch=1.7e17/cm^3, **vt0**=0.49v, _un_(mobility)=445 cm^2/Vs.
#### **PMOS**: tox=7.6nm , nch=1.7e17/cm^3, **vt0**=0.66v, _up_(mobility)=151 cm^2/Vs.
#### **VDD**=5V, **Lmin**=0.4 _um_, **Wmin**=0.6 _um_
# Mode of Operation of a typical 6T cell
## 6T cell CIRCUIT DIAGRAM

#### **HOLD STATE**
When the Word Line (WL) is at logic ‘0’, the access transistors M2 and M3 disconnect the cell from the Bit Lines and the previous state or data bits is stored.
#### **READ MODE**
###### (Memory : Q=1 ,QBar=0) , (WL :1) ,  (BL,BLBAR) acts as O/P LINES ,  (Precharge cap ON ) , (BLBAR _decreases_  , since QBar=0 potential difference occurs , current flows , cap discharges) 
###### (BL,BLBar sent to sense amplifier, gives _op as 1_) , (READ _SUCCESSFUL_)

#### **WRITE MODE**
###### (Memory : Q=0 ,QBar=1) , (WL :1) ,  (BL,BLBAR) acts as I/P LINES ,  (Precharge cap ON ) 
###### (forcing BLBAR =GND)  ,  (potential difference occurs , current flows)
###### (V < Vth of M5) ,  (M5 IS _OFF_) , (M0 _ON_) , (Q=1 WRITE _SUCCESSFUL_)


##  SRAM BLOCK DIAGRAM


## SRAM BLOCKS
### 6T 1bit cell Sram
Its a static memory of 4 transistors for storing data using node **Q** and **QBar** and 2 **_access transistors_** connected to **_word line_** to access the memory ( i.e during **read and write operation**).
### BLOCK DIAGRAM 6T CELL

### CIRCUIT DIAGRAM

### Sense Amplifier
Its a differential circuit amplifier used in read operation which acts as a comparator and senses the voltage difference between BL and BLBar.the sense amp is necessary to recover the signals from the bit lines because they do not experience full voltage swing as there is huge load capacitances of the **_bit cell array_**.
### BLOCK DIAGRAM

### CIRCUIT DIAGRAM
### Write Driver
The write driver is used to drive the input signal into the _bit-cell during a write operation_. It consists of two _tristate buﬀers_, one inverting and one non-inverting. It takes in a data bit, and outputs that value on to the bit-line, and its complement on the bit-line bar. Both tristates are enabled by the _**EN (enable)**_ signal. The bit-lines always need to be complements to ensure that the correct data is stored in the bit-cell. Also, the drivers need to be appropriately sized as the memory array grows and the bit-line capacitance increases.
### BLOCK DIAGRAM

### CIRCUIT DIAGRAM

### Precharge Circuit
It precharges the bit-lines during the first phase of the clock cycle before read and write operations.It has a third PMOS transistor which connects the two bit-lines together and equalizes the voltage between the two bit-lines.
### BLOCK DIAGRAM

### CIRCUIT DIAGRAM
### D-Flipflop
It is necessary to synchronize the inputs and outputs with a clock signal. In OpenRAM,a master-slave D-flipflop is used for the synchronizing process.
### BLOCK DIAGRAM


### CIRCUIT DIAGRAM

### Tristate Buffer
The TriState Buffer enables and puts the output data on data bus.
### BLOCK DIAGRAM


### CIRCUIT DIAGRAM

### Column Multiplexer

### Wordline Driver
They are used to drive the access transistors during read and write operations. 
## Prelayout simulations
Before doing the Layout,the prelayout simulatons checked.The read/write timing estimation in Spice is done using a fast-single-6T parasitic model. Fast-single-6T parasitic models considers and estimates the parasitics of the wordlines and bitlines in the bit cell array analysing the capacitance for only 1-Bit Cell.
###  read SNM curve

The **Signal to Noise Margin(SNM)** for SRAM Cell = **0.40**
It can be extracted by calculating the largest possible square in the two voltage transfer characteristic curves (VTC) of the involved CMOS inverters and get us to know how much noise the SRAM Cell can tolerate.
 ### Dc Simulation
 The DC Simulation does the write and read sanity check for the SRAM cell,observing the trip point and checking the iterative threshold voltages taken for the simulation.
 
 ### Transient 6-T simulations
 **Input signals**
 
 **Output signals**
 ## PVT Variation
 **for nmos**
 
 **for pmos**
 ## Post-Layout simulations
 ****6t 1-bit cell****
**Layout**

**simulation**


***
[OpenRAM]:      https://openram.soe.ucsc.edu/
[OpenRAMpaper]:  https://ieeexplore.ieee.org/document/7827670/
[SCMOS]:         https://www.mosis.com/files/scmos/scmos.pdf
