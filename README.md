medusa
======

medusa is a Linux CPU frequency governor designed for mobile multi-core
applications processors (e.g. ARM Cortex and Qualcomm Krait).

Compile
-------

Set ARCH, PLAT, KPATH (kernel build path) and TOOLCHAIN appropriately, then:

	$ make ARCH=${ARCH} -C ${KPATH} M=${PWD} CROSS_COMPILE=${TOOLCHAIN} CFLAGS_MODULE="-fno-pic -Wall" EXTRA_CFLAGS=-DPLAT_${PLAT}

Currently supported platforms are APQ8064, I9500 and I9505. To add a new platform,
add the frequency table and core count to medusa.c


Usage
-----

	# insmod ./medusa.ko
	# echo medusa | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

Set tunables in `/sys/devices/system/cpu/cpufreq/medusa/`. Most important is
_fthresh_, which is platform-dependent. See publications below for details.
Approximate values are 0 for anything Cortex-based, and 800,000 KHz for
Snapdragon-600 and similar.


More information
----------------

The theory behind medusa is discussed in the following publications:

_Unifying DVFS and Offlining in Mobile Multicores_  
Aaron Carroll and Gernot Heiser  
In RTAS'14 (Real-Time and Embedded Technology and Applications Symposium), Berlin, Germany, Apr 2014  
<http://www.nicta.com.au/pub?id=7617>  

_Mobile Multicores: Use Them or Waste Them_  
Aaron Carroll and Gernot Heiser  
In HotPower'13 (5th Workshop on Power-Aware Computing and Systems), Farmington, PA, USA, Nov 2013  
<http://www.nicta.com.au/pub?id=7302>  

Author
------

Written by Aaron Carroll <Aaron.Carroll@nicta.com.au>


Copying
-------

Copyright 2013-2014 NICTA

This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License version 2 as published by the Free
Software Foundation.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE, GOOD TITLE or NON INFRINGEMENT. See the GNU General Public
License for more details.

