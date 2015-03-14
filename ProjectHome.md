GCC6809 is a patch to the public GCC compiler sources that adds support for the 6809 backend.  It also includes a copy of the asxxxx assembler and scripts to emulate the rest of the GNU toolchain.

GCC6809 has been tested on Linux and Cygwin, and is probably portable to other
UNIX-like environments as well.  GCC6809 now supports the CoCo hardware
platforms as well as generic targets.

GCC6809 is released in patch form.  The latest stable version is 4.3.4-3 (patch 3 against the public 4.3.4 branch).  Support for newer branches has been started but is not active anymore.  The 4.3.4-3 patch has also successfully been applied to GCC 4.3.6 (the last of the 4.3 series) and should work OK, but this has not been extensively tested.

GCC6809 has been tuned and optimized for writing real-world 6809 programs:

  * It utilizes 100% of the 6809 instruction set, including all
adressing modes.  It also selects the right branch/call instructions.
  * It has builtin functions for accessing special 6809 instructions that
> > aren't exposed through normal C, such as <b>daa</b> and <b>sync</b>.
  * It can be used to write interrupt handlers as well as user code.
  * It has extensions for forcing code/data into different output sections/banks.
  * There is support for 8-bit "int" for tiny applications.

I've also provided a portable 6809 simulator that can be used to run
test programs.  It is named exec09 and is a based on a version originally written by Arto Salmi.  It has been enhanced with the following features:

<ul>
<li> Uses GNU autoconf for maximum portability </li>
<li> More GDB-like syntax </li>
<li> Builtin input/output memory mapped registers </li>
<li> Bounds checking, which catches jumps into non-program space, invalid<br>
opcodes, etc. </li>
<li>Limited support for parsing map files so that addresses can be<br>
translated into symbolic names </li>
</ul>

Althought not well tested, there is also a port of newlib to the 6809, which provides the standard C library functions.  It is based on newlib 1.15.

The I/O routines builtin to the C library target the simulation environment and the CoCo hardware.  Support for other hardware may be added in the future.