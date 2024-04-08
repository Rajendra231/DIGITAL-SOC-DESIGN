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

```bash
  magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged_unpadded.lef def read picorv32a.floorplan.def &
```


![image](https://github.com/Rajendra231/DIGITAL-SOC-DESIGN/assets/166032447/70a40d1a-9ba5-438e-914e-dde9e5cfb779)




