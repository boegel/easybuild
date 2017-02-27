.. _users_use_cases_jsc:

Jülich Supercomputing Centre (JSC) - Germany
============================================

:website: http://www.fz-juelich.de/jsc

:institution: Forschungszentrum Jülich - http://www.fz-juelich.de/portal/EN

:contact: Damian Alvarez, Alan O'Cais, Markus Geimer ({d.alvarez,a.ocais,m.geimer}@fz-juelich.de)

*(last update: Feb 24th 2017)*

.. _users_use_cases_jsc_history:

History
-------

The first contact between JSC and EasyBuild was through the LinkSCEEM (http://www.eumedgrid.eu/index.php/linksceem)
project in 2013. During that period the main x86_64 cluster at JSC -JUROPA- was approaching its end of life. Before its
decomission, a test system was deployed. That test system was the precursor for JUROPA's successor, named JURECA. Thus,
it was the right time to evaluate EasyBuild as an alternative to have consistent and efficient software deployment. The
evaluation period concluded and it was decided that EasyBuild would be JSC's tool of choice to manage software in
JURECA.

.. _users_use_cases_jsc_systems:

Systems
-------

At the moment, EasyBuild is used in JSC'S main production system and a 2 internal systems

JURECA
~~~~~~
* Operating system: CentOS Linux 7
* Processor architecture: Intel Haswell
* Number of nodes: 1872
* GPUs: NVIDIA K80 and K20x
* Interconnects: InfiniBand EDR
* Website: http://www.fz-juelich.de/ias/jsc/EN/Expertise/Supercomputers/JURECA/JURECA_node.html

JUROPA3
~~~~~~
* Operating system: Scientific Linux 7 (TODO: verify)
* Processor architecture: Intel Sandy Bridge, Intel Xeon Phi Knights Landing, Intel Xeon Phi Knights Corner
* Number of nodes: (TODO: count)
* GPUs: NVIDIA K80 and K20x (TODO: verify)
* Interconnects: InfiniBand FDR

JUAMS
~~~~~~
* Operating system: Scientific Linux 7 (TODO: verify)
* Processor architecture: Intel Haswell
* Number of nodes: (TODO: count)
* Interconnects: InfiniBand FDR

.. _users_use_cases_jsc_eb_setup:

EasyBuild setup
---------------

* Python version: 2.6/2.7 (provided by the OS)
* EasyBuild version: 2.X-3.1.0 and ``develop``

Modules tool & module naming scheme
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* Modules tool: Lmod 6 and Lmod 7
* Module syntax: Lua
* Module naming scheme: Custom, based on ``HierarchicalMNS``

Easyblocks
~~~~~~~~~~

Included easyblocks (https://github.com/hpcugent/easybuild-easyblocks) + a handful of internal easyblocks
TODO: check which easyblocks

Easyconfigs
~~~~~~~~~~~

Private repository (with plans to open it). That repository relies heavily on
https://github.com/hpcugent/easybuild-easyconfigs as a starting point, but it has custom toolchains and versions

Toolchains
~~~~~~~~~~

The table below shows the details of the toolchains in the 2016b stage (see :ref:`users_use_cases_jsc_eb_notes` to
learn about stages):

+----------------+---------------------------+----------------+------------------+------------------------+--------+----------------+-------------------------------+----------------------------------------------------------+
| Toolchain name |     Toolchain version     | Underlying GCC |     Compiler     |          MPI           |  CUDA  | Math libraries |    Includes software from     |                          Notes                           |
+----------------+---------------------------+----------------+------------------+------------------------+--------+----------------+-------------------------------+----------------------------------------------------------+
| GCCcore        | 5.4.0                     | 5.4.0          |                  |                        |        |                |                               | Used for boostrapping other compilers and basic software |
| GCC            | 5.4.0                     | 5.4.0          | GCC 5.4.0        |                        |        |                | GCCcore                       | Compiler toolchain                                       |
| iccifort       | 2016.4.258-GCC-5.4.0      | 5.4.0          | Intel 2016.4.258 |                        |        |                | GCCcore                       | Compiler toolchain                                       |
| iccifort       | 2017.0.098-GCC-5.4.0      | 5.4.0          | Intel 2017.0.098 |                        |        |                | GCCcore                       | Compiler toolchain                                       |
| PGI            | 16.9-GCC-5.4.0            | 5.4.0          | PGI 16.9         |                        |        |                | GCCcore                       | Compiler toolchain                                       |
| gpsmpi         | 2016b                     | 5.4.0          | GCC 5.4.0        | ParaStationMPI 5.1.5-1 |        |                | GCCcore, GCC                  | Compiler+MPI toolchain                                   |
| iimpi          | 2016b                     | 5.4.0          | Intel 2017.0.098 | IntelMPI 2017.0.098    |        |                | GCCcore, iccifort             | Compiler+MPI toolchain                                   |
| ipsmpi         | 2016b                     | 5.4.0          | Intel 2017.0.098 | ParaStationMPI 5.1.5-1 |        |                | GCCcore, iccifort             | Compiler+MPI toolchain                                   |
| gmvapich2c     | 2016b-GDR                 | 5.4.0          | GCC 5.4.0        | MVAPICH2 2.2-GDR       | 8.0.44 |                | GCCcore, GCC                  | Compiler+MPI+CUDA toolchain                              |
| imvapich2c     | 2016b-GDR                 | 5.4.0          | Intel 2016.4.258 | MVAPICH2 2.2-GDR       | 8.0.44 |                | GCCcore, iccifort             | Compiler+MPI+CUDA toolchain                              |
| pmvapich2c     | 2016b-GDR                 | 5.4.0          | PGI 16.9         | MVAPICH2 2.2-GDR       | 8.0.44 |                | GCCcore, PGI                  | Compiler+MPI+CUDA toolchain                              |
| gpsolf         | 2016b                     | 5.4.0          | GCC 5.4.0        | ParaStationMPI 5.1.5-1 |        | OLF 2016b      | GCCcore, GCC, gpsmpi          | Compiler+MPI+Math toolchain                              |
| intel-para     | 2016b                     | 5.4.0          | Intel 2017.0.098 | ParaStationMPI 5.1.5-1 |        | MKL 2017.0.098 | GCCcore, iccifort, ipsmpi     | Compiler+MPI+Math toolchain                              |
| intel          | 2016b                     | 5.4.0          | Intel 2017.0.098 | IntelMPI 5.1.3.181     |        | MKL 2017.0.098 | GCCcore, iccifort, iimpi      | Compiler+MPI+Math toolchain                              |
| gmvolfc        | 2016b-GDR                 | 5.4.0          | GCC 5.4.0        | MVAPICH2 2.2-GDR       | 8.0.44 | OLF 2016b      | GCCcore, GCC, gmvapich2c      | Compiler+MPI+CUDA+Math toolchain                         |
| imvmklc        | 2016b-GDR                 | 5.4.0          | Intel 2016.4.258 | MVAPICH2 2.2-GDR       | 8.0.44 | MKL 2017.0.098 | GCCcore, iccifort, imvapich2c | Compiler+MPI+CUDA+Math toolchain                         |
| pmvmklc        | 2016b-GDR                 | 5.4.0          | PGI 16.9         | MVAPICH2 2.2-GDR       | 8.0.44 | MKL 2017.0.098 | GCCcore, PGI, pmvapich2c      | Compiler+MPI+CUDA+Math toolchain                         |
+----------------+---------------------------+----------------+------------------+------------------------+--------+----------------+-------------------------------+----------------------------------------------------------+

*OLF 2016b: OpenBLAS 0.2.19, LAPACK 3.6.1, ScaLAPACK 2.0.2, FFTW 3.3.5

Configuration
~~~~~~~~~~~~~

EasyBuild is configured using a ``Developers`` module that sets up correctly all the EasyBuild related environment
variables

TODO: put the output of the command

> eb --show-config
#
# Current EasyBuild configuration
# (C: command line argument, D: default value, E: environment variable, F: configuration file)
#
buildpath                      (E) = /dev/shm/$USER
experimental                   (E) = True
fixed-installdir-naming-scheme (E) = True
hide-deps                      (E) = ANTLR, APR, APR-util, AT-SPI2-ATK, AT-SPI2-core, ATK, Autoconf, Automake, Bison, CUSP, Coreutils, DB, DBus, DocBook-XML, Dyninst, ETSF_IO, Exiv2, FFmpeg, FLTK, FTGL, GCCcore, GDAL, GEGL, GL2PS, GLEW, GLib, GLPK, GPC, GObject-Introspection, GTI, GTK+, GTS, Gdk-Pixbuf, Ghostscript, GraphicsMagick, GtkSourceView, HarfBuzz, JUnit, JSON-C, JSON-GLib, JasPer, LibTIFF, LibUUID, Libint, LittleCMS, M4, Mesa, NASM, OPARI2, OTF2, PCRE, PDT, PROJ, Pango, PnMPI, PyCairo, PyGObject, PyQt, Qhull, Qt, Qt5, S-Lang, SCons, SIP, SQLite, SWIG, Serf, Szip, Tcl, Tk, UDUNITS, XML-Parser, XZ, XKeyboardConfig, YAXT, Yasm, adwaita-icon-theme, ant, assimp, babl, binutils, byacc, bzip2, cairo, dbus-glib, damageproto, eudev, expat, g2clib, g2lib, gc, gexiv2, glproto, gperf, guile, grib_api, gsettings-desktop-schemas, fixesproto, fontsproto, fontconfig, freeglut, freetype, gettext, icc, ifort, inputproto, intltool, itstool, jhbuild, kbproto, libGLU, libICE, libSM, libX11, libXau, libXaw, libXcursor, libXdamage, libXdmcp, libXext, libXfixes, libXfont, libXft, libXi, libXinerama, libXmu, libXpm, libXrandr, libXrender, libXt, libXtst, libcerf, libcroco, libctl, libdap, libdrm, libdwarf, libelf, libevent, libffi, libfontenc, libgd, libgeotiff, libglade, libidn, libjpeg-turbo, libmatheval, libmypaint, libpng, libpciaccess, libpthread-stubs, libreadline, librsvg, libtool, libunistring, libunwind, libyaml, libxcb, libxkbcommon, libxml2, libxslt, makedepend, motif, ncurses, pixman, pkg-config, pkgconfig, popt, pscom, qrupdate, randrproto, recordproto, renderproto, scrollkeeper, texinfo, util-linux, wxPropertyGrid, wxWidgets, x264, xbitmaps, xcb-proto, xcb-util, xcb-util-image, xcb-util-keysyms, xcb-util-renderutil, xcb-util-wm, xextproto, xineramaproto, xorg-macros, xprop, xproto, xtrans, zlib
hide-toolchains                (E) = GCCcore
include-easyblocks             (E) = $CUSTOM_EASYBLOCKS_PATH/2016b/*.py
include-module-naming-schemes  (E) = $CUSTOM_MNS_PATH/2016b/*.py
include-toolchains             (E) = $CUSTOM_TOOLCHAINS_PATH/2016b/*.py
installpath                    (E) = $STAGES_PATH/2016b
job-backend-config             (E) = $SW_CONFIG_PATH/gc3pie.cfg
job-cores                      (E) = 48
job-max-walltime               (E) = 1
minimal-toolchains             (E) = True
module-naming-scheme           (E) = CustomHierarchicalMNS
packagepath                    (E) = $STAGES_PATH/2016b/packages
prefix                         (E) = $STAGES_PATH/2016b
repositorypath                 (E) = $STAGES_PATH/2016b/eb_repo
robot                          (E) = $GOLDEN_REPO/2016b
robot-paths                    (E) = $GOLDEN_REPO/2016b
set-gid-bit                    (E) = True
sourcepath                     (E) = $SOURCES_PATH/sources
sticky-bit                     (E) = True
umask                          (E) = 022
use-existing-modules           (E) = True

.. _users_use_cases_jsc_eb_notes:

Notes
~~~~~

* JSC deploys software in "Stages". A stage is snapshot of the latest versions of all the available software at a given
  time. The stages change every 6 months, with the arrival of new projects.
* There is a development stage for testing software before moving it to production.
* The software is deployed in a shared GPFS filesystem.
* Software is deployed in production just by the infrastructure manager.
* The module cache is updated by cron job every 30 minutes.
* Paper describing the JURECA use case: http://hpcugent.github.io/easybuild/files/eb-jsc-hust16.pdf
