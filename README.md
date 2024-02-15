# Loss of AM radio reception

Last week I noticed I could not listen to AM sport (BBC Radio 5 Live) in my Mk 6 VW Golf, which has a factory fitted stereo. No AM stations could be received. FM was reasonably OK, although not as good as usual (it seemed to fade in and out a bit, but it's hard to say exactly). AM was definitely duff.

We'd had some cold and then very wet weather recently. It's been a very wet winter here in the UK so far.

I think this had happened once before, and seemed to fix itself. But I'm not sure.

## Initial investigation
I didn't know where the aerial (antenna) was in the car. It turns out it's in the rear windscreen, in the hatchback tailgate.

Pulling off interior trim above the rear screen revealed two small PCBs, one on each side (left and right) just above the screen, each connected to an embedded aerial via a thin black wire. The embedded aerial wires themselves were separate from the rear screen demister, with no electrical or mechanical connection between them in the glass.

The aerials were completely different shapes. One was a horizontal straight wire running the full width of the screen, the other a narrower M-shaped or W-shaped affair with three vertical legs pointing downwards.

Above the screen, what looked like thin (5mm diameter) coaxial cables coming from the wiring loom and terminated in small plastic plugs (one white and one off white) were plugged into the PCBs: the white to the RH board and horizontal aerial, the off white to the LH board and vertical aerial.

The PCBs were different, but it was easy to see that they each contained a range of SMD passive components including resistors, capacitors and inductors, together with what looked like transistors and diodes. No chips though.

My working assumption was that these small boards (about 100 x 20mm) were aerial amplifiers.

I struggled for a while trying to understand how these amps were powered.

## Amplifier power supplies

After much internet searching I found that a common way to power amplifiers like these is via "phantom power". 12V (or less, possibly) is provided by the radio ("head unit") applied to the central (signal) conductor of the aerial coaxial cable. I don't know how it's connected at the radio end but DC must be blocked (by a blocking capacitor maybe) to stop it getting into the radio's tuning circuitry.

> As an aside, phantom power seems to be the reason why there are so many reports online of people installing non-OEM replacement head units only to find that the radio receiption is worse than with the original. If the replacement head unit does not supply phantom power, the aerial amplifiers won't work and the signal strength will be much lower at the radio input.

## Fault finding

With the radio on, my multimeter (on DC) read only a few tens of millivolts between the central conductor of the coax and its shield. I would have expected 12V or thereabouts to be present.

When I poked a screwdriver into the RH (white) coax connector I could hear 5Live on 693m AM through the radio, loud and clear. Doing the same to the LH (off white) connector made no difference to the AM signal, although it worked on FM. To confuse matters further, I found that repeating the RH trick with the screwdriver also helped on FM.

So it appears that the RH aerial is for AM _and_ FM, but the LH is only for FM.

> I searched some more on the internet and found some talk of _diversity_. It appears to be a mechanism (for FM only) where the head unit will select the best signal from two or more ampliifiers, depending on reception conditions.

Concentrating for the moment on AM, I turned my attention to the RH (horizontal) amp with the white connector. I removed the PCB and brought it to the workbench.

It was partially covered by what I assume is insulating varnish. This is not easy to remove. I used isopropyl alcohol and a lot of patience. Eventually I could make out some of the component markings. I managed to expose some areas of bare metal so I could try to reverse engineer the board a little with the help of my multimeter.

The amp was made by Blaupunkt. I could not find a circuit diagram online.

I can see that the central signal connector from coaxial input goes through some filtering to what looks like a DC power rail.

![alt text](image.png)



