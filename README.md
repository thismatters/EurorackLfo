# Low Frequency Oscillator

The Low Frequency Oscillator (LFO), as the name implies, oscillates at a low frequency. This implementation operates over a wide frequency range enabled by a rate knob and switch, offers access to 4 wave shapes simultaneously, and can be synced with an external clock.

The circuit here is based on the [Yusynth LFO 2](https://yusynth.net/Modular/EN/LFO/VC-LFO2.html) with minor tweaks to make it more Eurorack friendly. The changes I've made are thus:
* Selected resistors appropriate for +/-12V rails,
* Added polarity protection so that a backward power header doesn't fry anything (twin series schotty diodes: BAT54SL),
* Selected a modern dual NPN diode package for matched transistors,
* Full surface mount design.

The Yusynth page is a treasure trove of information about this circuit that I am too amateur to claim as my own; please read that outstanding page before using this circuit. The page provides many details and other implementations of this circuit that you may find suitable.

The KiCAD project here uses the library/footprints [found in my companion repo](https://github.com/thismatters/EurorackKiCAD).

## Width

6hp on a standard 3U rack.

## Inputs

Potentiometer labeled `rate` controls oscillation rate along with toggle switch to flip between `fast` and `slow`. Single `cv` input allows modulation of rate, which is augmented by a potentiometer labeled `cv`. Potentiometer labeled `pwm` adjusts the duty cycle for the square wave output. Oscillation can be synced to an external input by way of the `sync` input.

## Output

Four outputs, one for each of the following waveshapes: Sine, Saw, Triangle, Rectangle.
An LED visualizes the square wave output.

## Adjustment

You'll need an oscilloscope.

1. Set the `cv` knob to minimum.
1. Set the range switch to `slow`.
1. Set the `rate` knob to minimum.
1. Adjust RV4 until the LED blinks on every 10 seconds (0.1Hz)
1. Set the `rate` knob to maximum.
1. Connect the oscilloscope to the SAW output (sharp rising edge, ramp to low).
1. Adjust RV6 until the SAW output covers the -5V to 5V range.
1. Connect the oscilloscope to the TRIANGLE output.
1. Adjust RV7 until the TRIANGLE output covers the -5V to 5V range.
1. Connect the oscilloscope to the SINE output.
1. Adjust RV7 to perfect the SINE shape.
1. Set the range switch to `fast`.
1. Connect the oscilloscope to the TRIANGLE output.
1. Adjust RV5 to get a symmetric wave shape.


## Vendors

There are part numbers in the [BOM](lfo.csv) for many of the parts (not for basic passives though) at the following vendors:

* [Mouser](https://www.mouser.com): Needs no introduction. Get your ICs from here (or [digikey](https://www.digikey.com)).
* [Tayda Electronics](https://www.taydaelectronics.com/): Good supplier for passive components; audio jacks, and potentiometers. Their audio jacks are slightly smaller than the thonkiconn from thonk.
* [Love My Switches](https://lovemyswitches.com/): Has [really good knobs](https://lovemyswitches.com/anodized-aluminum-knob-the-lo-fi-1-4-smooth-shaft-12-5mm-od/) to go on those potentiometers!
* [OSHPark](https://oshpark.com/): Fast and (relatively) cheap PCB manufacturer. I haven't done a prototype run yet... stay tuned.
