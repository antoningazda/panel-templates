# Eurorack Panel Templates for KiCad

Have you ever wanted to create your own faceplate for your existing modules or are you making your own Eurorack modules? Or blank panels?

I created these templates, which you import into KiCad EDA Suite - an open source and free program to design PCBs (printed circuit boards) - from which you can make the panels.


## How do I get this thingy to work?
- install [KiCad](http://www.kicad.org/)
- download this repository (as .zip or clone it)
- open KiCad and go to File -> New Project From Template -> User Templates
- go to the written folder and paste all of the downloaded folders into this repostiory

Make sure your folder structure looks like this:
- template
    - 3U_02_Blank
    - 3U_04_Blank
    - etc.

Now to create a new panel, go again to KiCad -> File -> New Project From Template -> User Templates

You should see all of the available blank panel templates. Click on one, save the KiCad project.

You are seeing two files in this project. The .kicad_pcb is the one you want. The .kicad_sch is there by default and is not needed in this case.

Have fun!


## What the hell is HP
1HP is 5.08mm with the sizes of panels being rounded multiples of HP. Check out [doepfer.de](https://doepfer.de/a100_man/a100m_e.htm) for a better explanation.

### Creating a design
- Open KiCad -> File -> New Project From Template -> User Templates
- Select The HPs and save the project
- Open the .kicad_pcb file

You should be seeing a rectagle with some oval or circular holes.
Have fun creating your design.

#### Holes
- creating holes by drawing shapes on the Edge.Cuts layer
- creating holes with free-standing vias
- creating holes with new PTH and NPTH footprints - you can start by modifying the existing oval holes

#### Graphics
To create good looking graphics, you need to understand the material you're working with.

A double sided PCB - the most common one consists of these layers in this order:
- Front Silkscreen
- Front Solder Mask
- Front Copper
- FR4 Dielectric material
- Bottom Copper
- Bottom Solder Mask
- Bottom Silkscreen

By combining designs on all of these layers, you can create some pretty gnarly lookin stuff.

#### FR4 Dielectric material
This is most of the time a yellow-brownish board. It passes some light through. The most common thickness is 1.6mm.

#### Copper
A really thin layer of copper, which is originally for connecting electrical signals on a PCB. When you are creating panels, you can create a copper design and leave it exposed (more about this in the Solder Mask section) to have a gold or silver color. Also if you leave this copper under a solder mask, you can create textures and designs, which are only a little bit visible but can be really nice.

#### Solder Mask
By default, the copper and FR4 layers are protected by a solder mask layer. Usually offered colors are green, black, blue, yellow, red, even purple etc.

#### Silkscreen

The level of detail, you can get manufactured on a silkscreen is lower than the solder mask.

## My workflow for creating Eurorack panels
Creating designs in KiCad isn't really a great experience, so for more complicated stuff, use Inkscape or other vector based editors.
For more info, checkout my [video](http://www.youtube.com/).

Create your artwork with dimensions set by the Blank panel size.
When you are done with creating the artwork in a vector format.
For this, you can use these SVGs with the right sizes.

Make sure you have the right things grouped together, white artwork, black background

Create a frame around the artwork - for example 100x150

Export it all at 2500 DPI, no other settings, png

Open KiCad Image Converter

Import png, choose size, layer and Negative inversion - frame should be black

Export to clipboard, position

Edit footprint, delete frame

Add copper fill etc

File -> board setup - choose colours
Look at the 3D view, if everything looks good
Export using the fabrication toolkit
Rename the gerber.zip - check size - under 10 MB
Check using a gerber viewer

### Ordering the PCBs
I usually order from [JLCPCB](https://jlcpcb.com/).
If you use another company, the settings should be pretty similar.

Go to jlcpcb.com
Import the PCB
Check the size if its correct
Set the number of PCBs you want
Set Mask color etc.