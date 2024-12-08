---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---
By: Shine Sujith

Hello, This is my project for the module System on Chip Design and Verification (SoC) [1]. In this project I use Vivado to create, test and build a VGA (Video graphics array) design. VGA is a standard of video design introduced by IBM in 1987 [2]. 

## **Template VGA Design**
### **Project Set-Up**
To start we were given two verilog code templates along with a testbench and a design constraints file which we added to the project after creating it using Vivado. We had to set up the project on the C drive located on the computers in college because Vivado had some trouble writing to files located on OneDrive (Fig1.1). The first thing I did after adding my files to the project was moving the testbench into simulation sources since it was opened in design resources by default. Afterward I made sure the rest of the project heirachy was correct (Fig1.2). Initially we didn't have a clock set up, so we had to set one up in the clock wizard at a frequency of 25 Mega Hz. This frequency was chosen so we would not see any visable flickering. Once everything was set up I ran a simulation, synthesised, and impelmentation as well as generated a bitstream. I then connected to and programmed the board. I repeated this process for the second template but first I had to add some code into the VgaTop file to tell it to use the second template and not the first one.

![image](https://github.com/user-attachments/assets/ded24d46-4e81-489b-a733-083690a949c8)

![image](https://github.com/user-attachments/assets/5a1233ce-f7c1-4c04-91aa-212e3d4bcbf4)

### **Template Code**
The first template **ColorCycle** used a **state machine** to change the current state of the code (Fig2). Once the entire screen (480x640) was colored by writing a 12 bit value to the color register, it would change state to a different color. The first four bit of the register represent the red value, the middle four are the green value and the last four bits are the blue value. A count was used to wait a few seconds before changing the state so it would be visible to the human eye.

![processed-81E5C9A2-7114-47F4-B86C-36D499BD9F69](https://github.com/user-attachments/assets/cc953460-1735-486a-b36c-3e098141c3f8)

The second template **ColorStripes** uses two additional inputs row and col. These inputs represent the row and column of the current pixel. Another difference is that the stripes code uses three 4 bit color registers instead of one 12 bit register. In stripes **if statements** are used to change the color of the pixels. When the col value is within a certain range it writes a 4 bit value to three color registers one for each of the three colors.

Both templates were similar but also introduced new techniques to display an image. This was very useful when it came to creating my very own image. For example, they both had three registers to write to, to change the color of the pixel however one used a 12 bit register that was then split into three parts and assigned to three 4 bit registers on every positive clock edge while the other just assigns the three color register to another three color register on each positive clock edge.

### **Simulation**
The simulation process involves using a testbench to simulate the code. By doing this we can reduce the amount of time it takes to test the code. This is because if we want to run the code on the board, we must generate a new bit stream which involves running synthesis and implementing first before programming the board. This process takes time and must be done each time we make any changes to the code. It is much easier to run a simulation which only takes a few seconds. Using the simulation, we can get an idea of how the output might look like. In FigH we can see the output of a simulation or the waveform analysis in FigG. 

On the output we can see a clock and a reset which is at a value of zero. From this we can tell that the reset is active when it is high or at a value of one. We can also see hsync which is responsible for the horizontal alignment of the screen and vsync which is responsible for synchronising the refresh rate and frame rate of the screen, so we don’t see screen tearing []. We can also see the row and column changing and the values of the three color registers changing between 0 and f which is used in this case to represent 0000 and 1111.

![processed-37E39B11-F80F-4929-A3C0-83CAB8B4BC99](https://github.com/user-attachments/assets/fa548991-c6b9-414d-9b07-ec4d74d2f3e9)

color cycle:

![image](https://github.com/user-attachments/assets/030c42c9-9e93-411c-b0c7-70a5f9142dbe)

### **Synthesis**
Synthesis and implementation are two very important step of the design flow. At first glance they appear to be the same how ever thay are quite different. Synthesis involves converting RTL ([Register Transfer Level](https://www.doulos.com/knowhow/verilog/rtl-verilog/)) code into a netlist and implementation uses this netlist and run optimization, placement and routing on it [].

The **VGA Top architecute diagram** in FigL is a simplified version of the **schematic** in FigM. **Clk** and **rst** are inputs, clk is wired to the clock wizard which is used to generate a 25 Mega Hz clock. clk is also wired into ColorStripes or ColorCycle. VGA sync is responsible for generating a vsync and an hsync as well as a vidon signal along with a few other outputs that are passed into ColorStripes or ColorCycle where the main logic is performed. The outputs are hsync, vsync, and the three color registers. In FigN we can see an image of the device all the blue squares near the bottom left of the board are LUTs (Look Up Tables) being used to adust the rgb values and dispaly the design on the screen [].

![processed-28B6500B-BBC0-4A91-9F7F-55FD42A9083C](https://github.com/user-attachments/assets/63b79e85-6e86-4438-b18c-0f44fe19c3a2)

color stripes

![image](https://github.com/user-attachments/assets/576dd309-73ae-4b3d-9a01-0b93a6a981fd)

![image](https://github.com/user-attachments/assets/d88832a5-3f94-467c-9017-f62e7fcb3e3a)

![image](https://github.com/user-attachments/assets/04db0198-13bd-41ab-b7a8-9df35fef4618)

![image](https://github.com/user-attachments/assets/6a09c287-8547-4353-9f63-115c5318a786)

### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

![processed-3CAAAD42-3530-4D62-A645-65E38B7A5CF4](https://github.com/user-attachments/assets/88f2f267-7b83-4da9-9b67-dfc1c6497c1c)

![original-F0942EF8-6B20-451B-AFD8-20365A40162E](https://github.com/user-attachments/assets/e25c8cd1-6253-460a-bef2-4a55f86c8224)

![original-6C403910-FDC3-4E9E-9A8B-14E0686C30DA](https://github.com/user-attachments/assets/044c894d-4f72-4301-b184-6e5d888178e8)

![original-5CE57604-4EFA-4A78-8DD0-70804379F62D](https://github.com/user-attachments/assets/e9a47742-9beb-4f26-8035-49b1a61ebef9)

## **My VGA Design Edit**
My original idea was to split the screen up into square 60x80 pixels to form a grid of different colors then I would make the colors keep shifting one grid over contiously. To me this idea was very achievable and not too complex when I started, however as time went on there where a few limiting factors that I failed to take into account that caused me to rethink my original idea for example a lack of time caused by a slow start due to a lack of understanding of the basics of  verilog and lack of access to the boards outside of class. I then tried to simplify my design to a black and white checkered pattern that alternates every few seconds. I chose this design because it incorperates aspects of both of the tempaltes we were given. In the end I managed to create a black and white grid pattern that alternates. 

### **Code Adaptation**
I used the ColorStripes code as the base and incoperated a state machine and delay using `count` and `COUNT_TO` parameteres. I thought about simply hard coding the checkered pattern which would have been very easy to acomplies however i decided agsinst it because it would be too easy and not much of a challenge, so instead I added two more registers that were updated every 60 pixels and 80 pixels to seperate the screen into 60x80 segments instead of writing an if statement for each individual square and coloring them that way. I originally tried to alternate the colors using a new register called counter which would alternate between a 1 and a 0 after each 60x80 square. I had a few issues with this approch because I wasn't updating the two registers and the count resister on the clock edge, but this wasn't the only issue. Once is fixed the syncing issue I was able to display black and white stripes that alternate. This was a step in the right direction however the were a few pixels that were incorrectly colored. The other problem was that it was stripe pattern and not a checkered one. I thought this issue would be easily fixed by changing to an odd number of squares, so I changed the size of each square from 60x80 to 96x128 pixels. This gave me the result seen in FigF after this failure I was running out of time and decided to simpify my code by not messing around with adding registers and just using the `%` (modulo) operator. By using the condition `if((row/96) % 2 == 0 && (col/128) % 2 == 0)` I could split the screen into a five stripes on both the rows and columns with each stripe being 96x640 or 480x128 pixels depending on if it is a row or column. I then used the condition `if((row/96) % 2 == 0 || (col/128) % 2 == 0)` to get the other half of the checkered pattern I wanted. In the end I ran out of time and could not get an output for the checkered pattern, however if I had a few more minutes I would have had it. If I had more time all I had to do was split the rows up into five using if statements then used `%` to check if `(col/128) % 2 == 0` or `(col/128) % 2 == 1` depending on the row. 

![image](https://github.com/user-attachments/assets/f9f903d0-c7cf-4d6b-b809-cc1092bce483)

![image](https://github.com/user-attachments/assets/555b17bd-76c6-47b7-b024-2926d4ed76de)

![image](https://github.com/user-attachments/assets/991e8967-51e8-44b6-a689-31207f8de4aa)

![image](https://github.com/user-attachments/assets/0f7d9bd6-a859-46ec-9fe4-463606f2f64f)

### **Simulation**
I used the same testbench to simulate the code I didn't have to make any changes to it because I didn't incorperate anything like a switch or additional registers in the end. I used the simulation from time to time usually when making consecutive smaller changes to my code, however I found it easier to visualise the output and what is wrong with it when it is displayed on the screen rather than just from looking at the waveforms. For the most part there isn't much to note since its very similar to the previous ColorStripes template output. Although the output may look a little different due to the fact it is more zoomed in and I ran it for a much shorter time frame.

![image](https://github.com/user-attachments/assets/f4a5ae1b-3dc8-4fea-97a3-5993621af0ad)

### **Synthesis**
Using Vivado I ran sythesis and implenetation on my own code just like I did for the template code every time I made changes to the code. There weren't many difference when it comes to the schematic that was generated during the sythesis and implementation process. The layout of the schemetic looks much different, However if you look closly its practical the same. This makes sense since I just incorperated aspects of both templates in my code and changed it slightly so I expected there to not be any major differences. When looking at the device image we can see that alot more LUTs are in use, this is mostly because my code is producing a more complex output than the template code.

![image](https://github.com/user-attachments/assets/025d7d50-9c1f-4d28-aec4-d050d58d5452)

![image](https://github.com/user-attachments/assets/4986a99c-51ff-4896-82cf-a1971168a189)

![image](https://github.com/user-attachments/assets/f1d2cf9b-97b7-47cf-8723-b79cb83f421c)

### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

![processed-5974133D-C640-4B49-8A11-CE0A13A8515F](https://github.com/user-attachments/assets/5cfb9453-f5fd-4bba-9c31-f79f925ccbaa)

![processed-97377106-6E61-469B-B2B8-5B9D03F63449](https://github.com/user-attachments/assets/f22b5fc4-cbbe-4f38-8e16-a34c85d390f3)

![processed-FA5F6EB5-6C5E-40D0-AD3D-6E7DCAEFC484](https://github.com/user-attachments/assets/9264efcc-ed4b-462f-98cf-190f99cb69cb)

![processed-532B3647-FABE-467A-AC7B-46C3F17C78A7](https://github.com/user-attachments/assets/fe5da82d-4101-4a33-9134-442399b27079)

![processed-C36172DE-07F8-4656-88D7-4323F40A0728](https://github.com/user-attachments/assets/4e059b95-e2f2-460b-a447-d84999f03868)

![processed-9EE10D94-5F3B-4DA7-8EC2-A64C5223956C](https://github.com/user-attachments/assets/57fdccd8-2a54-4bc1-87c2-e285f9fb6761)

![processed-7A661696-972F-4907-9B7D-01295F3E3761](https://github.com/user-attachments/assets/998d1da2-0841-4612-a937-8e8275e4e783)

![processed-83FEA5B1-DA7E-45A2-98AC-C1DCC32A7907](https://github.com/user-attachments/assets/66c47b25-d45f-47b3-b00a-893224f0c681)

![processed-4D9C0AC7-89D9-4269-9997-313D02093A94](https://github.com/user-attachments/assets/2144ff2f-9ab9-42b4-a908-aad389c040a1)

## **References**
[1] M. Lynch, "SoC", Lecture, ATU, Galway, 2024.

[] Wikipedia, "Video Graphics Array", [Online] Available: [https://en.wikipedia.org/wiki/Video_Graphics_Array](https://en.wikipedia.org/wiki/Video_Graphics_Array) [Accessed 07/12/2024].

[] T. Polanco, "What is VSync, and should you turn it on or off?", 2024 [Online] Available: [https://www.tomsguide.com/features/what-is-vsync-and-should-you-turn-it-on-or-off](https://www.tomsguide.com/features/what-is-vsync-and-should-you-turn-it-on-or-off) [Accessed 07/12/2024].

[] AMD, "The difference between Implementation and Synthesis", [Online] Available: [https://adaptivesupport.amd.com/s/question/0D52E00006hpkc2SAA/the-difference-between-implementation-and-synthesize?language=en_US](https://adaptivesupport.amd.com/s/question/0D52E00006hpkc2SAA/the-difference-between-implementation-and-synthesize?language=en_US) [Accessed 08/12/2024].

[] P. Inhofer,"What is a LUT(and how do you use a LUT)?", 2021 [Online] Available: [https://mixinglight.com/color-grading-tutorials/understanding-luts/](https://mixinglight.com/color-grading-tutorials/understanding-luts/) [Accessed 08/12/2024].

