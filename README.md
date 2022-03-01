A 7T SRAM Cell using Supply Feedback Technique

Introduction

Semiconductor devices scaling has been going on for more than the last five decades. High demand in the electronic market for cheaper, enhanced performance, more functionalities portable devices has resulted in rampant scaling of semiconductor devices. In the novel 7T SRAM cell design the read and write operation have been performed separately using read and write port to enhance the data stability. Furthermore, the supply feedback transistor has been used between data storing node and cell power supply in order to increase the write ability of the SRAM cell.

Reference Circuit

![image](https://user-images.githubusercontent.com/54323691/156227343-3ee47609-293c-4dc3-bac9-d73f551e73af.png)

Reference Waveform

![image](https://user-images.githubusercontent.com/54323691/156227412-4fd4716b-75f1-4c05-8523-e2086d09b4cf.png)

The transient waveform during a write operation is presented in Figure. Assume the node Q and BL are initially set to logic ‘0’ and ‘1’ respectively. As shown in Figure, the data retained at storing node Q and Qb when WL is initially at 0 V. Then as WL progresses to Vdd, the data in node Q changing and reached the value of BL at 0.9 V cell supply voltage. When again WL falls down to 0 V then the data stored in node Q has been retained as shown in Figure.

Simulation

Each pMOS is has the W/L of 0.1u/0.03u and each nMOS has the W/L of 0.2u/0.03u.

Schematic Diagram

<img width="550" alt="image" src="https://user-images.githubusercontent.com/54323691/156225978-936ea40f-faa3-435a-9f6e-2f77206b7df1.png">

Cell View

<img width="416" alt="image" src="https://user-images.githubusercontent.com/54323691/156226081-31a94665-94d7-47d0-a240-6bab1918384e.png">

Waveform

<img width="898" alt="image" src="https://user-images.githubusercontent.com/54323691/156226149-b6582be2-1b0f-4023-a95b-6fc84bed1b70.png">

Parameters

<img width="203" alt="image" src="https://user-images.githubusercontent.com/54323691/156227749-5dde8625-5413-49b4-9d53-c4005ad4e3fe.png">

<img width="202" alt="image" src="https://user-images.githubusercontent.com/54323691/156227838-b9ee7d46-f646-4a4a-9548-cf75c4ba7c0d.png">

Net list
```
*  Generated for: PrimeSim
*  Design library name: sb_lib_7T
*  Design cell name: sb_7T_sram_tb_2
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Fri Feb 25 16:51:59 2022

.global gnd!
********************************************************************************
* Library          : sb_lib_7T
* Cell             : sb_7T_sram
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt sb_7t_sram bl blb gnd_1 q qb vdd wl
xm6 q wl bl gnd_1 n105 w=0.2u l=0.03u nf=1 m=1
xm5 blb qb gnd_1 gnd_1 n105 w=0.2u l=0.03u nf=1 m=1
xm1 q qb gnd_1 gnd_1 n105 w=0.2u l=0.03u nf=1 m=1
xm0 qb q gnd_1 gnd_1 n105 w=0.2u l=0.03u nf=1 m=1
xm4 net29 q vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm3 q qb net29 net29 p105 w=0.1u l=0.03u nf=1 m=1
xm2 qb q net29 net29 p105 w=0.1u l=0.03u nf=1 m=1
.ends sb_7t_sram

********************************************************************************
* Library          : sb_lib_7T
* Cell             : sb_7T_sram_tb_2
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi0 bl net15 gnd! q qb net9 wl sb_7t_sram
v1 net9 gnd! dc=0.9
v4 net15 gnd! dc=0 pulse ( 0.9 0 0 10p 10p 5n 10n )
v3 wl gnd! dc=0 pulse ( 0 0.9 2n 10p 10p 5n 10n )
v2 bl gnd! dc=0 pulse ( 0 0.9 0 10p 10p 5n 10n )








.tran '1n' '10n' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(q) v(qb) v(bl) v(wl)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```
References
[1] J. K. Mishra, P. Kumar Misra and M. Goswami, "A Low Power 7T SRAM cell using Supply Feedback Technique at 28nm CMOS Technology", 7th International Conference on Signal Processing and Integrated Networks (SPIN), 2020.
[2] Jitendra Kumar Mishra, Prasanna Kumar Misra, Manish Goswami, "Design of SRAM cell using Voltage Lowering and Stacking Techniques for Low Power Applications", Circuits and Systems (APCCAS) 2020 IEEE Asia Pacific Conference on, pp. 50-53, 2020.
[3] Sridhara, et al. "Microwatt embedded processor platform for medical system-on-chip applications." In VLSI Circuits (VLSIC), IEEE Symposium on, pp. 15-16. IEEE, 2010.

Acknowledgements
Kunal Ghosh, Co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd.
Chinmay Panada, IIT Hydrabad
Synopsis
