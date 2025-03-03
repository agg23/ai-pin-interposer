# Humane AI Pin Interposer

A device aiding in the connection to the USB pins on the back of the AI Pin, for purposes of ADB access.

> [!NOTE]  
> At the time of writing, access to the USB pins doesn't actually allow us to do anything. Only go to this effort if you're interested in playing around.

![](images/Docked%20Pin.jpg)

Dock Body             |  Probe Holder
:-------------------------:|:-------------------------:
![](images/Dock%20Body.png)  |  ![](images/Probe%20Holder.png)

## Instructions

### Requirements

- [ ] 4x P50-B1 test probes - These are 0.68mm diameter, 16.55mm fully extended spring probes. You can easily find them en masse on places like Amazon, and you probably want more than just 4 as they are very easy to break. - I purchased https://www.amazon.com/dp/B07RKMN3TG
- [ ] Some form of USB connectivity - You could just splice a USB A cable, or you can buy USB breakout boards like https://www.amazon.com/dp/B0D12KX74M
- [ ] Small gauge wire - I use [22AWG solid core](https://www.adafruit.com/product/1311) - You're soldering to something 0.7mm thick and you can't waste too much space
- [ ] 2x M3 12mm bolt - Smaller lengths will likely work.
- [ ] Screwdriver for M3 bolts
- [ ] Access to a 3D printer
- [ ] Soldering iron and solder
- [ ] Adhesive like hot glue or tape
- [ ] (Optional) 2x small steel paperclip (or another ferromagnetic bar)
- [ ] (Optional) Multimeter

### Assembly

1. [Download the latest version of the parts](https://github.com/agg23/ai-pin-interposer/releases/latest) (`Dock Body.stl`, `Probe Holder.stl`). Print the parts. Unless you have really good bridging you will need supports on the cradle. Given the small dimensions in the pin holder, you may want to tweak your settings to run slower, enable retraction on small gaps, etc. I have allowed for some dimentional inaccuracy and wall expansion, but this may cause problems for you. I printed at 0.2mm for everything.
2. Solder a wire to each of your 4 pins. I recommend trying to only have the solder and the wire on one side and not to have it spread around the pin. Do not obstruct the bottom of the pin; it is used for accurate positioning.
   
   ![](images/Soldered%20Pins.jpg)

3. Place each pin into one of the 4 slots on the pin holder. There should be some resistance to the installation, and you may have to push it in with a fingernail or a hard tool like a spudger or screwdriver (be careful, the pins are easy to break/bend). The end of the pin MUST rest on the bottom ledge of the pin holder; this accurately positions the pin for interface with the AI Pin.

   ![](images/Pin%20Holder.jpg)

> [!NOTE]  
> You can theoretically solder to the pins at this stage (assuming you didn't in step 2), which would allow you to slide the pins the entire length of the holder, which seems to work nicer.

4. Secure the position of the pin through some form of adhesive. Hot glue should be adequate. Be aware of the clearances of the holder in the main dock part. The pins must all rest at the bottom of the holder cavity.

   ![](images/Glued%20Pins.jpg)

5. Solder your wires to your USB connection method. When the "hu.ma.ne" text is positioned at the bottom of the AI Pin, the pinout from top to bottom is:
     * VCC - Red
     * D- - White
     * D+ - Green
     * GND - Black
  
    <img src="images/AI%20Pin%20Pinout.jpg?raw=true" width="512">

6. Slide the pin holder into the dock, being carful not to damage or put preasure on the test probes. The probes should extend out of the hole in the top of the dock by ~1mm. Be careful not to damage your wires or soldering.

   ![](images/Installed%20Holder.jpg)

7. Screw the two M3 bolts into the holder and dock. The holder should sit very slightly beneath flush with the bottom of the dock.
8. Test continuity of your wires and pins with the multimeter. Verify there are no shorts and that there is a direct path from your USB pin to the probe in the interposer.
9. Align your USB breakout board (if you have one). There are notches for holding a standard thickness PCB. You probably want to apply the same adhesive here.
10. If you're installing magnetic material (paperclips, some other metal), you can do so now. This will help hold your Pin on the probes to prevent it from unseating.

![](images/Docked%20Pin.jpg)

Enjoy your Humane AI Pin interposer. You can now connect USB to your computer and place your AI Pin into the dock. If you have done everything correctly, then running `adb devices` should produce the following output:

```bash
> adb devices
List of devices attached
[random-device-id]        unauthorized
```

### Use

Currently we do not have ADB access, so there's not much of a usecase. However, the proceedure goes like this:

1. Expose the USB pads
   1. The four USB pads on your AI Pin are hidden behind the crescent moon logo in the back middle of the Pin.
   2. We don't currently have a recommend way of removing this sticker. Isopropyl alcohol, heat, and a plastic spudger are recommended.
2. Connect the interposer to your computer using some form of USB
3. Carefully place the AI Pin into the dock. The Pin's camera MUST face away from the hole at the back of the interposer (where you probably attached a USB port). If you insert the Pin in the opposite direction you will be reversing the USB pins, which is a bad idea.
4. Connect to ADB. To be continued...


### FAQ

#### My connection is finicky

Make sure the Pin is pushed down into the dock all the way. If you have not installed magnetic material, you may wish to do so. You can also clean your Pin's pads with isopropyl alcohol - the tiniest contamination can cause issues since they're so small.
  