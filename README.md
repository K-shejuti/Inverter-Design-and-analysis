# Inverter-Design-and-analysis
CMOS Circuits generally consists of a network split into two parts, Upper one referred to as a **pull up network** and the lower half as a **pull down network**. The former consists of P-channel MOSFETs and later N-Channel MOSFETs. Reason is simple. As one transistor is on, another is off. This eliminates the issue of an resistive path to the ground and hence, no voltage division occurs(At least not a significant one). This way, one can easily achieve a Strong High and a Strong LOW from the same network. PULL UP is what offers a low resistance path to the VDD and PULL DOWN is what offers a low resistance path the GND.

## 1.CMOS inverter prelayout analysis
### 1.1 Voltage Transfer Characteristics
DC analysis would be used to plot a Voltage Transfer Characteristics (VTC) curve for the circuit. It will sweep the value of Vin from high to low to determine the working of circuit with respect to different voltage levels in the input. The following plot is observed when simulated 
![Screenshot from 2024-01-03 12-48-11](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/c8b1eaae-658a-4ec0-9266-b37eb04ce82b)

A voltage transfer characteristics paints a plot that shows the behavior of a device when it's input is changed(full swing). It shows what happens to the output as input changes. In our case, for an inverter we can see a plot that is like a square wave(non ideal), that changes it's nature around 0.83 volts of input.The trip point is where vin=vout staright line cuts the VTC. So here the trip point is 0.83. So one can say that there are like 3 regions in the VTC curve, the portion where output is high, the place of transistion and the one where the output goes low. But actually there are five regions of operation and they are based on the working of inverter constituents, that is the NMOS and the PMOS transistors with respect to the change in the input potential.

![143764318-d0893545-f47c-44b8-a27c-8de8bc4f0759](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/4686bf1c-2d64-4fde-ad4a-d69af84029f1)

Ideally if the trip point is VDD/2 then we get the maximum noise margin. In ideal case the trip point would have been 0.9 . So shifting the VTC curve towards right will help us to achieve the trip point near VDD/2. For this we just need to increase the width of PMOS transistor.

![Screenshot from 2024-01-03 12-58-39](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/37980946-dfa7-4a99-8c5c-239861ebb45c)

Here the width of PMOS/ width of NMOS=2. So the trip point is shifted to 0.86. Previous case it was 1.
### 1.2 Noise Margin analysis

Now it is time to talk about the important parameters of this device that are based off it's VTC curve. 
- VOH - Maximum output voltage when it is logic '1'.
- VOL - Minimun output voltage when it is logic '0'.
- VIH - Maximum input voltage that can be interpreted as logic '0'.
- VIL - Minimum input voltage that can be interpreted as logic '1'.
  
VOH and VOL are easy to determine as they are your aboslute values. In our case it is 1.8V and 0V respectively. For Vih and Vil, we have another method. At Vin = VIH, NMOS is in Saturation region and PMOS in Linear; while when Vin = VIL, NMOS is in Linear and PMOS in Saturation. Another interesting thing about these points is that, these are the points on the curve, when the magnitude of slope = 1. So we can use measure commands to find them on the plot. In the plot shown below, look at the points that are at the intersection of the vout curve and the blue vertical line. These are our VIH and VIL.

![Screenshot from 2024-01-03 13-49-28](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/56359f12-a2c7-450f-840e-883d0c3744c2) ![Screenshot from 2024-01-03 13-47-34](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/8eff866f-78d1-4fa5-95ce-d044858e0f61)

Noise margins are defined as the range of values for which the device can work noise free or with high resistance to noise. This is an important parameter for digital circuits, since they work with a set of specific values(2 for binary systems), so it becomes crucial to know what values of the voltages can it sustain for each value. This range is also referred to as Noise Immunity. There are two such values of Noise margins for a binary system:

NML(Noise Margin for Low) - VIL - VOL

NMH(Noise Margin for HIGH) - VOH - VIH

So for our calculated values, the device would have, NML = 0.74V and NML = 0.98V.

### 1.3 Delay Analysis
The propagation delay of inverter  is the difference in time (calculated at 50% of input-output transition), when output switches, after application of input.

![switch1_new](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/78be9763-16a2-4da5-8281-af9fb0e21b77)

In the above figure, there are 4 timing parameters. Rise time (tr) is the time, during transition, when output switches from 10% to 90% of the maximum value. Fall time (tf) is the time, during transition, when output switches from 90% to 10% of the maximum value.The propagation delay high to low (tpHL) is the delay when output switches from high-to-low, after input switches from low-to-high. The delay is usually calculated at 50% point of input-output switching, as shown in above figure. The propagation delay low to high(tpLH) is the time during transition when output switches from low to high.
#### 1.3.1 Propagation delay
Here first we will calculate propagation delay tpLH and tpHL in simulation.

![Screenshot from 2024-01-04 01-27-07](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/6cf18a38-0c0e-4d47-a7ed-3aa9b96b265f)

From the simulation tpHL=0.24 picosecond and tpLH=0.35 picosecond














