# Digital-SOC-Design-With-VSD-Labs

Digital System-on-Chip (SOC) design is a fundamental aspect of modern electronics engineering, facilitating the integration of various digital components onto a single chip. The "Digital SOC Design with VSD Labs" course provides a comprehensive overview of SOC design methodologies, tools, and techniques, with a hands-on approach using Virtual Silicon Development (VSD) Labs.

Benefits:

- Gain a deep understanding of SOC design principles and methodologies.
- Develop practical skills through hands-on lab exercises using VSD Labs.
- Learn from industry experts and experienced instructors in the field of digital design.
- Access to a supportive community of learners and professionals to collaborate and share knowledge.

CREATING NEW VIRTUAL MACHINE:

![Screenshot (595)](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/66f9a57d-d125-4503-b3b8-65d0a37b3af7)


![Screenshot 2024-04-08 204557](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/6407ec7a-3bc1-4b77-8a57-ef25cac26d1d)


![Screenshot 2024-04-08 204627](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/d442196c-c426-46d1-85ed-aaff58932fdf)


![Screenshot 2024-04-08 204656](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/cd79e620-8890-4815-9a22-2fa20f815b42)

![image](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/ad1cdf02-9179-4562-8720-c31af7314307)

# DAY 1: Section 1 Inception of open source EDA Openlane and Sky130 PDK
Synthesis and calculating flip-flop ratio:

#Using following command to invoke openlane:
- docker
- ./flow.tcl -interactive
- package require openlane 0.9
- prep -design picorv32a

  
![image](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/5c330b22-64d1-4b82-8aa6-1a2ee14c51e6)

#Running synthesis


![image](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/a5149f1f-81c8-4364-9aa9-6b0a6732fd64)

![image](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/1fb74963-6762-4914-9999-b1e30eff0f58)

#Calculating flip-flop ratio

![image](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/f0cf9bed-8c33-48f1-b5e4-4880e70c57c4)

![image](https://github.com/Rajendra231/Digital-SOC-Design/assets/166032447/ad77a403-3556-441c-bf85-495d5479f522)


Flip-Flop ratio = Total number of Dflip-flop / Total number of cells
 

Percentage = Flip flop ratio * 100

 Ratio=1613 / 14876 
 
Percentage = 10.84296854%


