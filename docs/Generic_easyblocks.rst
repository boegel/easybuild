==============================
Overview of generic easyblocks
==============================

.. contents::
    :depth: 2
    :local:
    :backlinks: top

.. _BinariesTarball:

``BinariesTarball``
===================

(derives from :ref:`Tarball`)

Support for installing a tarball of binaries

Customised steps in ``BinariesTarball`` easyblock
-------------------------------------------------
* ``install_step`` - Install by copying unzipped binaries to 'bin' subdir of installation dir, and fixing permissions.

.. _Binary:

``Binary``
==========

(derives from EasyBlock)

Support for installing software that comes in binary form.
    Just copy the sources to the install dir, or use the specified install command.

Extra easyconfig parameters specific to ``Binary`` easyblock
------------------------------------------------------------

====================   ===============================================================   =============
easyconfig parameter   description                                                       default value
====================   ===============================================================   =============
``staged_install``     Perform staged installation via subdirectory of build directory   ``False``
``install_cmd``        Install command to be used.                                       ``None``
====================   ===============================================================   =============

Customised steps in ``Binary`` easyblock
----------------------------------------
* ``build_step`` - No compilation, this is binary software
* ``configure_step`` - No configuration, this is binary software
* ``install_step`` - Copy all files in build directory to the install directory

.. _Bundle:

``Bundle``
==========

(derives from EasyBlock)

Bundle of modules: only generate module files, nothing to build/install

Customised steps in ``Bundle`` easyblock
----------------------------------------
* ``build_step`` - Do nothing.
* ``configure_step`` - Do nothing.
* ``install_step`` - Do nothing.

.. _CMakeMake:

``CMakeMake``
=============

(derives from :ref:`ConfigureMake`)

Support for configuring build with CMake instead of traditional configure script

Extra easyconfig parameters specific to ``CMakeMake`` easyblock
---------------------------------------------------------------

========================   =====================================================   ===============
easyconfig parameter       description                                             default value
========================   =====================================================   ===============
``configure_cmd_prefix``   Prefix to be glued before ./configure                   ``""``
``prefix_opt``             Prefix command line option for configure script         ``"--prefix="``
``tar_config_opts``        Override tar settings as determined by configure.       ``False``
``separate_build_dir``     Perform build in a separate directory                   ``False``
``srcdir``                 Source directory location to provide to cmake command   ``None``
========================   =====================================================   ===============

Customised steps in ``CMakeMake`` easyblock
-------------------------------------------
* ``configure_step`` - Configure build using cmake
* ``install_step`` - Configure build using cmake

.. _CMakePythonPackage:

``CMakePythonPackage``
======================

(derives from :ref:`CMakeMake`, :ref:`PythonPackage`)

Build a Python package and module with cmake.

    Some packages use cmake to first build and install C Python packages
    and then put the Python package in lib/pythonX.Y/site-packages.

    We install this in a seperate location and generate a module file
    which sets the PYTHONPATH.

    We use the default CMake implementation, and use make_module_extra from PythonPackage.

Extra easyconfig parameters specific to ``CMakePythonPackage`` easyblock
------------------------------------------------------------------------

========================   =====================================================   ===============
easyconfig parameter       description                                             default value
========================   =====================================================   ===============
``configure_cmd_prefix``   Prefix to be glued before ./configure                   ``""``
``prefix_opt``             Prefix command line option for configure script         ``"--prefix="``
``tar_config_opts``        Override tar settings as determined by configure.       ``False``
``separate_build_dir``     Perform build in a separate directory                   ``False``
``srcdir``                 Source directory location to provide to cmake command   ``None``
========================   =====================================================   ===============

Customised steps in ``CMakePythonPackage`` easyblock
----------------------------------------------------
* ``build_step`` - Build Python package with cmake
* ``configure_step`` - Main configuration using cmake
* ``install_step`` - Install with cmake install

.. _CmdCp:

``CmdCp``
=========

(derives from :ref:`MakeCp`)

Software with no configure, no make, and no make install step.
    Just run the specified command for all sources, and copy specified files to the install dir

Extra easyconfig parameters specific to ``CmdCp`` easyblock
-----------------------------------------------------------

========================   =====================================================================   ====================================================
easyconfig parameter       description                                                             default value
========================   =====================================================================   ====================================================
``configure_cmd_prefix``   Prefix to be glued before ./configure                                   ``""``
``tar_config_opts``        Override tar settings as determined by configure.                       ``False``
``with_configure``         Run configure script before building                                    ``False``
``files_to_copy``          List of files or dirs to copy                                           ``[]``
``cmds_map``               List of regex/template command (with 'source'/'target' fields) tuples   ``[('.*', '$CC $CFLAGS %(source)s -o %(target)s')]``
``prefix_opt``             Prefix command line option for configure script                         ``"--prefix="``
========================   =====================================================================   ====================================================

Customised steps in ``CmdCp`` easyblock
---------------------------------------
* ``build_step`` - Build by running the command with the inputfiles
* ``configure_step`` - Build by running the command with the inputfiles
* ``install_step`` - Build by running the command with the inputfiles

.. _ConfigureMake:

``ConfigureMake``
=================

(derives from EasyBlock)

Support for building and installing applications with configure/make/make install

Extra easyconfig parameters specific to ``ConfigureMake`` easyblock
-------------------------------------------------------------------

========================   =================================================   ===============
easyconfig parameter       description                                         default value
========================   =================================================   ===============
``configure_cmd_prefix``   Prefix to be glued before ./configure               ``""``
``prefix_opt``             Prefix command line option for configure script     ``"--prefix="``
``tar_config_opts``        Override tar settings as determined by configure.   ``False``
========================   =================================================   ===============

Commonly used easyconfig parameters with ``ConfigureMake`` easyblock
--------------------------------------------------------------------
====================   ================================================================
easyconfig parameter   description
====================   ================================================================
configopts             Extra options passed to configure (default already has --prefix)
buildopts              Extra options passed to make step (default already has -j X)
installopts            Extra options for installation
====================   ================================================================


Customised steps in ``ConfigureMake`` easyblock
-----------------------------------------------
* ``build_step`` - Start the actual build
        - typical: make -j X
* ``configure_step`` - Configure step
        - typically ./configure --prefix=/install/path style
* ``install_step`` - Create the installation in correct location
        - typical: make install

.. _ConfigureMakePythonPackage:

``ConfigureMakePythonPackage``
==============================

(derives from :ref:`ConfigureMake`, :ref:`PythonPackage`)

Build a Python package and module with 'python configure/make/make install'.

    Implemented by using:
    - a custom implementation of configure_step
    - using the build_step and install_step from ConfigureMake
    - using the sanity_check_step and make_module_extra from PythonPackage

Extra easyconfig parameters specific to ``ConfigureMakePythonPackage`` easyblock
--------------------------------------------------------------------------------

========================   =================================================   ===============
easyconfig parameter       description                                         default value
========================   =================================================   ===============
``runtest``                Run unit tests.                                     ``True``
``configure_cmd_prefix``   Prefix to be glued before ./configure               ``""``
``prefix_opt``             Prefix command line option for configure script     ``"--prefix="``
``options``                Dictionary with extension options.                  ``{}``
``tar_config_opts``        Override tar settings as determined by configure.   ``False``
========================   =================================================   ===============

Customised steps in ``ConfigureMakePythonPackage`` easyblock
------------------------------------------------------------
* ``build_step`` - Build Python package with 'make'.
* ``configure_step`` - Configure build using 'python configure'.
* ``install_step`` - Install with 'make install'.

.. _FortranPythonPackage:

``FortranPythonPackage``
========================

(derives from :ref:`PythonPackage`)

Extends PythonPackage to add a Fortran compiler to the make call

Extra easyconfig parameters specific to ``FortranPythonPackage`` easyblock
--------------------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``runtest``            Run unit tests.                      ``True``
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

Customised steps in ``FortranPythonPackage`` easyblock
------------------------------------------------------
* ``build_step`` - Customize the build step by adding compiler-specific flags to the build command.
* ``configure_step`` - Customize the build step by adding compiler-specific flags to the build command.
* ``install_step`` - Customize the build step by adding compiler-specific flags to the build command.

.. _IntelBase:

``IntelBase``
=============

(derives from EasyBlock)

Base class for Intel software
    - no configure/make : binary release
    - add license_file variable

Extra easyconfig parameters specific to ``IntelBase`` easyblock
---------------------------------------------------------------

======================   ===================================   ====================
easyconfig parameter     description                           default value
======================   ===================================   ====================
``m32``                  Enable 32-bit toolchain               ``False``
``license_activation``   License activation type               ``"license_server"``
``usetmppath``           Use temporary path for installation   ``False``
======================   ===================================   ====================

Customised steps in ``IntelBase`` easyblock
-------------------------------------------
* ``build_step`` - Binary installation files, so no building.
* ``configure_step`` - Configure: handle license file and clean home dir.
* ``install_step`` - Actual installation

        - create silent cfg file
        - set environment parameters
        - execute command

.. _JAR:

``JAR``
=======

(derives from :ref:`Binary`)

Support for installing JAR files.

Extra easyconfig parameters specific to ``JAR`` easyblock
---------------------------------------------------------

====================   ===============================================================   =============
easyconfig parameter   description                                                       default value
====================   ===============================================================   =============
``staged_install``     Perform staged installation via subdirectory of build directory   ``False``
``install_cmd``        Install command to be used.                                       ``None``
====================   ===============================================================   =============

.. _MakeCp:

``MakeCp``
==========

(derives from :ref:`ConfigureMake`)

Software with no configure and no make install step.

Extra easyconfig parameters specific to ``MakeCp`` easyblock
------------------------------------------------------------

========================   =================================================   ===============
easyconfig parameter       description                                         default value
========================   =================================================   ===============
``files_to_copy``          List of files or dirs to copy                       ``[]``
``configure_cmd_prefix``   Prefix to be glued before ./configure               ``""``
``prefix_opt``             Prefix command line option for configure script     ``"--prefix="``
``tar_config_opts``        Override tar settings as determined by configure.   ``False``
``with_configure``         Run configure script before building                ``False``
========================   =================================================   ===============

Customised steps in ``MakeCp`` easyblock
----------------------------------------
* ``configure_step`` - Configure build if required
* ``install_step`` - Install by copying specified files and directories.

.. _PackedBinary:

``PackedBinary``
================

(derives from :ref:`Binary`, EasyBlock)

Support for installing packed binary software.
    Just unpack the sources in the install dir

Extra easyconfig parameters specific to ``PackedBinary`` easyblock
------------------------------------------------------------------

====================   ===============================================================   =============
easyconfig parameter   description                                                       default value
====================   ===============================================================   =============
``staged_install``     Perform staged installation via subdirectory of build directory   ``False``
``install_cmd``        Install command to be used.                                       ``None``
====================   ===============================================================   =============

Customised steps in ``PackedBinary`` easyblock
----------------------------------------------
* ``install_step`` - Copy all unpacked source directories to install directory, one-by-one.

.. _PerlModule:

``PerlModule``
==============

(derives from ExtensionEasyBlock, :ref:`ConfigureMake`)

Builds and installs a Perl module, and can provide a dedicated module file.

Extra easyconfig parameters specific to ``PerlModule`` easyblock
----------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``runtest``            Run unit tests.                      ``"test"``
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

Customised steps in ``PerlModule`` easyblock
--------------------------------------------
* ``build_step`` - No separate build procedure for Perl modules.
* ``configure_step`` - No separate configuration for Perl modules.
* ``install_step`` - Run install procedure for Perl modules.

.. _PythonPackage:

``PythonPackage``
=================

(derives from ExtensionEasyBlock)

Builds and installs a Python package, and provides a dedicated module file.

Extra easyconfig parameters specific to ``PythonPackage`` easyblock
-------------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``runtest``            Run unit tests.                      ``True``
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

Customised steps in ``PythonPackage`` easyblock
-----------------------------------------------
* ``build_step`` - Build Python package using setup.py
* ``configure_step`` - Configure Python package build.
* ``install_step`` - Install Python package to a custom path using setup.py

.. _RPackage:

``RPackage``
============

(derives from ExtensionEasyBlock)

Install an R package as a separate module, or as an extension.

Extra easyconfig parameters specific to ``RPackage`` easyblock
--------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

Customised steps in ``RPackage`` easyblock
------------------------------------------
* ``build_step`` - No separate build step for R packages.
* ``configure_step`` - No configuration for installing R packages.
* ``install_step`` - Install procedure for R packages.

.. _Rpm:

``Rpm``
=======

(derives from :ref:`Binary`)

Support for installing RPM files.
    - sources is a list of rpms
    - installation is with --nodeps (so the sources list has to be complete)

Extra easyconfig parameters specific to ``Rpm`` easyblock
---------------------------------------------------------

====================   ===============================================================   =============
easyconfig parameter   description                                                       default value
====================   ===============================================================   =============
``postinstall``        Enable post install                                               ``False``
``force``              Use force                                                         ``False``
``install_cmd``        Install command to be used.                                       ``None``
``staged_install``     Perform staged installation via subdirectory of build directory   ``False``
``makesymlinks``       Create symlinks for listed paths                                  ``[]``
``preinstall``         Enable pre install                                                ``False``
====================   ===============================================================   =============

Customised steps in ``Rpm`` easyblock
-------------------------------------
* ``configure_step`` - Custom configuration procedure for RPMs: rebuild RPMs for relocation if required.
* ``install_step`` - Custom installation procedure for RPMs into a custom prefix.

.. _RubyGem:

``RubyGem``
===========

(derives from ExtensionEasyBlock)

Builds and installs Ruby Gems.

Extra easyconfig parameters specific to ``RubyGem`` easyblock
-------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

Customised steps in ``RubyGem`` easyblock
-----------------------------------------
* ``build_step`` - No separate build procedure for Ruby Gems.
* ``configure_step`` - No separate configuration for Ruby Gems.
* ``install_step`` - Install Ruby Gems using gem package manager

.. _Tarball:

``Tarball``
===========

(derives from EasyBlock)

Precompiled software supplied as a tarball:
    - will unpack binary and copy it to the install dir

Customised steps in ``Tarball`` easyblock
-----------------------------------------
* ``build_step`` - Dummy build method: nothing to build
* ``configure_step`` - Dummy configure method
* ``install_step`` - Install by copying from specified source directory (or 'start_dir' if not specified).

.. _Toolchain:

``Toolchain``
=============

(derives from :ref:`Bundle`)

Compiler toolchain: generate module file only, nothing to build/install

.. _VSCPythonPackage:

``VSCPythonPackage``
====================

(derives from :ref:`VersionIndependentPythonPackage`)

Support for install VSC Python packages.

Extra easyconfig parameters specific to ``VSCPythonPackage`` easyblock
----------------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``runtest``            Run unit tests.                      ``True``
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

.. _VersionIndependendPythonPackage:

``VersionIndependendPythonPackage``
===================================

(derives from :ref:`VersionIndependentPythonPackage`)

No longer supported class for building/installing python packages without requiring a specific python package.

Extra easyconfig parameters specific to ``VersionIndependendPythonPackage`` easyblock
-------------------------------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``runtest``            Run unit tests.                      ``True``
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

.. _VersionIndependentPythonPackage:

``VersionIndependentPythonPackage``
===================================

(derives from :ref:`PythonPackage`)

Support for building/installing python packages without requiring a specific python package.

Extra easyconfig parameters specific to ``VersionIndependentPythonPackage`` easyblock
-------------------------------------------------------------------------------------

====================   ==================================   =============
easyconfig parameter   description                          default value
====================   ==================================   =============
``runtest``            Run unit tests.                      ``True``
``options``            Dictionary with extension options.   ``{}``
====================   ==================================   =============

Customised steps in ``VersionIndependentPythonPackage`` easyblock
-----------------------------------------------------------------
* ``build_step`` - No build procedure.
* ``configure_step`` - No build procedure.
* ``install_step`` - Custom install procedure to skip selection of python package versions.

