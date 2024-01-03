# Inverter-Design-and-analysis
CMOS Circuits generally consists of a network split into two parts, Upper one referred to as a **pull up network** and the lower half as a **pull down network**. The former consists of P-channel MOSFETs and later N-Channel MOSFETs. Reason is simple. As one transistor is on, another is off. This eliminates the issue of an resistive path to the ground and hence, no voltage division occurs(At least not a significant one). This way, one can easily achieve a Strong High and a Strong LOW from the same network. PULL UP is what offers a low resistance path to the VDD and PULL DOWN is what offers a low resistance path the GND.

## 1.CMOS inverter prelayout analysis
### 1.1 Voltage Transfer Characteristics
DC analysis would be used to plot a Voltage Transfer Characteristics (VTC) curve for the circuit. It will sweep the value of Vin from high to low to determine the working of circuit with respect to different voltage levels in the input. The following plot is observed when simulated 
![Screenshot from 2024-01-03 12-48-11](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/c8b1eaae-658a-4ec0-9266-b37eb04ce82b)

A voltage transfer characteristics paints a plot that shows the behavior of a device when it's input is changed(full swing). It shows what happens to the output as input changes. In our case, for an inverter we can see a plot that is like a square wave(non ideal), that changes it's nature around 0.83 volts of input.The trip point is where vin=vout staright line cuts the VTC. So here the trip point is 0.83. So one can say that there are like 3 regions in the VTC curve, the portion where output is high, the place of transistion and the one where the output goes low. But actually there are five regions of operation and they are based on the working of inverter constituents, that is the NMOS and the PMOS transistors with respect to the change in the input potential.

![143764318-d0893545-f47c-44b8-a27c-8de8bc4f0759](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/4686bf1c-2d64-4fde-ad4a-d69af84029f1)

Ideally if the trip point is VDD/2 then we get the maximum noise margin. In ideal case the trip point would have been 0.9 . So shifting the VTC curve towards right will help us to achieve the trip point near VDD/2. For this we just need to increase the width of PMOS transistor.The Simulation shows: 
![Screenshot from 2024-01-03 12-58-39](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/37980946-dfa7-4a99-8c5c-239861ebb45c)

Here the width of PMOS/ width of NMOS=2. Previos case it was 1.





