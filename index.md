---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Hello, This is my project for the module System on Chip Design and Verification (SoC). In this project I use VIvado to create, test and build a VGA design.

## **Template VGA Design**
### **Project Set-Up**
Summarise the project set-up and design flow. Include a screenshot of your own set-up, for example see the image of my Project Summary window below. Guideline 1 short paragraph.

We were given a two different verilog code templates, One of the was called color cycle which cycled through different colors on the screen and another called stripes which diaplays those colors as stripes (columns) side by side on the screen. 

![image](https://github.com/user-attachments/assets/ded24d46-4e81-489b-a733-083690a949c8)

![image](https://github.com/user-attachments/assets/5a1233ce-f7c1-4c04-91aa-212e3d4bcbf4)


### **Template Code**
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
The first template (color cycle) used a switch statement to change the current state of thr code. Once the entire screen (480x640) was colored by writing a 12 bit value to the color register it would change state to a different color. The first four bit of the regiter was the red value, the middle four are the green value and the last four bits are the blue value. A count was used to wait a few seconds before changing the state so it would be visable to the human eye.

![processed-81E5C9A2-7114-47F4-B86C-36D499BD9F69](https://github.com/user-attachments/assets/cc953460-1735-486a-b36c-3e098141c3f8)

The stripes code uses two additional inputs row and col. These inputs represent the row and column of the current pixel. Another difference is that stripes has three 4 bit color registers instead of one 12 bit register. In stripes if statements are used to change the colors. When the col value is within a certain range it writes a four bit value to three color registers one for each of the three colors.

Both templates were similar to each other but also introduced new techniques to display an image. This was very useful when it came to creating my very own image.
### **Simulation**
color cycle:
![image](https://github.com/user-attachments/assets/030c42c9-9e93-411c-b0c7-70a5f9142dbe)
color stripes
![image](https://github.com/user-attachments/assets/6822c22f-86e0-46d4-9620-8cee61fd5e5f)




Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
![processed-37E39B11-F80F-4929-A3C0-83CAB8B4BC99](https://github.com/user-attachments/assets/fa548991-c6b9-414d-9b07-ec4d74d2f3e9)
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.

![processed-28B6500B-BBC0-4A91-9F7F-55FD42A9083C](https://github.com/user-attachments/assets/63b79e85-6e86-4438-b18c-0f44fe19c3a2)

color stripes
![image](https://github.com/user-attachments/assets/576dd309-73ae-4b3d-9a01-0b93a6a981fd)
![image](https://github.com/user-attachments/assets/d88832a5-3f94-467c-9017-f62e7fcb3e3a)
![image](https://github.com/user-attachments/assets/04db0198-13bd-41ab-b7a8-9df35fef4618)
![image](https://github.com/user-attachments/assets/6a09c287-8547-4353-9f63-115c5318a786)





### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

![processed-3CAAAD42-3530-4D62-A645-65E38B7A5CF4](https://github.com/user-attachments/assets/88f2f267-7b83-4da9-9b67-dfc1c6497c1c)

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
My original idea was to split the screen up into square 60x80 pixels to form a grid of different colors then I would make the colors keep shifting one grid over contiously. To me this idea was very achievable and not too complex when I started, however as time went on there where a few factors that caused my to rethink my original idea for example time caused by a slow start and lack of access to the boards outside of class. In the end I managed to creating a black and white checkered pattern that alternates. 
### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
To achieve 

For my own project code I used aspects of both templates. I stared with the stripes code and modified it to diaplay a grid instead of stripes. I also adjusted the code to only use one if statement by creating an addtional row and column register that gets incremented by 60 and 80 respectivly. By using these registers in as part of the if statments conditions and incrementing them I don't need to write an if statement for each individual square on my grid.

I used the color cycle code to implement a wait and two states to the code in the first state the code alternates between black and white for each square. In the second state the colors swap black squares become white squares and vice versa.

![image](https://github.com/user-attachments/assets/f9f903d0-c7cf-4d6b-b809-cc1092bce483)

![image](https://github.com/user-attachments/assets/555b17bd-76c6-47b7-b024-2926d4ed76de)

![image](https://github.com/user-attachments/assets/991e8967-51e8-44b6-a689-31207f8de4aa)

![image](https://github.com/user-attachments/assets/0f7d9bd6-a859-46ec-9fe4-463606f2f64f)



### **Simulation**
![image](https://github.com/user-attachments/assets/f4a5ae1b-3dc8-4fea-97a3-5993621af0ad)


Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
![image](https://github.com/user-attachments/assets/025d7d50-9c1f-4d28-aec4-d050d58d5452)
![image](https://github.com/user-attachments/assets/4986a99c-51ff-4896-82cf-a1971168a189)
![image](https://github.com/user-attachments/assets/f1d2cf9b-97b7-47cf-8723-b79cb83f421c)



Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.
![processed-5974133D-C640-4B49-8A11-CE0A13A8515F](https://github.com/user-attachments/assets/5cfb9453-f5fd-4bba-9c31-f79f925ccbaa)
![processed-97377106-6E61-469B-B2B8-5B9D03F63449](https://github.com/user-attachments/assets/f22b5fc4-cbbe-4f38-8e16-a34c85d390f3)
![processed-FA5F6EB5-6C5E-40D0-AD3D-6E7DCAEFC484](https://github.com/user-attachments/assets/9264efcc-ed4b-462f-98cf-190f99cb69cb)

## **References**
[1] M. Lynch, “SoC”, Lecture, ATU, Galway, 2024.


## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
