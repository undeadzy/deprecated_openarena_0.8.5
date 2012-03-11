This project is deprecated.  I have a new project that tracsk OpenArena 0.8.8
called openarena_engine.  You should use that as OA 0.8.8 was released.

This client never had all of the changes.  The openarena_engine project has
all of the 0.8.8 client/server changes.


Undeadzy's version of OpenArena 0.8.5
=====================================

This is ioquake3 with Open Arena modifications for OA 0.8.5.

These changes don't match exactly what upstream has.  I cherry pick changes in
order to make it more maintainable.  For instance, I don't care about branding
or icons.  I don't want to have to maintain that.

This is also only the client/server engine.  It doesn't include any of the
OA assets.  Unlike OA 0.8.5, this tracks the latest ioquake3 changes.

Additions:
----------

* Protect all OpenArena modifications with #ifdef OPEN_ARENA
* Added Makefile.local with default OpenArena settings
  + Note: This won't work on Debian if you are using the game data package.
    You'll need the other topic branch for that.

Changes:
--------

* Left in punkbuster cvars because ioquake3 does even for standalone.
* Left in CL_CDKeyValidate because it's not called anyway
* Made functions static when they aren't used outside of the definition

Omissions:
----------

* No branding changes in the Makefile
  + I had to make some for the directory structure because other OA engines
    will expect that.  Those changes are in code/sys/
* This doesn't contain any game logic changes.  I'm unfamiliar with the
  build process and OA appears to be a mixup of various SVN versions.
  + This will work fine if you use the OA game data and replace that engine
    with this one
* Didn't keep the redundant code to check for authorize server
* Doesn't handle the challenge response the same way.  ioquake3 handles this
  already for standalone games.
* Didn't add the #ifndef DEDICATED around the heartbeat
* Didn't make any SDL changes from sdl-win32-mouse-fixes.diff in OA's SVN
* Doesn't filter out say/say-team messages for Cmd_Args_Sanitize
* Doesn't use sv_public
* Doesn't hardcode cl_yawspeed and cl_pitchspeed to 140.0

OpenArena is loosely based on r1432 of ioquake3.  It contains changes
from later versions as well.  This doesn't handle any of the game changes
so it cannot be used to rebuild all of OA yet.
