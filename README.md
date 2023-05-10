# Octolamp
A 3D printable, GitHub infused, wifi enabled smart light powered by [WLED](https://kno.wled.ge/) and compatible with [Home Assistant](https://www.home-assistant.io/)

<img src="images/IMG_9122.jpg" alt="Picture of a fully constructed Octolamp" width="600" />

### Components

To build the Octolamp, you'll need access to a 3D printer, soldering iron and the following components:

- [Black PLA Filament](https://amzn.to/3CTo54W) (for the base) - [[US](https://amzn.to/3CTo54W)] [[UK](https://amzn.to/3w7fCXX)]
- [White PLA Filament](https://amzn.to/3GKObIz) (for the inner body and reflector) - [[US](https://amzn.to/3GKObIz)] [[UK](https://amzn.to/3XBNVSM)]
- WS2812B LED Strip, 60 LED's per meter, just under 2m worth but usually sold in spools of 5m - [[US](https://amzn.to/3XwWnCT)] [[UK](https://amzn.to/3QKIzm6)]
- ESP8266 NodeMCU D1 Mini Module (or similar clone or other WLED compatible device) - [[US](https://amzn.to/3koQwS0)] [[UK](https://amzn.to/3kmp473)]
- USB lead (Micro or Type-C depending on the model of D1 Mini you have purchased, usually Micro-USB) [[US](https://amzn.to/3CTpqsl)] [[UK](https://amzn.to/3XxulY2)]

If you are looking for recommended links to buy these somewhere locally then please see [Purchasing Links](#purchasing-links) below.

Assuming you already have the PLA filament and a spare USB lead, the construction cost for the electrical components works out at <$20 per lamp.

### Instructions

The lamp itself consists of 3 printable parts, printed in regular PLA on a printer with greater than a 210mmx210mm print bed (the popular [Ender 3](https://amzn.to/3CRwSUQ) or [Prusa i3](https://amzn.to/3ZxlHdI) should both work, this was tested with an [Ender 3 S1](https://amzn.to/3CRwSUQ))

All models are designed to be printed without supports. I used a 10% gyroid infill.

The 3 components are:
- [Black base](models/octolamp_black_outer.stl)
- [White reflector](models/octolamp_white_reflector.stl)
- [White inner](models/octolamp_white_inner.stl)

When constructed they snap-fit together as shown.

<img src="images/octolamp-xsection.png" alt="Cross-section of the Octolamp" width="600">

When you have assembled your 3d printed parts you can begin contruction.

<img src="images/IMG_9083.jpg" alt="Component parts for the Octolamp build" width="600">

#### Step 1 - Install WLED

First, you'll want to flash your D1 Mini device with [WLED](https://kno.wled.ge/) and then configure it to connect to your WiFi network. the [WLED project](https://kno.wled.ge/) is an open source firmware for many embedded devices that allow you to create beatiful LED displays and network them together. There are controller apps for iOS and Android and it is also fully compatible with the popular [Home Assistant](https://www.home-assistant.io/) software meaning that once built you can control your lamp from anywhere and build any number of automations so that it flashes when someone stars your GitHub repo, changes color when your build breaks or switches on and off with your office lights. 

Note that for large LED displays you can need significant power, you'll also likely want a controller that has a level shifter to send a reliable 5v signal for data to your LED strip. However as we're only powering 100 or so LED's you can get away with pulling the power and data directly from the pins of an inexpensive D1 Mini.

The quickest and easiest way to install WLED on your D1 mini is to plug it into the USB socket on your computer and then visit the [WLED web installer site](https://install.wled.me/).

- [https://install.wled.me/](https://install.wled.me/)

Flash the device with the latest build of WLED, configure the device to connect to your WiFi network and then you are ready to go.

#### Step 2 - Stick the LED Strip to the White Inner

The White Inner component acts as the guide for the flexible LED strip as well as the diffuser for the lights which are stuck to the side. You only need the +5v, G and Data pins so snip off any additional power lines that might come with your strip or solder on new wires to the strip if yours didn't come with pre-soldered wires.  Remove the plastic from the adhesive backing and start sticking at the bottom middle, looping around the outside then over to the inside and finally around the central part. Cut at the marked lines when you are finally done.

<img src="images/IMG_9090.jpg" alt="Path of the LED strip" width="600">

When finished you should have around 100 LED's in your lamp, but it's worth counting at this point as you'll need the exact number later (depending how I did my sticking I've used anything from 99 to 105)

#### Step 3 - Add the Reflector
Next, feed the wires through the hole in the reflector. If you are using plugs to connect your strip and controller then you can do this at any time but if you are soldering the strip directly to the controller then you need to do it now.

#### Step 4 - Solder LED Strip to D1 Mini
Rather than use plugs, I solder my strip directly to my D1 Mini, but you can use connectors if you wish.  Connect the +5v and G lines to the corresponding pins on the D1 Mini and the data line to D4 (just above the +5v and G pins).

<img src="images/IMG_9125.jpg" alt="The wires from the LED strip soldered to the D1 Mini" width="600">

#### Step 5 - Assemble
Next up, feed your USB lead through the back of the black outer body and connect it to your D1 Mini.  Place the D1 Mini in the small inlaid portion in the center of the lamp. Then drop in the relfector and finally place the white inner onto it, and snap fit into the black outer body. This should force the white reflector down which then also secures the electronics in place.  Power up your device and at this point about half of your LED's should be glowing orange.

#### Step 6 - Connect to WLED and configure display
All the rest of the configuration is configuring WLED for your device.  Connect using the IP address from installation time, then go to Config, LED Preferences and update the Length of the LED strip to be the number of LED's you installed in Step 2 (for me that's typically between 99 - 105).  When you press Save the rest of your LED's should be glowing orange.

You can now configure your light display with the amazing flexibility of WLED. Once you have your favorite setting, store it as a preset and then go back to the LED Preferences and scroll down to Defaults where you can set which preset it displayed when the lamp is powered on (i.e. Preset 1 instead of the default orange in Preset 0)

#### Step 7 - Share your makes!
That's it!  You are now done but I'd love to see pictures of your built and assembled lamps.  Feel free to share pictures of them [in discussions here](https://github.com/martinwoodward/octolamp/discussions) or on social media and tag me on them [martinwoodward@hachyderm.io](https://hachyderm.io/@martinwoodward) on Mastodon or [@martinwoodward](https://twitter.com/martinwoodward) on Twitter and other socials

### Notes

I've tried to make the model super flexible so it includes ways to mount the lamp to a wall and different USB cable routing options.

The copyright for the invertocat logo belongs to GitHub. For acceptable use of that logo see the [GitHub logo usage guidelines](https://github.com/logos).

### Purchasing Links
The fun part of this project is making it yourself, the lamp isn't officially sold pre-assembled (and the license is non-commercial use only so they shouldn't be doing that).  But if you want to buy the components to make this them then the following components have been used and recommended by community members. Note some of these links make use of affiliate programs but they should always be linking to components the community trust.

#### United States

- [Black PLA Filament](https://amzn.to/3CTo54W) (for the base)
- [White PLA Filament](https://amzn.to/3GKObIz) (for the inner body and reflector)
- [WS2812B LED Strip, 60 LED's per meter](https://amzn.to/3XwWnCT), just under 2m worth but usually sold in spools of 5m 
- [ESP8266 NodeMCU D1 Mini Module](https://amzn.to/3koQwS0) (or similar clone or other WLED compatible device)
- [Ender 3](https://amzn.to/3YjmLkD) S1 3D Printer

#### United Kingdom
- [Black PLA Filament](https://amzn.to/3w7fCXX) (for the base)
- [White PLA Filament](https://amzn.to/3XBNVSM) (for the inner body and reflector)
- [WS2812B LED Strip, 60 LED's per meter](https://amzn.to/3QKIzm6), just under 2m worth but usually sold in spools of 5m 
- [ESP8266 NodeMCU D1 Mini Module](https://amzn.to/3kmp473) (or similar clone or other WLED compatible device)
- [Ender 3](https://amzn.to/3xcwoW9) S1 3D Printer

#### Singapore
- [WS2812B LED Strip, 60 LED's per meter](https://s.lazada.sg/s.0zKLk), just under 2m worth but usually sold in spools of 5m 
- [ESP8266 NodeMCU D1 Mini Module](https://shp.ee/9gxtxxn) (or similar clone or other WLED compatible device)

### Link to these instructions
<img src="images/octocat_QR_code.png"  width="648" height="655" alt="QR Code to these instructions" />

Instructions: https://github.com/martinwoodward/octolamp

