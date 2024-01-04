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

From the simulation tpHL=0.24 picosecond and tpLH=0.35 picosecond.

#### 1.3.2 RISE and FALL time
Here we will calculate rise and fall time and factors that affect the rise and fall time. 
![Screenshot from 2024-01-04 01-40-19](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/355eb680-5d14-4d82-92d3-558925aa5837)

From the simulation the rise time is approximately 0.35 picosecond and fall time is 0.31 picosecond. 

Factors affetcting the rise time:
1) **Increasing the power supply VDD will reduce the rise and fall time.** In the simulation we will change our power supply from 1.8V to 1.0V and observe how it is affecting our rise time.
![Screenshot from 2024-01-04 01-49-57](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/d5b80ff6-359f-4275-9c19-3c34898e32be)
Here Rise time increases from 0.35 to 0.6 picosecond.
2) **Increase the Load capacitance**. It will increase the rise time. Delay will increase. Here I changed the width of PMOS to be 4 and NMOS to be 2. 
![Screenshot from 2024-01-04 19-39-03](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/7c2ffca7-a862-4aa0-bdd0-6c00a10fb444)

Here the load capacitance value is 1 pico. Now changing the load capacitance from 1 to 0.5 pico will reduce the rise time from 2.55 nano to 1.28 nanosecond.

![Screenshot from 2024-01-04 19-41-07](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/042d1367-ef32-4068-8872-fd8c9a2df6a5)

3)**Increasing the width of the MOSFETs**. 
Firstly I tried to increase the width of the unloaded inverter and observed the delay. But it did not change the delay much. Becasue increasing the width is reducing the equivalent resistance of the nmos and pmos but at the same time it is increasing the internal capacitance of the inverter by the same factor. so both effect is getting nullified.  Now when the load capacitance is attached I tried to double of width of both MOS. width of PMOS=8 , width of NMOS=4. From the Simulation :

![Screenshot from 2024-01-04 19-45-59](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/4f0e1dd4-41e8-47de-93e6-d13961a3d665)

We can observe that The rise time is reduced to 0.63 ns from 1.2 ns. So for loaded cmos inverter increasing the width will reduce the delay.

### 1.4 Power Analysis
CMOS Inverter is associated with total 3 kinds of power. 
1) **Dynamic power** -The input is switching,the capacitor is continously charging or discharging,there is a power loss involved in the process and it is the dynamic power.
2) **Switching power**- When vin>Vtn (Threshold voltage of the NMOS) ,both the transistor starts conducting,when both are in saturation the current is maximum and after VDD-Vtp, current reduces again to 0. this involved power dissipiation is known as switching power.
3) **Leakage Power** - In steady state ideally there is no path for current  from   VDD to ground. But there are some leakage current involved and it dissipiates power even in the steady state.
**NOTE** The dynamic and switching power is involved in transient analysis and leakage power is involved in steady state analysis.

Below is the average power simulation.

![Screenshot from 2024-01-04 21-43-29](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/860094d5-ae8e-4265-85ae-1f751b531cd3)

The average power consumption is 0.81microwatt. 

Ways To reduce the power consumption
1)**Reduce Switching cycles**- The above power is associated with one switching cycle. but as the no of input cycles increases the power dissipiation increases.
2) **Reduce load capacitance** -reduncing the load capacitance will reduce the power consumption. It can be achieved with the help of layout. 
3) **Reduce Power Supply** - Reducing the power supply will automatically reduce the power consumption.

Below is the simulation of average power consumption when the load capacitor is reduced to 0.2pico from 0.5 pico.

![Screenshot from 2024-01-04 21-48-21](https://github.com/K-shejuti/Inverter-Design-and-analysis/assets/152790020/076ab7f4-9433-4fa7-8f0f-3f82400a26f9)

The power dissipiation is reduced to 0.32microwatt from 0.81 microwatt.












   












