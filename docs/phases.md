---
layout: page
title: Phases
permalink: /phases/
---

This page tries to document the different phases in the project. Phases will most likely overlap each other. This page is an early version and will probably change a lot.


Phase 1: Preparatory work
-------------------------
Some research that preferely should be done before everything else

 * Do a first version of a requirement specification
 * Figure out what kind of expertise that will be needed in this project
 * Research what similar projects exists
 * Research what other open source projects we could import code from
 * Document everything and make a simple web site


Phase 2: Platform implementation: Browser ("Proof-of-concept")
--------------------------------------------------------------
Boilerplate to run the software as a proof-of-concept in a browser (Via web assembly)

This will be really useful for research and development. People could try the software in their browser without the need to install potential malicious software on their computer. Even if the ability to route audio thru the browser will be limited it could still be really useful to experiment with the user interface.


Phase 3: Networking and community
---------------------------------
 * Start talking to people about the concept
 * Try to find other people that want to participate in some way


Phase 3: Documentation
----------------------
 * Start documenting in detail how things should work. This will be based on the requirement specification and act as a more detailed document on how the software should be implemented. This will partly be done in parallell with developing the software.


Phase 4: DSP library
--------------------
Make a platform independent C library with generic DSP functions. This could for example be the raw IIR and FIR algorithms, but should probably not include the code to calculate the coefficients for them.

### Suggested functions:
 * lin2log - Converts a linear value from a fader (0..1) to a value (0..1) that could be multiplied to a signal to get a experienced linear volume control.
 * log2lin - As lin2log, but the other way around
 * IIR filter
 * FIR filter
 * Delay


Phase 5: Filter reference implementation
----------------------------------------
 * Scrape the web for all possible implementation and algorithms used to calculate IIR and FIR filters
 * Put them together in a useful library


Phase 5: DSP Engine
-------------------
 * Uses the DSP library
 * Fully platform independent
 * Create basic building blocks like filters, equalizers, dynamic processors, delays, mixers etc
 * Lets the user connect these building blocks in a modular way
 * Exposes an API that could be used to let a GUI connect to the engine
 * Gives the user the full flexibility to create whatever preset (s)he likes, no matter if it's a loudspeaker management system (LMS), a digital mixer or something else.


Phase 6: Architectural work
---------------------------
 * Make more decisions on how the components in the system should work together
 * Make a better plan for how the API should work
 * Make some fancy schematics / graphs
 * ZeroMQ + OSC as API?
 * How does external devices communicate with the software/hardware
 * Plugins?
 * AES67?


Phase 7: Platform implementation: Linux
---------------------------------------
Boilerplate to work on a Linux system with ALSA, Jack, Pulseaudio or similar.

In this way the DSP engine could be used in a real application, as long as the latency requirements aren't to strict.

Distribute as an app image for Ubuntu? Snap? Docker? Raspberry Pi image?


Phase 8: GUI
------------
 * Start implementing a GUI that could connect to the DSP engine
 * The GUI will be built on Qt / QML
 * Could be compiled as a native application on Linux, OS X and Windows
 * Could be compiled into web assembly and run in a browser
 * Could probably be made into an Android or iOS app (Low priority, get a decent browser!)


Phase 10000000: Hardware implementation
---------------------------------------
To use the software to its full extend we need to make it run on a dedicated DSP with access to high quality analog and/or digital inputs and outputs. More info TBD.