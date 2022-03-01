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
[image](https://drive.google.com/file/d/1e907JlxxsMwxBq_byi6nVdxgxY9tS87c/view?usp=sharing)

## **Reference Waveform**

## **Tools Used for Simulation**
### **Synopsys Custom Compiler**
The Synopsys Custom Compiler design environment is an industry standard solution for full-custom analog, custom digital, and mixed-signal IC design. 
