# Sram Design of conventional 6T cell & comparing its cell stability with 8T cell
# Table Of Contents
- [Abstract](#Abstract)
- [Introduction](#Introduction)
- [6T Sram Design](#6T-Sram-Design)
    - [Modes Of Sram Operation](#Modes-Of-Sram-Operation)
    - [Sram Block Diagram](#Sram-Block-Diagram)
    - [Sram Blocks](#Sram-Blocks)
        - [6T 1bit cell Sram](#6T-1bit-cell-Sram)
        - [Sense Amplifier](#Sense-Amplifier)
        - [Word Line Driver](#Word-Line-Driver)
        - [Write Driver](#Write-Driver)
        - [Precharge Circuit](#Precharge-Circuit)
        - [D Flipflop](#D-Flipflop)
        - [Column Multiplexer](#Column-Multiplexer)
        - [Tristate Buffer](#Tristate-Buffer)
    - [Prelayout Simulations](#Prelayout-Simulations)
        - [DC read](#DC-read)
        - [DC write](#DC-write)
        - [Transient 6T Simulations with related blocks](#Transient-6T-Simulations-with-related-blocks)
        - [Threshold voltage characterisation VT vs TEMP](#Threshold-voltage-characterisation-VT-vs-TEMP)
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
## Abstract
With the increasing competencies in semiconductor industry stability has become a prime concern.So enhanced solution for improving the stability is using 8T SRAM.It provides a better read stability with greater read noise margin, eliminates data flipping due to noise source during a read access.
## Introduction
As SRAM is scaled, so maintaining a sufficient Noise Margin is difficult due to both increase in variability and shifting of device characteristics from design targets. This work will somehow make strong signal to noise ratio which will improve the performance rate ,focusing on improvement of data stability in SRAM  by modifying it to a 8T from 6T.
## 6T Sram Design
