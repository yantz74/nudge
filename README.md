## Nudge - automatic nozzle alignment, made easy

*One microstep for a probe.  One giant leap for multiple-head-kind.*

**tl;dr:** Manual calibration sucks, but with this probe, you can get fresh, fully-automatic offset alignment on every print.

| ![alt_text](Renders/another_iso_crop.png) | ![alt_text](Renders/electrical_path_crop_2.png) | ![alt_text](Images/both_iso_small.jpg) |
| - | - | - |

## Nudge in action! >>>  ![alt_text](Videos/Probing.gif)

**Nudge** is a low-cost, high-repeatability probe to enable automatic nozzle alignment on multi-toolhead 3D printers (IDEX, Dual Gantry, and Toolchanger).  

It’s like a Z endstop, but can be nudged in X and Y directions, too.  

When the metal probe tip is nudged by the nozzle, a button-head screw in the Wobbler lifts off slightly from the smooth socket-head screws in the Mount, breaking the electrical path.  Software nudges the nozzle against the probe in Z, then X, and Y, repeating this process to determine offsets between any number of toolheads.

When multiple heads can work together, with perfect alignment, multi-color and multi-material prints look great!  

Here's a sample from Ankurv ([3DUnplugged]()), whose [Daksh v2]() toolchanger uses Nudge to ensure alignment betweeen heads:

| ![](Images/bender.jpg) | ![](Images/bender_zoom.jpg) | ![](Images/bender_zoom_2.jpg) |
| - | - | - |

Here's a sample from Zruncho of some Voron cubes.  The full-size cube would have been perfectly aligned if the nozzle was cleaned first!

| ![](Images/gems_small.jpeg) | ![](Images/cubes.jpeg) |
| - | - |

You can print, build, and deploy a Nudge in as little as one hour, with only $10 in parts:

![](Images/all_parts.png)

Build it using the instructions in this repo, or with [this video](https://youtu.be/6eRomxUo7TI).  Yes, it used to have a 'y' at the end of the name.  Note also that this video is slightly out of date - for example, now, Nudge has a straight-through JST, rather than a right-angle JST, and plastic to ensure the horizontal screws stay aligned.

[![](Images/yt_thumb.png)](https://youtu.be/6eRomxUo7TI)

## [> > > Watch build](https://youtu.be/6eRomxUo7TI)

Nudge is highly repeatable; here's an early sample of probing accuracy from a 10-sample run:
```
Printing stats for x:
  Range: 0.0023
  Standard Deviation: 0.0010
Printing stats for y:
  Range: 0.0016
  Standard Deviation: 0.0007
--- 95.45 seconds total; 19.09 per iteration ---
```

Definitely usable!  Z is not quite as good, though, so you may still want to keep that endstop switch around for determining Z offsets.

**Firmware Support**: Nudge works great on CoreXY with nozzle alignment code from [Viesturz' klipper-toolchanger](https://github.com/viesturz/klipper-toolchanger) repo, but other kinematics should be possible with Klipper tweaks.

| Printer Type | Klipper Kinematics type | Test/Support Status |
| - | - | - |
| Toolchanger | CoreXY | :white_check_mark: |
| IDEX | Hybrid CoreXY w/ Dual Carriage | :white_check_mark: (as of 2024-06-19) |
| IDEX | CoreXZ Dual Carriage | :x: Fails during probing |
| DG | Dual Gantry CoreXY | :x: Fails during probing |

Related patches:
* [RCF's klipper-toolchanger fix for IDEX](https://github.com/viesturz/klipper-toolchanger/pull/23/commits)
* [Frans-Willem's Klipper PR for IDEX](https://github.com/Klipper3d/klipper/pull/6486)

No, fully-automatic offsets are not yet supported.  If you figure this out, please share.

**Hardware Support**: Mounting options for many common multi-toolhead open-source printers/mods are included here, including Trident, Tridex, Tri-Zero, Double Dragon, Dueling Zero, V2, Micron, F-Zero, and more.  One almost certainly fits!  *Unlike other options, a Nudge can be permanently mounted within a hot chamber, with as little as 6mm overtravel.*

**Parts to print**:

| Mount | Wobbler | Floating Base (optional) | Indexed Base (optional)  |
| - | - | - | - |
| ![](Renders/mount_iso_2_trim.png) | ![](Renders/wobbler_iso_trim.png) | ![](Renders/floating_base_iso_trim.png) | ![](Renders/indexed_base_iso_trim.png) |

**Mount options:**

| 2020 | 1515 High (sticks up) | 1515 Low (sits low) |
| --- | --- | --- |
| ![](Renders/nudge_2020_rear.png) | ![](Renders/nudge_1515_high.png)  | ![](Renders/nudge_1515_low.png) |

**Wobbler options**: 3mm Pin, 5mm Pin, or M3 screw and internally-threaded dowel:
![](Renders/all_wobblers_side_trim.png)

**Sound good?**  Jump to the [Instructions](INSTRUCTIONS.md) section to get started and find the printed parts to match your printer's layout; one should fit!  

Or, read about some advantages to this design...
## Advantages
 * **Highly repeatable** - single-microstep-level repeatability (typically below .003125 Std Dev over 10 samples).
 * **Low cost** - approximately $10.
 * **Easily sourced** - Zruncho had all parts on hand already. All are on Amazon and AliExpress; smooth M3x6 SHCS is the only “new” part.
 * **Minimizes travel loss** - probe tip fits next to the bed; as little as 6mm overtravel suffices.
 * **Easily adjusted** - Z height, position along an extrusion, and magnet forces are all adjustable, in-situ.
 * **Fast build and print** - print, build, and test in about an hour.  No heatsets, soldering, or gluing required.
 * **Flexible mounting** - options are available to fit almost any printer.
 * **Simple wiring** - 2-pin JST header matches existing Z nozzle endstops.
 * **Temperature-tolerant** - no electronics to burn out at chamber temps (like a camera), and no plastic next to the bed to melt.
 * **In-place mounting option** - run this at the start of every print, just like a QGL or ZTA cycle, so that offsets are perfect, even with temperature changes, or after tightening or maintenance.

Like what you see?  [Buy me a coffee](https://ko-fi.com/zruncho3d) to show the love and enable future mods and content - stuff like [F0](https://github.com/zruncho3d/f-zero), [T0](https://github.com/zruncho3d/tri-zero), [B0](https://github.com/zruncho3d/boxzero), [X0](https://github.com/zruncho3d/double-dragon), [D0](https://github.com/zruncho3d/DuelingZero), [DX](https://github.com/zruncho3d/DuelingX), [ZeroPanels](https://github.com/zruncho3d/ZeroPanels), [ZeroClick](https://github.com/zruncho3d/zeroclick), [NoDropNuts](https://github.com/zruncho3d/f-zero/tree/main/STLs/NoDropNuts), [Poke](https://github.com/zruncho3d/poke), [Vampire Bat](https://github.com/zruncho3d/vampire_bat), and more.

 :heart: *-Zruncho*

## What's Here?

- #### [BOM](BOM.md): Parts list to build your own
- #### [Instructions](INSTRUCTIONS.md): Instructions to print and assemble
- #### [Configuration](CONFIGURATION.md): Configuration - firmware & macros
- #### [Design](DESIGN.md): Learn about why Nudge is designed like that!
- #### [FAQ](FAQ.md): Common questions, answered

## Troubleshooting

**Probe not returning to center?** Magnet force may be insufficient, especially with heavier 5mm pins.  You can easily increase magnet force by cutting the screw towers and aligning the BHCSes to decrease magnet distance.  You can also just push the magnets out slightly for the same effect.  Worst-case use stronger magnets.

**Probe triggered early?** Increase `spread`, improve the initial alignment accuracy, or add travel (by moving the bed or sensor).

**Probe triggering unreliably?** Check each pair of screws with a multimeter.  After a few heat cycles, you will probably need to tighten the SHCSes, as the plastic likes to relax a bit.

**High result variation?** Check the rigidity of the mount and be absolutely sure

**Unsatisfied with Z repeatability?** Z is just not as good, due to the design.  You can keep your original endstop and wire it inline with the original Z endstop, or you can flip the Nudge upside down and change the config to use Tap/Boop etc for the Z probing.

## Support

Find the thread in the User Projects forum channel on the [DoomCube Discord](https://discord.gg/doomcube) and post there.

## Credits

**Enjoy!** I hope you enjoy using this as much as the beta team did bringing this to release!  

Special thanks to `Caza` for critical design feedback and ideas, `Ankurv` for all-up testing,  and the beta team who helped validate the design: `Telxoid`, `Esoterical`, `SteveBuilds`, and others who provided data and feedback, including `RCF` and `Frans-Willem`, who created a PRs for IDEX.

We made a lot of prototypes and test articles to get here.

![alt_text](Images/prototypes.jpg)

It's 60+ and this isn't even all of them.

Thanks also to [Fabreeko](https://www.fabreeko.com/) for supporting this build!  Without HoneyBadger rails, the test gantry would not have happened, and Nudge would not have been as good.  Support vendors like this, which support open-source dev, whenever you can.

-Z

