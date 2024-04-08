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







