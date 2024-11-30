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

### **Template Code**
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
The first template (color cycle) used a switch statement to change the current state of thr code. Once the entire screen (480x640) was colored by writing a 12 bit value to the color register it would change state to a different color. The first four bit of the regiter was the red value, the middle four are the green value and the last four bits are the blue value. A count was used to wait a few seconds before changing the state so it would be visable to the human eye.

The stripes code uses two additional inputs row and col. These inputs represent the row and column of the current pixel. Another difference is that stripes has three 4 bit color registers instead of one 12 bit register. In stripes if statements are used to change the colors. When the col value is within a certain range it writes a four bit value to three color registers one for each of the three colors.

Both templates were similar to each other but also introduced new techniques to display an image. This was very useful when it came to creating my very own image.
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
My original idea was to split the screen up into square 60x80 pixels to form a grid of different colors then I would make the colors keep shifting one grid over contiously. To me this idea was very achievable and not too complex when I started, however as time went on there where a few factors that caused my to rethink my original idea for example time caused by a slow start and lack of access to the boards outside of class. In the end I managed to creating a black and white checkered pattern that alternates. 
### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
To achieve 
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

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
