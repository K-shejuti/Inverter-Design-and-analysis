# Inverter-Design-and-analysis
CMOS Circuits generally consists of a network split into two parts, Upper one referred to as a **pull up network** and the lower half as a **pull down network**. The former consists of P-channel MOSFETs and later N-Channel MOSFETs. Reason is simple. As one transistor is on, another is off. This eliminates the issue of an resistive path to the ground and hence, no voltage division occurs(At least not a significant one). This way, one can easily achieve a Strong High and a Strong LOW from the same network. PULL UP is what offers a low resistance path to the VDD and PULL DOWN is what offers a low resistance path the GND.

## 1.CMOS inverter prelayout analysis
### 1.1 Voltage Transfer Characteristics
DC analysis would be used to plot a Voltage Transfer Characteristics (VTC) curve for the circuit. It will sweep the value of Vin from high to low to determine the working of circuit with respect to different voltage levels in the input. The following plot is observed when simulated 
![Screenshot from 2024-01-03 12-48-11](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/c8b1eaae-658a-4ec0-9266-b37eb04ce82b)
A voltage transfer characteristics paints a plot that shows the behavior of a device when it's input is changed(full swing). It shows what happens to the output as input changes. In our case, for an inverter we can see a plot that is like a square wave(non ideal), that changes it's nature around 0.83 volts of input. So one can say that there are like 3 regions in the VTC curve, the portion where output is high, the place of transistion and the one where the output goes low. But actually there are five regions of operation and they are based on the working of inverter constituents, that is the NMOS and the PMOS transistors with respect to the change in the input potential.



