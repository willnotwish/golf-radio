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

### On the bench: AM + FM aerial amplifier

Concentrating for the moment on AM, I turned my attention to the RH (horizontal) amp with the white connector. I removed the PCB and brought it to the workbench.

It was partially covered by what I assume is insulating varnish. This is not easy to remove. I used isopropyl alcohol and a lot of patience. Eventually I could make out some of the component markings. I managed to expose some areas of bare metal so I could try to reverse engineer the board a little with the help of my multimeter.

The amp is made by Blaupunkt. I could not find a circuit diagram online.

I can see that the central signal connector from coaxial input goes through some filtering to what looks like a DC power rail.

![alt text](file:///Users/nick/dev/electronics/car-radio/am-amp-overview.png)

### Back at the car: a broken pipe and damaged cables

I powered the amp via a separate 12V supply. It drew very little current. With the aerial connected, AM reception was fine.

I removed the head unit, then the aerial plugs and (carefully, for fear of shorts) checked the voltage at the connectors with the aerial connected. It was 10.3V DC. So it looks like the head unit is supplying phantom power OK. I'm not sure why it's 10V and not 12V but I won't worry about that right now.

I re-measured the voltage at the tailgate at the other end of the aerial cable. Still nothing.

I then started to trace the aerial cables back from the tailgate uner the trim. They pass through a rubber boot at the tailgate hinge, together with a ribbed rubber pipe carrying the rear screen washer fluid. I pulled the boot off and discovered that the pipe was split nearly in two! I think it had been leaking for some time, because the rear screen washer was always slow to operate.

I then noticed some cuts in the outer aerial cable covering. The damage was similar on both cables. I cut the cable back before the damage (head unit side) and measured the central conductor voltage with respect to the outer braid. Still nothing. I checked for continuity between the outer braid and the chassis. This was good (zero resistance).

This implies that the aerial cables are both damaged somewhere between the point where they disappear into the main body trim (after the tailgate) and teh head unit. The cables are hidden in the car behind numerous trim pieces. The thought of removing all these pieces to replace the cable is daunting.

### Water damage

My current theory is that the cable is damaged enough to prevent transmission of phantom power but not enough to stop the radio signal. Possibly there is some water damage caused by the leaky pipe. The broken pipe needs fixing; I have ordered a plastic insert which should cure the leak.

Maybe water has leaked into the cables. It is possible that the pillar which holds the cables fills with water when the rear screen washer is operated.

Thinking about it some more, it is likely that the phantom power supply provided by the head unit has a reasonably high output impedance (resistance, in this case, because we're talking about DC), in order for it not to become overloaded if the aerial cables are short circuited by accident.

I removed more trim at the rear of the car in order to investigate further. The aerial cables are composed of at least two sections, because there is a plug & socket pair behind the side upper trim near where the rubber boot fits. I can see areas of blue staining where the windscreen washer fluid has leaked. The damage does not look extensive, however.

I separated the intermediate plug and socket and measured 12V at the connector with the radio on.

The final cables passing through the rubber boot to the tailgate are faulty. I think washer fluid has got into the plugs.

### Cable replacement

The connectors are called Fakra, made by Amphenol, among others. Fachkreis Automobil auf Deutsch. The off white (they call it "curry yellow") and the white version are not interconnectable. They each contain a lug in a different position. I imagine the tooling is expensive.

Farnell, among others, [sell Fakra](https://uk.farnell.com/c/connectors/rf-coaxial-connectors-accessories/rf-connectors?connector-type=fakra-coaxial) but the version in my car seems to be Tyco. Mouser have a larger selection, and they sell made up cables, but they cost about over £25 each. Not worth it, I'd say.

The cable is made by Leoni. I think it is Dacar 300. This is a 50 ohm cable. As wer are only talking about a metre or so I think any old 50 ohm coax would work. It needs to be flexible though, because it will bend each time the tailgate is opened or closed.

Are there any cheaper alternatives? It would seem so. I could use plain old BNC connectors with a jointing piece, or SMA connectors which screw together (think satellite ot cable TV).

Alternatively I could just splice the two lengths together. I'd get some signal loss but I think that would probably be OK at relatively low RF.






