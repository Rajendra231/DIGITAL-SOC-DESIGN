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


# DAY 1:  Inception of open source EDA Openlane and Sky130 PDK
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


# DAY 4: Pre-layout timing analysis and importance of good clock tree

#In this lab we are converting grid info into lab info

We can open track file from directory shown in image and get more information about it.

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/ab9d8018-176c-4982-b2c5-a8547defe8f6)

![Screenshot 2024-04-09 142451](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/e2aef559-6f01-4075-a5ce-951ea7f4b478)


![Screenshot 2024-04-09 143607](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/2a61d9b2-2c17-4aaa-bc05-3bd006f3bc07)



![Screenshot 2024-04-09 143414](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/9a290f3e-0efe-4462-bf93-38b7687e85d9)



#converting magic layout to std cell LEF


![Screenshot 2024-04-09 151110](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/864fc7e7-a754-479e-9af7-9475c9f936ea)


![Screenshot 2024-04-09 151315](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/1ffb3598-15c3-409d-8578-a2635acd447f)

now we will open this file in magic using `magic -T sky130A.tech sky130_vsdinv.mag &`

now we have to run command `lef write` in takon window to extarct the lef file

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/14017f26-1086-4142-9d53-a732f8e8efc1)

we will need to move the files to the src folder where all design files are available.

To do this we can copy the file using `cp` command


![Screenshot 2024-04-09 153222](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/9f281d44-2cf2-43a5-b5c5-e2328386fd4f)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/4aa54bd3-d8e2-42bb-8f30-371f314de35d)

#OPENLANE 

- Now we will open openlane directry and run `docker` command

- ./flow.tcl -interactive

- package require openlane 0.9

- prep -design picorv32a

- set lefs [glob $::env(DESIGN_DIR)/src/*.lef]  

- add_lefs -src $lefs

- run_synthesis

- prep -design picorv32a -tag  08-04_18-39 -overwrite

- set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

- add_lefs -src $lefs


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/bd0a6cf0-41ff-4170-8ba0-9ee0c70bf970)


![Screenshot 2024-04-09 160257](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/14c38b3a-a486-4ce6-9f8d-d86d4da22d2f)



```bash
  run_synthesis
```

![Screenshot 2024-04-09 160334](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/24b4fe67-9ca1-47c8-9f92-337e354f5061)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/3e6903e3-884d-49ed-a523-743777344f85)


#configuring synthesis settings to fix slack and include vsdinv

We will modify README.MD file in the configuration directry

 
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/ff9af182-589c-429e-8692-47b98890ae30)

Now we will run the following commands in openlane:


`echo $::env(SYNTH_STRATEGY)`

`set ::env(SYNTH_STRATEGY) "DELAY 3"`

`echo $::env(SYNTH_BUFFERING)`

`echo $::env(SYNTH_SIZING)`

`set ::env(SYNTH_SIZING) 1`

`echo $::env(SYNTH_DRIVING_CELL)`

`run_synthesis`


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/6e44639f-9168-4949-9db8-efa33ec189eb)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/bf8dcc07-9b70-4ea4-843e-ca9911bab569)


```bash
 run_synthesis
```


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/8cb1cea1-bb54-467a-86e9-28c735eeac8d)



![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/1fe1d069-6276-466d-a558-63b752d5ec42)

#ERROR SOLVING

`init_floorplan`

`place_io`

`tap_decap_or`

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/3d63d2f3-8b88-4c5e-acf4-4be04e8fcab1)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/28fd08c1-8820-4615-a42c-197de7b816ca)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/f550be0c-ef2c-4063-8b56-ae81d7a88489)

Errors are solved succesfully,so now we are using `run_placement`command

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/696cb5cd-fd76-402b-ac97-d3ad5fc1646f)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/81b19396-54c0-4071-a43c-dbca4789b551)

```bash
  
   magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged_unpadded.lef def read picorv32a.floorplan.def &
```
   

![WhatsApp Image 2024-04-09 at 18 47 30_50ee1ce4](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/18104b2e-a5bc-4f4e-8832-fe9487f18fd9)


#placement output im magic

![WhatsApp Image 2024-04-09 at 18 46 57_3ef16343](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/7ad21e07-d671-4f62-90e1-b67c92d2ea76)


To view internal layers we need to run command `expand` in tckon tab

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/a8bf4627-ee06-4fc1-ad8e-39e7412e5471)

# DAY 5:  Final steps for RTL2GDS using tritonRoute and openSTA

#performng PDN generation and layout

 Building power distribution network

` docker`

`./flow.tcl -interactive`

`package require openlane 0.9`

`prep -design picorv32a -tag 08-04_18-39`

`echo $::env(CURRENT_DEF)`


 
![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/1e5e597d-527f-4556-9f7c-3899e8fc656d)


now run `echo $::env(CURRENT_DEF)` IN OPENLANE 


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/29e87141-5540-4c29-93df-84f1a54be9f2)

#Generating pdn(power distribution network) using `gen_pdn`

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/01edd8a3-ec12-4fe2-bf49-10384d0fedf0)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/f30a8448-6c7b-4a1f-97b2-f50c1d3a4e80)

#Routing

 Running `echo $::env(CURRENT_DEF)` and ` echo $::env(ROUTING_STRATEGY)`

 ![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/88ac0d24-fea1-4ce0-b5ed-1a7a89b72e5e)

 ```bash
   run_routing
```

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/8b3f58f7-0146-4f27-bee9-d1eec64a6d1c)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/d9fe423e-70c4-4661-a737-27bd99fd933c)

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/0fcb0c22-57d3-46c2-bfd4-c015e39e4f07)


Since OpenLANE does not have a SPEF extraction tool, this process needs to be done outside of OpenLANE directory.

The resulting .spef file can be located in the routing folder under the results folder.


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/a26bbeea-d5fa-487c-9144-46ea26246abe)


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/160e45ef-5ae7-40ce-88ac-bc42ea5a3287)

#Final generated layout

![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/96cd239d-2a74-4081-9fbd-6184d0f3742c)



# References
- Workshop Github material
- https://github.com/google/skywater-pdk
- https://github.com/nickson-jose/vsdstdcelldesign
- https://sourceforge.net/projects/ngspice/
- https://github.com/
- https://www.vlsisystemdesign.com/wp-content/uploads/2017/07/Introduction-to-Industrial-Physical-Design-Flow.pdf


# Acknowledgement
I would like to extend my heartfelt thanks and express my deep gratitude to Mr. Kunal Ghosh, Co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd., and Mr. Nickson Jose for their exceptional guidance and presentation of the DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING workshop. Their expertise and insights have been invaluable in helping me learn about physical chip design using OpenLANE software and other advanced techniques. The workshop was meticulously designed and executed, and I have gained a wealth of knowledge and new perspectives from it. I cannot thank Mr. Kunal Ghosh and Mr. Nickson Jose enough for their unwavering commitment to sharing their expertise and making this workshop a resounding success.




