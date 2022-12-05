# Antenna Design Workshop
###### tags: `Antenna Design`

## 08/11/22

Project Template -> MW & RF & Optical -> Antennas -> Wire -> Time Domain -> default settings -> next

Setup Solver: Button to run the simulation

Modelling tab: Import objects into the workspace
Simulation tab: Design frequency range, background and boundaries

Designing an antenna:
* Modelling the antenna
* attach the source
* check whether it radiates

### Task: 1
Design a **half-wave dipole** antenna for 1 GHz

-> Wavelength: 300mm 

-> Total length of antenna = $\frac{\lambda}{2}$ = 150mm

-> Therefore the upper and lower portion are of 75mm each.

-> The various parameters can be defined in terms of variables, instead of changing the numerical value everytime.

-> Outer Radius of cylindrical wire = 5mm

-> Inner Radius of cylindrical wire = 0mm

Outer radius is defined by an variable `r_o`
The Zmin and Zmax parameters are defined by variables `-z_min` and `-z_max`
outer radius r_o = 2.5
z_min = 5,
z_max= 75
lamda = 300

Select the material copper(annealed) from materials library

For dipole 2 ->
create another cylinder with same dimensions and material as dipole1. The Zmin and Zmax parameters of this new dipole are assigned as variables `z_min` and `z_max` respectively.

For port ->
For the AC source, select Discrete Port from 'Ports' in navigation tree
Characteristic impedance is set to be $50\Omega$.
The source is placed between `0,0,-z_min` and `0,0,zmin`. Hence the coordinates (0,0,-5) & (0,0,5)

Frequency setting->
In simulation tab select frequency set `min: 0.5` `max: 3` 
as the resonant frequency is 1GHz.
In the next dialog box selxt accuracy to be -30db and Port as Port1

The results can be observed by selecting 1D Results -> S-Parameters from the navigation tree. To obeserve the freq corresponding to minimum, axis markers can be used.

## 09/11/22

Radiation resistance = $80{\pi}^2 ({\frac{dl}{\lambda}})^2$

$A(r) = \frac{\mu}{4\pi}I dl\frac{e^{-j\beta r}}{r}e^{j\omega t}$

Triangle Current Density -> ? (check its derivation from books)

For half wave dipole of length $\frac{\lambda}{2}$ the current distribution is sinusoidal ie either $sin$ or $cos$

Correct answer is 73$\Omega$ 

$dl \rightarrow R_r = 80\pi^2(\frac{dl}{\lambda})^2$

find $E_{\theta}$ and $H_\phi$

The port should see the value of 73 ohms
So update the port impedance to $73\Omega$ by right clicking the port1 in navigation tree and selecting properties.

![](https://i.imgur.com/fu3uYC5.png)

The first minimum is at 0.8575 MHz

For 50$\Omega$:
![](https://i.imgur.com/4YIzNcA.png)

The impedance value of half wave dipole is 73$\Omega$

The second resonant frequency

For field monitor ->
Navigation tree -> Field Monitor -> Right Click - New Field Monitor -> Dialog box opens -> 

For radiation Pattern of antenna ->
Navigation Tree -> 2D/3D results -> Far fields



![](https://i.imgur.com/tNCvbxi.png)


Select field monitors : 
- E-Field
- H-Field and surface current
- Far Field
- Current Density

Simulate Again.

Observe current density under 2D/3D Results

Animate fields to observe animation of current density
From plot properties change the animation rate to observe the surface current density better.
 
 -x-x-x-
 
For 1GHz resonant frequency:
$\frac{\lambda}{2} = 150 mm$

For 2.5GHz 
$\lambda = 120mm$

So $1.25\lambda = 150mm$
Apply the field monitors for 2.56GHz and observe the radiation pattern:
![](https://i.imgur.com/Sn3IRlQ.png)

For surface current, two minimas should be present at the same instant of time.

Farfield -> polar

![](https://i.imgur.com/fJhfDIe.png)

## 10/11/22

**Assignment 1** 
Design a dipole antenna whose total length is $1.5\lambda$.

**Yagi Uda antenna:**
Central axis is a dipole antenna.

![](https://i.imgur.com/DSy0uus.png)

Yagi Uda antenna
![](https://i.imgur.com/bgvEH9R.png)

Dipole Length = $0.458\lambda$ to $0.5\lambda$
Reflector Length = $0.55\lambda$
Distance b/w reflector and dipole = $0.35\lambda$
Distance b/w dipole and director = $0.125\lambda$

Creating a Yagi Uda Antenna:
Follow the previous steps for making the dipole
For creating the reflector and Director make cylinders of appropriate dimensions and the corresponding X and Y centre

Observe the resonant frequency from the s11 parameters. Apply the field monitors at this frequency aand observe the radiation pattern:

![](https://i.imgur.com/HZy3b0e.png)
![](https://i.imgur.com/lGmPr1s.png)

The radiation pattern verifies that this is a directional antenna. 

Dipole with reflector:

Select dipole -> Transform -> rotate -> rotate by 180 along Y axis -> select copy -> click OK

Height of reflector should be greater than the height of dipole

For adding the port press C and select the lower and upper edge of the dipole 1 and dipole 2. Then from Simulation select discrete port, a port b/w points 

From simulation select frequency between 0-3GHz
THe Field Monitors can be applied from Simulation tab

![](https://i.imgur.com/n6oPO02.png)

![](https://i.imgur.com/9BgA70k.png)

Observe the gain for this antenna and comare it with previous session's dipole antenna. It was observed that this antenna has a higher gain 

Parametric Analysis : 
Can analyse the results of simulation for a range of parameter values.
Simulation -> Par. sweep -> New sequence -> New parameter -> z_max -> range from 55 to 75 -> step width = 5 -> Check(optional) -> start

![](https://i.imgur.com/f93xhRs.png)

## 11/11/22

**Monopole Antenna:**

![](https://i.imgur.com/jYTdcO5.png)

$\lambda = 300mm$
$radius = 0.033\lambda = 9.9$
At exact $lambda/4$ we won't get resonance. The resonance is at L - offset. 
Optimized value of outer radius of plate is 268/2mm and that of inner radius is 5.1/2 . 
radius of ground plate= $3\lambda/2\pi$ -> correction in the above diag.



#### Assigning Port 
- press 'p' to select point 
- press 'c' to select center
- select discrete port. Both points will automatically be connected

For zero offset:
![](https://i.imgur.com/sZjw7BH.png)

Radiation pattern:
![](https://i.imgur.com/KhDOGEN.png)

For parametric sweep we can change the value of parameter offset from 0 to 10.

![](https://i.imgur.com/NxD2a5h.png)

**Patch Antenna:**
Size of patch antenna should be as small as possible.
Copper Clad(Double sided PCB) of thickness 1.6mm mm.
A dielectric material(FR-4) is present between the copper clad PCB with epsilon value of 4.3/4.4

The Patch antenna is designed for the top surface whereas the bottom is ground plane.

Connect patch with the ground bottom for excitation. 
Micro-strip, Co-axial 
![](https://i.imgur.com/PYsTyMA.png)



Dimensions of patch:
* L = 29
* W = 38
* h = 1.6
* $\epsilon_r$ = 4.3

The dimensions of PCB should be 5 to 4 mm greater than your patch.

Online Dimension calculator for dimensions of micro-strip patch antenna - [Link](https://www.emtalk.com/mpacalc.php)


Substrate: FR-4 45mm * 45mm * 1.6mm
Feed; width=3mm, length=12mm
Patch size: length = 29mm, width=38mm,height=0.035mm
Slot: length = 7mm ; width = 0.6 mm 

3 components need to be designed:
* Substrate
Along X-axis width of the component whereas along Y-axis length is considered.
Select brick from modelling tab. Xmin = -(Ws/2), Xmax = (Ws/2), Ymin = 0, Ymzx=(Ls), Zmin = 0, Zmax = Hs and the material is FR-4(lossy)

* Ground
Press F and select the bottom of the substrate by double click. Then from modelling tab select extrude. The heigth is defined by the parameter Hc(=0.035mm) and material as PEC.

* Patch
Select the top part of the substrate. For the local co-ordinate system from WCS select `Align WCS`. Now from modelling select brick and put the appropriate dimensions. -(Lp/2)to(Lp/2) and -(Wp/2)to(Wp/2) and Hc. Lp=29, Wp=38
 
* Micro-strip line
Length of feed line = 8mm
Width of feed line = 3mm
Pick points -> pick edge system -> select the edge of the dielectric. We have to shift WCS co-ordinate system to this edge. So select `Align WCS` now.
Verify the directions of WCS co-ordinate with XYZ.
![](https://i.imgur.com/waXKsO3.png)
Lf = 8mm
Wf = 3mm
![](https://i.imgur.com/F9ZFIwv.png)
Press F and select the outer edge of the feed line
Home -> Macros -> Solver -> Port -> Calculate port extension coeff.
In the pop up dialog box,
Press Calculate, we get k(=5.58) value. Press Construct port from picked phase. Then close the dialog box.

![](https://i.imgur.com/DOyozxc.png)

The s-parameter graph:
![](https://i.imgur.com/a15vqoe.png)
The peak should go below -20 value. Can achieve this by changing the parameters.

