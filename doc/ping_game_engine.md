Programming with the Ping Game Engine
-------------------------------------

**Understanding the main interrupt loop**

The heart of the Ping Game Engine lies in IRQ interrupt routines. This allows for accurate timing necessary to keep the game running smoothly. There is a different interrupt routine for each mode of the program: Main Menu, World Update, and Screen Update.

When the game begins, the IRQ vector is set to point to the World Update routine. This will update everything about the game world, such as enemies, sprites, the player, background scroll, and anything to prepare the Screen Update to draw. The World Update routine then sets the IRQ vector to the Screen Update, which updates the screen as needed before resetting the IRQ vector back to the World Update. These two routines alternate back and forth until the game ends or is paused.

Within the World Update routine are different modes of operation, depending on the state of the game. These handle fades, general game updates, etc, and are discussed in more detail in the "Game Modes" section.

**Game Modes**

**Update Routines: *World Update* and *Screen Update* **

The World Update and Screen Update routines go hand in hand in ensuring the smoothest gameplay possible. The World Update routine must prepare Screen Update to set sprite positions, perform page-flipping and smooth scrolling, among other graphics-related tasks. Since Screen Update must update the entire screen in a small amount of time to avoid screen flicker, World Update must do most of the time-expensive tasks. Specific tasks are outlined below.

***World Update***

World Update must perform the following tasks to get Screen Update ready
for drawing a frame of animation:

1. Read input (joystick, keyboard)
2. Update player/enemy sprites (positions, images, attributes)
3. Update screen smooth scrolling position and rough scrolling position
4. Update player/enemy sprite positions to reflect new scroll delta
5. Copy level data to offscreen page
6. Copy color data for current frame to an array

After these tasks have been completed, World Update sets the next interrupt to point to Screen Update.

***Screen Update***

To run as quickly as possible, most of what Screen Update does is to simply copy data set up by World Update to screen memory, all computations having been made previously. This involves the following tasks:

1. Copy color data prepared by World Update to VIC color memory
2. Set VIC smooth X scroll register
3. Set screen memory to point to the offscreen page (page-flip)
4. Move all sprites to desired positions

The Screen Update will then set the next interrupt to point back to World Update, and the entire Update process is repeated for another frame.

**Data Structures**

**Naming Conventions**

To distinguish between different types of data, there are certain
conventions for how their names are written.

Variables: variableName or variable\_name

Constants: CONSTANT\_NAME

Subroutines: SubroutineName

Block of data: (same as Subroutines)

Zeropage Vars: (same as variables)

Record: name**\_record**


**Records**

Records are like *structs* in C. They are collections of data that provide a simple way of keeping related items grouped together. In Ping, the naming convention for a record with the name 'person' would be person\_record , and a member 'age' of person\_record might be p\_age , or per\_age (notice the first letter is lowercase). The reason you wouldn't write person\_age is to distinguish between the record itself and the members of that record. Here's an example of a record in an assembly file:

person\_record:

per\_age
dc.b 0

per\_sex
dc.b 0

per\_job
dc.b 0

If you need an array of records, replace all instances of 'dc.b 0' with 'ds.b ***x***', where ***x*** is the size of the array.

