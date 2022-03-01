# **High Speed 16T Full Adder Design using 28nm CMOS Technology**
Design and Simulation of a full adder using transmission gate logic, in 28nm technology using 15 transistors.

## **Abstract**
This design has an objective to implement a full adder using transmission gate logic, in 28nm technology. Contrary to the conventional adder designs, this design has XOR/XNOR nodes which improve the circuit to operate with lesser delay. The model provides full swing even at smaller operating voltages by minimizing threshold loss observed in circuits with low supply voltages, specifically when the feature size is 28nm or less. By implementing Transmission Gate Logic, the circuit results in reduced leakage power. The circuit is simulated using Synopsys Custom Compiler tool for synthesis. 

## **Reference Circuit Details**
With ever-increasing computing needs and their high-speed requirements, demanding low power consumption, it becomes crucial to not only make more functional circuits but to optimize them. A key circuit in realizing arithmetic functions and address generation, is the Full Adder circuit. A common 1-bit full adder has three inputs – two binary digits and a carry-in digit, which produce two outputs - sum and carry-out. At a primary level, the full adder logic is implemented using XOR, AND and OR gates. However,their extensive use in digital logic makes low-power, high speed adder cell designs a vast area of study. Improvements are introduced at every level to enhance the performance of the cell. The proposed design, aims to reduce delay during high speed and low power operation using 28nm technology. The design implements transmission gate structure of MOSFETs resulting in lower leakage power.
The circuit utilizes 16 transistors to realize the full adder. It mainly can be divided into three modules – an 8-transistor complementary XOR/XNOR generator, a 4-transistor transmission gate-based Multiplexer to generate the sum and a pass transistor logic implementation of the carry output. The logic expressions for the adder cell outputs are as follows: 

𝑆𝑢𝑚 = (𝐴⨁𝐵)⨁𝐶𝑖𝑛

𝐶𝑜𝑢𝑡 = (𝐴⨁𝐵) ⋅ 𝐶𝑖𝑛 + (𝐴 ⊙ 𝐵) ⋅ 𝐶𝑖𝑛

The most important part of the circuit is the XOR/XNOR generator module, which performs the XOR and XNOR logic operations on the inputs A and B. Subsequently, the generated complementary outputs are applied to the sum and carry output modules. To enhance the working of the module, a pair of PMOS transistors have been connected in series between the XNOR and supply nodes which reduce the delay and drive a stronger output. By adjusting the aspect ratios of the transistors in the sum module, it can be used to provide minimum gate delay even at a low supply. The carry output module takes both the outputs of the first module and while it can be implemented with two transistors, using an additional pair of complementary transistors allows for a full level swing at the output. To minimize the channel length, the width can be adjusted to operate in 28nm technology.

## **Reference Circuit**
![image](https://user-images.githubusercontent.com/100704799/156207134-71fcd216-4bfe-4885-ac4b-fcab9ed05245.png)

## **Reference Waveform**
![image](https://user-images.githubusercontent.com/100704799/156207407-3d3b3545-d5c9-47de-85fc-64ff2720aefd.png)

## **Tools Used for Simulation**
**Synopsys Custom Compiler**

The Synopsys Custom Compiler design environment is an industry standard solution for full-custom analog, custom digital, and mixed-signal IC design. Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. 

For the purposes of implementing this design at a transistor-level, Synopsys 28nm PDK(Process Design Kit) available on the platform was used. The circuit was simulated and analysed using Synopsys PrimeWave.

## **Design using Synopsys Custom Compiler**
### Full Adder Design
![image](https://user-images.githubusercontent.com/100704799/156209106-641b56a7-081f-4656-a3df-d1b503a67c92.png)
### Full Adder Block Schematic
![image](https://user-images.githubusercontent.com/100704799/156208489-fe0be61b-2031-4575-8b3b-65d224a3744d.png)
### Transmission Gate Block - sm_tg1 Schematic
![image](https://user-images.githubusercontent.com/100704799/156209337-af9771ed-5e4e-47e2-9560-0f8ddc3306bc.png)
### Transmission Gate Block - sm_tg2 Schematic
![image](https://user-images.githubusercontent.com/100704799/156209548-419bfb29-8998-49f3-91ba-c89dd2def475.png)

## **Simulation Output** 
### **Waveform**
![image](https://user-images.githubusercontent.com/100704799/156210265-debb48fc-982f-45f6-b383-2f8c40684af5.png)

### **Netlist**
```*  Generated for: PrimeSim
*  Design library name: FullAdder_15T
*  Design cell name: sm_fulladder_tb
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Tue Mar  1 16:37:34 2022

.global gnd! vdd!
********************************************************************************
* Library          : FullAdder_15T
* Cell             : sm_tg1
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt sm_tg1 nmos_gt pmos_gt tg_in tg_out vt_bulk_n_gnd! vt_bulk_p_vdd!
xm0 tg_in nmos_gt tg_out vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm1 tg_in pmos_gt tg_out vt_bulk_p_vdd! p105 w=0.274u l=0.03u nf=1 m=1
.ends sm_tg1

********************************************************************************
* Library          : FullAdder_15T
* Cell             : sm_tg2
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt sm_tg2 nmos_tg2 pmos_tg2 tg2_in tg2_out vt_bulk_n_gnd! vt_bulk_p_vdd!
xm0 tg2_out pmos_tg2 tg2_in vt_bulk_p_vdd! p105 w=0.247u l=0.03u nf=1 m=1
xm1 tg2_out nmos_tg2 tg2_in vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
.ends sm_tg2

********************************************************************************
* Library          : FullAdder_15T
* Cell             : sm_fulladder
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt sm_fulladder a b cin cout gnd_1 sum vcc vt_bulk_n_gnd! vt_bulk_p_vdd!
xm13 net80 cin sum vt_bulk_p_vdd! p105 w=0.29u l=0.03u nf=1 m=1
xm7 net43 net80 vcc vt_bulk_p_vdd! p105 w=0.137u l=0.03u nf=1 m=1
xm5 net43 b net16 vt_bulk_p_vdd! p105 w=0.125u l=0.03u nf=1 m=1
xm4 net16 a vcc vt_bulk_p_vdd! p105 w=0.15u l=0.03u nf=1 m=1
xm1 b a net80 vt_bulk_p_vdd! p105 w=0.274u l=0.03u nf=1 m=1
xm0 net80 b a vt_bulk_p_vdd! p105 w=0.274u l=0.03u nf=1 m=1
xm12 net43 cin sum vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm8 net80 net43 gnd_1 vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm3 b a net43 vt_bulk_n_gnd! n105 w=0.12u l=0.03u nf=1 m=1
xm2 net43 b a vt_bulk_n_gnd! n105 w=0.12u l=0.03u nf=1 m=1
xi20 net80 net43 cin cout vt_bulk_n_gnd! vt_bulk_p_vdd! sm_tg1
xi14 net43 net80 cin sum vt_bulk_n_gnd! vt_bulk_p_vdd! sm_tg1
xi18 net43 net80 a cout vt_bulk_n_gnd! vt_bulk_p_vdd! sm_tg2
.ends sm_fulladder

********************************************************************************
* Library          : FullAdder_15T
* Cell             : sm_fulladder_tb
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi0 a b cin cout gnd! sum net3 gnd! vdd! sm_fulladder
v10 net3 gnd! dc=1.8
c7 cout gnd! c=1p
c6 sum gnd! c=1p
v13 cin gnd! dc=0 pulse ( 0 1.05 0 0.1u 0.1u 20u 40u )
v12 b gnd! dc=0 pulse ( 0 1.05 0 0.1u 0.1u 10u 20u )
v11 a gnd! dc=0 pulse ( 0 1.05 0 0.1u 0.1u 5u 10u )








.tran '1u' '40u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(a) v(b) v(cin) v(cout) v(sum)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```
## **Author**
[Lakshmi Jayani Penumarthy](mailto:lakshmi.19bec7007@vitap.ac.in), VIT-AP University

## **Acknowledgement**
I would like to extend my gratitude to **Mr. Kunal Ghosh** - Founder, VLSI System Design Corporation Pvt. Ltd. and **Mr. Chinmaya Panda** - IIT Hyderabad, for their continued support and guidance throughout the duration of this Hackathon. Further, thanks to the **Synopsys Team** for giving me an opportunity to work with the industry-grade tools and avail them on the Cloud platform. This **Cloud-based Analog IC design hackathon** has been a remarkable experience, all due to the efforts of the organizing teams at **VSD and IIT Hyderabad** alike.   

## **References**
- D. K. Jena, R. K. Lal, R. Malik, A. Sen and J. K. Geda, "An improved low power high speed Full Adder design with 28nm for extended region of operation," _2014 International Conference on Electronics, Communication and Computational Engineering (ICECCE)_, 2014, pp. 137-141.
- C. K. Tung, S. H. Shieh, C. H. Cheng, “Low-power high speed full adder for portable electronic application,” _Electronics Letters, The Institution of Engineering and Technology_, Vol. 49, No. 17, August 2013.
