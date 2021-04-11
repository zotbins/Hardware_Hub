# KiCad Workshop Tutorial

This tutorial will attempt to teach some of the basics of [KiCad](https://www.kicad.org/), a cross platform and open source electronics design automation suite. We'll be using three key features of KiCad to design a Printed Circuit Board (PCB) for our [Waste Watcher](https://github.com/zotbins/waste_watcher) circuit. The three key features are:

1. [Schematic Capture](https://www.kicad.org/discover/schematic-capture/)
2. [PCB Layout](https://www.kicad.org/discover/pcb-design/)
3. [3D Viewer](https://www.kicad.org/discover/3dviewer/)

This tutorial is really basic. For more details I suggest going through the wonderful documentation on the KiCad website.

## Table of Contents

1. Why is this useful
2. Prerequisites
3. The PCB we will be Designing
4. Let's Get Started: Circuit Design

## Why is this useful?

Once you finish designing a PCB, you can send it out to manufacturers to help you mass produce your design if you ever want to have your product scale. Using a tool like KiCad can really make your life easier when designing a production quality PCB.

## Prerequisites
- Basic Knowledge of reading circuit diagrams
- [KiCad 5.1.9](https://www.kicad.org/download/) Installed our your Computer

## The PCB we will be Designing

Below is the image of the PCB we will be designing.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/pcb_cad.png?raw=true)

Pretty cool right? Or maybe it's just me who thinks it's cool. I'm going insane.

*If you're wondering why is there only male pin headers on the PCB and where are the electronics such as the ESP32CAM and the Ultrasonic Sensor, don't worry about it for now. The male pin headers simply represents the soldering points for those electronics.*

## Let's Get Started: Circuit Design

Ok, let's start off with our circuit. What do we want in our circuit? Good question, we want:
- ESP32 CAM
- HC-SR04 Ultrasonic Sensor
- A two-pin connector to power the electronics above

Ok, now that we know what we want in our circuit, next it's usually up to the circuit designer to figure out how everything is connected together. I did that work for you in this circuit diagram here:

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/circuit_diagram.png?raw=true)

*For the batteries, just think of it as any 5V power source for now. It doesn't matter what type of power source we use as long as it is 5V DC.*

## Open Up KiCad!

Once you open up KiCad go ahead and create a new project. **File > New > Project**

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/open_kicad.png)

I named my project "tutorial" because I'm super creative.

When you create you're project it should already generate two files for you. A .kicad_pcb file a .sch file.

## Getting Familliar with the Schematic Layout Editor

We're going to first start off with editing the schematic file. So go ahead and click on the **Schematic Layout Editor** circled in yellow in the image below.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/open_schematic_editor.png)

Next, make sure the following tile buttons on the left are selected. This will make sure you have the same setup as me as you are following this tutorial.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/schematic_editor_intro.png)

On the right of the image above. I want you to just familiarize yourself with some of the tools we will be using:
1. Select Item
2. Place Symbol
3. Place Power Port
4. Add Wire
5. Place no connection Flag
6. Place Text

Next, I want you all to familiarize yourself with the list of available Hotkeys are shortcuts. As you build more projects, knowing the list of Hotkeys will help you design PCB's faster. To view the Hotkeys list go to **Help > List Hotkeys**. If you are on Windows you can do **Ctrl + F1**.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/hotkey_list.png)

Some common hotkeys I use are :
- **R** to rotate
- **C** to copy

## Adding your Components
For our circuit we will be placing the following components onto our schematic. These are the elements that will physically go onto your PCB. We are going to add the following components:
- Screw_Terminal_01x02
- Conn_01x08_Female
- Conn_01x04_Male

Click on the **Place Symbol** Icon on the top right and then click anywhere on the canvas. Search up each of the following components listed above and place them one by one. Use the copy and rotate tool to try to arrange the schematic like in the image below.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/place_components.png)

Next, let's go ahead and add some text by clicking on the **Place Text** tool and labeling the components as I have done so in the image below.

## Making the Connections
Next, up we're going to make some connections. Go ahead and connect the following pins as in the image below. For the rest of the pins that are not connected to anything we are going to do a **place no connection flag**
![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/schematic_wiring.png)

If you notice in the image above. There are a bunch of question marks next to each component. So here's what we are going to do. We're going to annotate and assign all those question marks to numbers. On the top bar, click on the **annotate schematic symbols** button as show in the image below.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/annotate_schematic_symbols)

## Annotating Schematic and Checking the Electrical Connections
Just go ahead and leave everything as default when the Annotate Schematic window pops up and click annotate.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/annotate_schematic_window.png)

Now all those question marks should be replaced with numbers! Yay!

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/annotation_numbers_shows.png)

Next we are going to check if all the electrical connections are ok. That means we are checking, is everything connected?

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/electrical_rules_check.png)

Just run it and you should get no errors, because we connected everything in our schematic! This tool is pretty useful for when you have a huge complicated circuit.

## Generating A Netlist
For the sake of this tutorial I won't go into detail of what a netlist is. Just know that it is basically a file that is used to store information about the connections so that our PCB layout editor will know what to do.

Click on the **generate netlist** button as shown in the image below.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/generate_netlist_butt.png)

Just leave the default setting and click **OK**.

## Assign PCB footprints to schematic symbols

Now we have all the parts of our schematic. Now in order for us to transition into our PCB layer, we need one more step. Which is assigning the footprints for each schematic symbol, or component. What does that mean? Well, each symbol needs to have the exact hole size, pad size, etc. in order to be made into a PCB. That's what we're doing here!

Click on the **assign PCB footprints to schematic symbols** button as shown below.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/assign_pcb_footprints_to_schematic.png)

We're going to go through the middle column one by one.

![img](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/symbol_footprint_assignment.png)

A few tips.
- Use the **Footprint Libraries** column (leftmost) to help you narrow down the footprints you want
- Use the **Filtered Footprints** to find and select your specfic footprint
- You can view your footprint by right clicking on it
- You can also view the footprint in a CAD model

Now let's save everything and go back to the main KiCad Window.

## Creating your PCB!
Click on the **PCB Layout Editor** button as shown in the image below.

![](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/pcb_layout_editor_butt.png)


You want to load the netlist by clicking on the **Load netlist** button on the top. Then click ok and add the footprint to the PCB layout by left-clicking on the black canvas once.

![](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/pcb_layout_editor_load_netlist.png)

First, we want to move the two 1 by 8 male header pins to exactly 22.86 mm apart, as shown in the ESP32CAM datasheet.

![](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/esp_32_cam_datasheet.png)

Use the grid points and the dimension tool to help you space it out accordingly. Also rotate and place the other footprints according to this picture.

![](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/rotate_and_place_footprints.png)

## Edge Cut
In the image above, do you see that yellow square outline? You shouldn't have that yet, since I skipped ahead. That yellow square outline is called the edge cut. It will determine the shape and size of your PCB.

First, change your layers to **Edge.Cuts**, then select the add graphical lines button on the right side panel. Finally, draw the square around your PCB footprints.

![](https://github.com/zotbins/Hardware_Hub/blob/main/kicad_basic_tutorial/imgs/edge_cuts.png)

## Route Tracks
This will flex our creativity here. We need to set the exact copper traces for connecting the PCBs together.

Go back to the **F.Cu (PgUp)** Layer and click the **Route Tracks** button on the right side panel.

## Add Text
Use the add text tool to add your text. Make sure that it is on the **F.SilkS** Layer.

## View in 3D Mode 

**view > 3D-viewer**

## You're Done!
Thanks.
