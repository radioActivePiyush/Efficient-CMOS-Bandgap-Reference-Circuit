# Efficient-CMOS-Bandgap-Reference-Circuit

**ABSTRACT** -  This work presents efficient bandgap reference(BGR) design using self bias current mirror circuit. This design removes one complementary-to-absolutetemperature (CTAT) bipolar device in voltage reference branch , which reduced the chip area[1]. This design shares the bipolar device used to generate proportional-to-absolute-temperature (PTAT) voltage, thus reducing overall power consumption. Use of self bias current mirror instead of traditionally used operational amplifier also reduces the power requirement, complexity and area of circuit. Different techniques like cascode current mirror [2] and symmetrically matched current mirrors[3] can be used to improve output. Design and simulation of the circuit will be in 28nm CMOS process , for a temperature range of -40°C to 125°C.

# Table of Contents
 * [Introduction](#Introduction)
 * [Proposed Bandgap Reference](#Proposed Bandgap Reference)
 
# Introduction:

In many applications as stable voltage reference is needed  which is independent of power supply and temperature  variations. BGRs are extensively employed as reference  circuits as they have weak dependence on process,  temperature and voltage variations. There are mainly two  types of BGR curcuits:
 1. *Using operational amplifier (opamp)*
Use of op-amps have some  disadvantages over current mirrors like 
(a) op—amps require  more power which can be constraint in low power applications. 
(b) require more number of transistors which makes it area inefficient. 
2. *Using current mirror.* 
Current mirror based BGRs lacks in  terms of power supply rejection (PSR) as compared to opamp based design but it is simpler to design, requires less power and area with only marginal decrease in performance which makes it an attractive choice for modern applications. 
The PSR of simple current mirror (CM) based BGR can be improved by using cascoded current mirror (CCM) [2] or symetrically matched current mirror (SMCM) [3]

# Proposed Bandgap Reference :
Figure 1(b) shows the core part of the proposed BGR circuit [1] in comparison with traditional circuit 1(a). From the figure it  is clear that proposed circuit uses one bipolar device less in reference branch. The BJT Q2 is used for generation of PTAT voltage across the resistor R1 and voltage across it adds to  VREF. This modification reduces the total current and power consumption of the circuit is reduced by 33% and area required is also reduced.
 |![Fig. 1: Conventional current mirror](images/pic2.PNG "Fig. 1: Conventional current mirror ")| ![Fig. 2: Conventional current mirror](images/pic1.PNG "Fig. 2: Conventional current mirror")|
|--|--|
| Fig. 1: Conventional current mirror  | Fig. 2: Conventional current mirror |

<br />
Calculations of R1 and R2 can be done by the formulas given  
below

    R1= Vt ln(4) / I1
    where,	
		Vt = thermal voltage of the semiconductor and its value at room temperature is approximately 25.8 mV
		I1 = bias current of the Q1, Q2 transistors, here i have taken it to be 3uA.

VR2 is the PTAT voltage across the resistor R2 and is given  by the equation below for the proposed architecture

    VR2 = (R2/2R1) . VT . ln(4)

For zero temparature cofficient of the circuit derivative of VREF with respect to temperature must be zero

    enter code here
  
The power-supply rejection (PSR) performance does not change significantly from the traditional selfbiased BGR. The PSR can be improved by using 
(a) cascode current mirrors [2] or <br /> 
(b) symmetric biasing of both the branches [3] as shown in the figure below. <br />
![Fig. 3: Conventional current mirror](images/pic3.PNG "Fig. 3: symmetric biasing current mirror ") <br />
Design and comparison of both of the above improvement methods is also done here.

# Tools Used:

*• Synopsys Custom Compiler:*
&emsp;The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

*• Synopsys Primewave:*
&emsp;PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

*• Synopsys 28nm PDK:*
&emsp;The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.

# Circuit Implementation and Simulations 
*Few considerations for common to all schematic designs below*
* For all designs PTAT currents **Ix** (labeled in schematics and figures above) were designed to be around **3u A**.
* all mosfets use are of minimum dimensions. Although for real implementation dimensions can be increased to improve matching keeping W/L ratios same. 
*  PNP BJT bipolar devices are used for generation of PTAT currents.
* Ration of parallel BJTs for CTAT current generation is 4:1 for all designs.
* Vcc (supply voltage) = 3.3v 
* Temperature variation form -40 C to 125 C ,  Supply variation from 0v to 5v

#### • Case 1: Conventional BGR
<center>
<table>
<thead>
  <tr>
    <th><img src="images/case1_sch.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 1: Case 1 schematic</td>
  </tr>
</tbody>
</table>
</center>

<center>
<table>
<thead>
  <tr>
    <th><img src="images/case1_temp_var.PNG"></br></th>
    <th><img src="images/case1_supply_var.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 5: Temperature Variation</td>
    <td>Fig. 6: Supply Variation</td>
  </tr>
</tbody>
</table>
</center>

#### • Case 2: Propposed BGR
<center>
<table>
<thead>
  <tr>
    <th><img src="images/case2_sch.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 7: Case 2 schematic</td>
  </tr>
</tbody>
</table>
</center>

<center>
<table>
<thead>
  <tr>
    <th><img src="images/case2_temp_var.PNG"></br></th>
    <th><img src="images/case2_supply_var.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 9: Temperature Variation</td>
    <td>Fig. 10: Supply Variation</td>
  </tr>
</tbody>
</table>
</center>

#### • Case 3: Propposed BGR with cascoded current mirror 
<center>
<table>
<thead>
  <tr>
    <th><img src="images/case3_sch.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 11: Case 3 schematic</td>
  </tr>
</tbody>
</table>
</center>

<center>
<table>
<thead>
  <tr>
    <th><img src="images/case3_temp_var.PNG"></br></th>
    <th><img src="images/case3_supply_var.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 12 : Temperature Variation</td>
    <td>Fig. 13 : Supply Variation</td>
  </tr>
</tbody>
</table>
</center>

#### • Case 4: Propposed BGR with symetrically biased cirrent mirror
<center>
<table>
<thead>
  <tr>
    <th><img src="images/case4_sch.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 14: Conventional BGR schematic</td>
  </tr>
</tbody>
</table>
</center>

<center>
<table>
<thead>
  <tr>
    <th><img src="images/case4_temp_var.PNG"></br></th>
    <th><img src="images/case4_supply_var.PNG"></br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Fig. 15: Temperature Variation</td>
    <td>Fig. 16: Supply Variation</td>
  </tr>
</tbody>
</table>
</center>
