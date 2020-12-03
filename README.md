# Sram Design of conventional 6T cell & comparing it with 8T cell
# Table Of Contents
- [Introduction](#Introduction)
- [Abstract](#Abstract)
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
    - [Pvt Varriation](#Pvt-Variation)
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
Design of conventional 6T 1bit cell of Sram and its stability comparision with 8T 1bit cell Sram.
 

