F-16 High Fidelity Flight Dynamics and Tech/Academic Initial Demonstration
Build 2016..-k
preceding commit hash: 09a491c

Update to: SkateZilla Build (version?)
Update to: Cpt.Smileys v.3 Build

Important Notes:
This is a High Fidelity Flight Dynamics and Tech/Academic Initial Demonstration,
and it NOT a Combat Ready or Systems Ready Module.
There Are No Functioning Cockpit Systems.

Do NOT Use the External 3D model or Cockpit Model EDMs outside of this Module.
Anyone Caught Moving the 3D External/Cockpit EDMs to Private/Hacked/Jury Rigged Mods, 
Even for Personal Use will be dealt with harsely as it violates the license Agreements for the 3D Assets.
So Once Again, Do NOT use the 3D Model EDMs with any private Mods.

Use of program code:
Use Only for Non-Commercial Purposes

Changes since SkateZilla build:
- fix memory leak in FM code
- some refactoring of code for easier changes and additions later
- reduced few unnecessary memory allocations and memory copying
- possible bugfix in inertia handling, testing needed
- splitting code into new objects, reduce C-style "access globally"
- preparations for adding fuel usage and resulting weight-change, speed brakes, wheel brakes, canopy control etc.
- removed "GeneralFilter" since the library only works with VC++ 2010 compiler *without* Service Pack 1 and needs Windows 7.1 SDK
 * in the place is currently "DummyFilter" which does nothing so we can work on the rest of it all
 * better solution needs to be worked out sooner or later..
- some small additions to support different tanks in fuel system
- wheel brakes (toe brakes) are now caught in the input, not finished adding braking factor yet
- started DLL to support cockpit functions, just dummy library so far
- some work on force vectors: use cross-product calculation from FM template, needs force positions in code still
- landing gears should be down when starting from ground now
 * using strut compression value given to DLL in new API method
 * TODO: wheel positions (not in CG)
 * TODO: wheel brakes forces, use proper calculation with kinetic energy
- cockpit stick should move according to pitch/bank input
 * controlled from the DLL, binding in the lua-script to "gauge"
- early support for nosewheel steering with rudder input
 -> broken, disabled
- early experimental support for differential wheel brakes with toe-brakes
 -> broken, disabled
- light blinker code for reuse
- landing gear in/out functionality
- early version of weight balance calculation (with fuel mass)
- placeholder for center of lift change as function of speed
- added simple aerobrake functionality, calculation needs fixing
- reworked aerodynamic code for less reallocation of memory:
possibly slightly higher amount of memory used when running but better and stabler framerate,
code is much much simpler to follow and modify now
- removed unnecessary unit conversions: this has fixed elevon flutter at high speeds

In progress/TODO:
- flight control dynamics for differential/symmetric modes of paired control surfaces
and "mixing" of different surfaces, also needs updates into lift/drag calculations afterwards..
- supersonic aerodynamics
- ground effect

Known Issues:
-Landing Gear Collision is not retractable (disabled intentionally)
 -> figure out how to remove now that landing gear in/out control is working
 
-Nose Wheel Steering Animation is Disabled (disabled intentionally)
-Landing Gear Strut and Piston Data Needs to be re-done (uses template settings)
 (causes Aircraft Ground handling problems and tipping.)
-Landing Gear Suspension values Need to be tuned
 (Landing still feels a bit off, but is no longer a 100% chance of damaged gear)
-Some Control Surface/Pylon Clipping issues.


To Install:
Copy entire project as-is to DCS/mods/aircraft/F16Demo/
