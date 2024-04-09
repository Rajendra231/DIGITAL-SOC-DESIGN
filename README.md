# Digital-SOC-Design-With-VSD-Labs

Digital System-on-Chip (SOC) design is a fundamental aspect of modern electronics engineering, facilitating the integration of various digital components onto a single chip. The "Digital SOC Design with VSD Labs" course provides a comprehensive overview of SOC design methodologies, tools, and techniques, with a hands-on approach using Virtual Silicon Development (VSD) Labs.

Benefits:

- Gain a deep understanding of SOC design principles and methodologies.
- Develop practical skills through hands-on lab exercises using VSD Labs.
- Learn from industry experts and experienced instructors in the field of digital design.
- Access to a supportive community of learners and professionals to collaborate and share knowledge.

CREATING NEW VIRTUAL MACHINE:

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/327fc352-de01-446c-bbc6-062a02853144)


![Screenshot 2024-04-08 204557](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/d21ed282-9aaf-413b-933e-0e006624800e)


![Screenshot 2024-04-08 204627](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/5c744692-8648-4ee0-9aa7-4c9631604900)

![Screenshot 2024-04-08 204656](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/cd9e87a0-c475-43be-87d3-3ea78b3c9974)

![Screenshot 2024-04-08 205308](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/97a87429-371e-4f1b-97bd-5c995249b0d6)


# DAY 1: Section 1 Inception of open source EDA Openlane and Sky130 PDK
Synthesis and calculating flip-flop ratio:

#Using following command to invoke openlane:
- docker
- ./flow.tcl -interactive
- package require openlane 0.9
- prep -design picorv32a

![Screenshot 2024-04-08 212105](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/6c20e74b-2df8-48cf-9207-e4d86c4415bb)


#Running synthesis

```bash
  run_synthesis
```


![Screenshot 2024-04-08 213343](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/fd67e3f9-8fb4-4f1d-9f56-736e5a22cb28)

![Screenshot 2024-04-08 213527](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/d66c33ba-57d6-4bbc-8eae-73b03d225b20)

#Calculating flip-flop ratio

![Screenshot 2024-04-08 213822](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/f18eb064-90f1-4789-bbff-e4286a600d05)

![Screenshot 2024-04-08 213847](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/9d144b98-b5d7-408b-ada9-686fbaf66506)


Flip-Flop ratio = Total number of Dflip-flop / Total number of cells
 
Percentage = Flip flop ratio * 100

 Ratio=1613 / 14876 
 
Percentage = 10.84296854%

# DAY 2: Good floorplan vs Bad floorplan and introduction to library cells

```bash
  run_floorplan
```
![Screenshot 2024-04-08 225508](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/5db362bb-ca56-44fc-bf60-3ccc71911cf8)


![Screenshot 2024-04-08 225534](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/6ca2cdec-1b6e-4b67-ba66-f7edeb65e1e0)

#Examining floorplan using Magic

```bash

  magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged_unpadded.lef def read picorv32a.floorplan.def &

```



![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/70a40d1a-9ba5-438e-914e-dde9e5cfb779)

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/e51f4673-81e6-44f7-b43a-ae1dbc317444)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/dfb798a6-aec9-4775-87e0-e83147a5f45f)

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/756fa90b-e08b-47bb-87da-0a5bb8471341)

```bash
  run_placement
```
![Screenshot 2024-04-08 234012](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/711ee225-8855-4beb-ba33-905b235745d7)

```bash

  magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged_unpadded.lef def read picorv32a.floorplan.def &

```
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/4f852f4c-e70a-4944-838a-de40e66cf780)


# DAY 3: Design library cell using Magic Layout and ngspice characterization

#Modifing floorplan


```bash
  set ::env(FP_IO_MODE) 2
```
```bash
  run_floorplan
```
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/bdb9123a-af50-4dbd-8811-20bc0f2acf33)

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/a8b04762-465f-4f0c-bb48-4f5d548ab4e7)

```bash

  magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged_unpadded.lef def read picorv32a.floorplan.def &

```
#Observed changed design


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/9c1952ac-e3d5-4a29-946e-ec78651337d8)

#Cloning inverter from github repository

```bash

  git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```
```bash

  magic -d XR -T "/libs/sky130A.tech" mag sky130_inv.mag
```


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/4156bbee-0fd8-4dc2-8d55-6c5bafff0171)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/3bd92f34-29b8-4762-87bb-f88c104eecb8)

#nmos
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/8a48973e-fe61-45fd-ba04-4e6db2ff9da3)

#pmos
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/1d3df3f0-4de1-4976-b3a5-8d5655a96a49)

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/910078a4-1c3f-4941-a0d2-22346cff77bb)

#spice file

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/a3996564-afc9-40ee-9423-1a743e7f8f97)

#modifing file

```bash

  option scale=0.01u 
include ./libs/pshort.lib
include ./libs/nshort.lib
//. subckt sky130_inv A Y VPWR VGND
M1000 Y A VPWR VPWR pshort_model. 0w=37 l=23
+ ad=1443 pd=152 as=1517 ps=156
M1001 Y A VGND VGND nshort_model. 0 w=34 l=23
+ ad=1435 pd=152 as=1365
ps=148̦
VDD VPWR 0 3.3V
VSS VGND
0 OV
Va A VGND PULSE(OV 3.3V 0 0.1ns 0.1ns 2ns 4ns)
CO A Y 0.0754fF
C1 Y VPWR 0.117fF
C2 A VPWR 0.0774fF
C3 Y VGND 0.279fF
C4 A VGND 0.45fF
// C5 VPWR VGND 0.781f
//. ends 
.tran 1n 20n
.control run
endc
end
```
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/dd09981d-da1f-4f6c-9719-84ccccfba9f6)

#Now run 

```bash

  ngspice sky130_inv.spice
```
Now ploting graph by using command plot y time a

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/0fb7f041-7f43-493c-92dc-ad36da65b2dd)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/202b99b7-29a6-427a-98ab-9bc6fc795ee1)

Increasing the value of C3 0.24ff to 2ff

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/4abb666b-f5ef-464a-9fa5-3891f17fe281)

#20%

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/2a67f4d9-99e8-454c-a74e-f8e530912d20)

#80%
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/218bd6f4-0093-4ad5-9511-a7236b483a96)

#50%
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/ccb905b8-1612-427e-be32-735bcd682842)

The value of parameters are:

- Rise time

rise time= (2.2489 - 2.181)e-09 = 66.92 psec

- Fall time

fall time= (4.0951 - 4.0526)e-09 = 42.51 psec

- Propagation delay


propogation delay =(2.2106 - 2.15012)e-09 = 60.48 psec

- Cell fall delay

cell fall delay =(4.07735 - 4.04988)e-09 = 27.47 psec

# DRC Corrections and rules

For doing DRC coorection we have to download lab files using
```bash
   wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
```

![Screenshot 2024-04-09 024807](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/360297d6-d573-43cd-9da2-f17043c1a13f)


Sky130A Periphery rules: https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/5fced034-2e0b-4903-a942-0e5a8b1e9286)


To start magic tool,we can use command 
```bash
  magic -d XR
```
And we will open `met3.mag` file

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/e91f35f4-b9ad-4648-9e12-22efdf343b19)

We can see contact cuts using `cif see VIA2`


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/1d13d0c4-3aba-40ed-be74-e1a4233057c6)


# Fixing ploy.9 error

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/1954caa8-7c3a-440d-9301-485ae03681b6)

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/d2de3ffa-8593-4ebd-927d-2dedc5f2e1c9)

Now we run `tech loadsky130A.tech`  and do drc check using `check drc`

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/9f741a38-484a-4c39-9317-1cbaefb26457)

#  Lab challenge exercise to describe DRC error as geometrical construct


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/b44948b6-d7d1-4f84-9356-9d9959e559f5)

#Making some changes in sky130A.tech file

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/f0af79b2-8a80-412c-a00d-089dc2721fe1)


![Screenshot 2024-04-09 132248](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/6c2d16ef-5570-4c94-9ac9-9437eb213c40)

Now executing the command `drc style drc(full)` and `drc check`

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/1bae79c4-935e-4acc-8ab4-e5d86f13e51a)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/931b9045-e6df-46cc-a139-23a789124d85)



![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/3011ddbb-0c09-4f65-8df9-ab3b615b6dc7)





