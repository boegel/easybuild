.. _release_notes:

EasyBuild release notes
=======================

The latest version of EasyBuild provides support for building and installing **1,152** different software packages,
using 25 different (compiler) toolchains. It contains 180 software-specific easyblocks and 30 generic easyblocks,
alongside 6,488 easyconfig files.

.. _release_notes_eb310:

v3.1.0 (February 3rd 2017)
--------------------------

feature release

**framework**

* various enhancements, including:

  * ARM: GCC optimal/generic architecture compiler flags (`#1974 <https://github.com/hpcugent/easybuild-framework/pull/1974>`__)
  * add support for ``--check-style`` to check style in easyconfig files (`#1618 <https://github.com/hpcugent/easybuild-framework/pull/1618>`__, `#2038 <https://github.com/hpcugent/easybuild-framework/pull/2038>`__)
  * add ``HOME`` and ``USER`` from env to available cfg file constants (`#2063 <https://github.com/hpcugent/easybuild-framework/pull/2063>`__)
  * ``--optarch`` can now be specified on a toolchain basis (`#2071 <https://github.com/hpcugent/easybuild-framework/pull/2071>`__)
  * implement ``get_cpu_features`` function in systemtools (`#2074 <https://github.com/hpcugent/easybuild-framework/pull/2074>`__, `#2078 <https://github.com/hpcugent/easybuild-framework/pull/2078>`__)
  * support use of ``linalg`` without MPI, add ``iimkl`` toolchain definition (`#2082 <https://github.com/hpcugent/easybuild-framework/pull/2082>`__)
  * spoof HTTP request header with empty agent (`#2083 <https://github.com/hpcugent/easybuild-framework/pull/2083>`__)
  * exclude dependencies of dependencies that extend $MODULEPATH in make_module_dep (`#2091 <https://github.com/hpcugent/easybuild-framework/pull/2091>`__)

* various bug fixes, including:

  * make ``fetch_github_token`` more robust against ``RuntimeError`` from ``keyring`` (`#2070 <https://github.com/hpcugent/easybuild-framework/pull/2070>`__)
  * POWER: Fix ``--optarch=GENERIC`` for GCC (`#2073 <https://github.com/hpcugent/easybuild-framework/pull/2073>`__)
  * fix docstring in toolchain class (`#2075 <https://github.com/hpcugent/easybuild-framework/pull/2075>`__)
  * skip test cases involving ``.yeb`` if ``PyYAML`` is not installed, silence test in options subsuite (`#2081 <https://github.com/hpcugent/easybuild-framework/pull/2081>`__)
  * fix traceback with '``eb --check-github``' if ``GitPython`` is not installed (`#2085 <https://github.com/hpcugent/easybuild-framework/pull/2085>`__)
  * fix regex for determining list of patched files in GitHub diff (`#2088 <https://github.com/hpcugent/easybuild-framework/pull/2088>`__)
  * modify robot so that it only appends dependencies of tweaked easyconfigs (`#2090 <https://github.com/hpcugent/easybuild-framework/pull/2090>`__)
  * escape metacharacters in paths passed to ``re.compile`` in ``dry_run_set_dirs`` (`#2098 <https://github.com/hpcugent/easybuild-framework/pull/2098>`__)
  * fix broken error message in ``get_toolchain_hierarchy`` + dedicated test case (`#2099 <https://github.com/hpcugent/easybuild-framework/pull/2099>`__)

**easyblocks**

* new easyblock for FFTW (`#1083 <https://github.com/hpcugent/easybuild-easyblocks/pull/1083>`__)
* various enhancements, including:

  * update sanity check for flex 2.6.3, no more ``libfl_pic.a`` library (`#1077 <https://github.com/hpcugent/easybuild-easyblocks/pull/1077>`__)
  * cleanup build before proceeding with full Boost (`#1080 <https://github.com/hpcugent/easybuild-easyblocks/pull/1080>`__)
  * update CP2K easyblock: copy data dir, support version 4.1, support ELPA, fix psmp build with foss toolchain (`#996 <https://github.com/hpcugent/easybuild-easyblocks/pull/996>`__, `#1020 <https://github.com/hpcugent/easybuild-easyblocks/pull/1020>`__, `#1043 <https://github.com/hpcugent/easybuild-easyblocks/pull/1043>`__, `#1084 <https://github.com/hpcugent/easybuild-easyblocks/pull/1084>`__)
  * add sanity check support for OpenSSL 1.1 (`#1087 <https://github.com/hpcugent/easybuild-easyblocks/pull/1087>`__)
  * support the latest changes in Inspector 2017 (`#1047 <https://github.com/hpcugent/easybuild-easyblocks/pull/1047>`__)
  * update NEURON easyblock to support the lack of ``hoc_ed`` in 7.4 (`#987 <https://github.com/hpcugent/easybuild-easyblocks/pull/987>`__)
  * add support for WPS 3.8 (`#1079 <https://github.com/hpcugent/easybuild-easyblocks/pull/1079>`__)
  * also consider ``setuptools`` in ``EasyBuildMeta`` easyblock (`#1093 <https://github.com/hpcugent/easybuild-easyblocks/pull/1093>`__)

* various bug fixes, including:

  * (correctly) define ``$ROSETTA3_DB`` in Rosetta easyblock (`#1092 <https://github.com/hpcugent/easybuild-easyblocks/pull/1092>`__)

**easyconfigs**

* added easyconfigs for ``foss/2017a`` and ``intel/2017a`` common toolchains (`#3968 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3968>`__, `#3969 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3969>`__)
* added example easyconfig files for 16 new software packages:

  * ack (`#3983 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3983>`__), cclib (`#4065 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4065>`__), ConnectomeWorkbench (`#3411 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3411>`__), GroIMP (`#3994 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3994>`__), hyperspy (`#3991 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3991>`__), I-TASSER (`#1216 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1216>`__),
    ImageJ (`#4023 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4023>`__, `#4062 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4062>`__), libconfig (`#4051 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4051>`__), libspatialindex (`#4002 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4002>`__), mahotas (`#3990 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3990>`__), Minia (`#3949 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3949>`__), muParser (`#4007 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4007>`__), 
    NetLogo (`#3941 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3941>`__), QIIME (`#3868 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3868>`__), QwtPolar (`#4019 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4019>`__), Tensorflow (`#4084 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4084>`__, `#4095 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4095>`__)

* added additional easyconfigs for various supported software packages, including:

  * Boost 1.62.0 + 1.63.0, CP2K 4.1, GSL 2.3, PLUMED 2.3.0, Qt5 5.7.1, WRF 3.8, WPS 3.8, Yade 2016.06a, zlib 1.2.11

* various enhancements, including:

  * update FFTW 3.3.5 easyconfigs to use FFTW easyblock & enable running of tests (`#3985 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3985>`__)
  * add FME extensions (+ deps) in R 3.3.1 easyconfigs (`#4063 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4063>`__)

* various bug fixes, including:

  * add libxml2 dependency on HDF5 (`#3759 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3759>`__)
  * remove unnecessary dependency in libmatheval (`#3988 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3988>`__)
  * fix permissions on SWASH binaries (`#4003 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4003>`__)
  * add conda-forge channel to perl-app-cpanminus (`#4012 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4012>`__)
  * add missing deps (libpthread-stubs, libpciaccess) to libdrm 2.4.70 (`#4032 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4032>`__)
  * modloadmsg style fixes in multiple easyconfigs (`#4035 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4035>`__)
  * include X11 as dep for Molden (`#4082 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4082>`__)
  * remove incorrect definition for $ROSETTA3_DB, now (correctly) defined via Rosetta easyblock (`#4083 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4083>`__)

* fix source URLs for several easyconfigs, including:

  * arpack-ng 3.1.3 + 3.1.5 (`#4050 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4050>`__), ChIP-Seq 1.5-1 (`#4050 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4050>`__), Ghostscript 9.10, 9.14 + 9.16 (`#4050 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4050>`__),
    Git 1.7.12, 1.8.2 + 1.8.3.1 (`#4050 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4050>`__), HBase 1.0.2 (`#4043 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4043>`__), libevent 2.0.22 (`#4037 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4037>`__), libsodium 1.0.3 (`#4046 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4046>`__),
    lynx 2.8.7 (`#4050 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4050>`__), Maven 3.2.2 and 3.3.3 (`#4039 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4039>`__), MEME 4.8.0 (`#4050 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4050>`__), PCC 20131024 (`#4044 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4044>`__), S-Lang 2.3.0 (`#4045 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4045>`__),
    Spark 1.3.0 (`#4041 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4041>`__), splitRef 0.0.2 (`#4040 <https://github.com/hpcugent/easybuild-easyconfigs/pull/4040>`__)


.. _release_notes_eb302:

v3.0.2 (December 22nd 2016)
---------------------------

bugfix release

**framework**

* various bug fixes, including:

  * also skip dependencies of dependencies marked as external module in get_toolchain_hierarchy (`#2042 <https://github.com/hpcugent/easybuild-framework/pull/2042>`__)
  * disable verbose setvar in modules.py (`#2044 <https://github.com/hpcugent/easybuild-framework/pull/2044>`__)
  * force copying of easyconfigs in --new-pr/--update-pr, even when combined with -x (`#2045 <https://github.com/hpcugent/easybuild-framework/pull/2045>`__)
  * fix verification of filename for easyconfigs used to resolve deps (`#2051 <https://github.com/hpcugent/easybuild-framework/pull/2051>`__)
  * skip RPATH sanity check when toolchain did not use RPATH wrappers (`#2052 <https://github.com/hpcugent/easybuild-framework/pull/2052>`__)
  * check whether file-like paths are readable before reading them in systemtools module (`#2065 <https://github.com/hpcugent/easybuild-framework/pull/2065>`__)

* various small enhancements, including:

  * add 'rpath' toolchain option to selectively disable use of RPATH wrappers (`#2047 <https://github.com/hpcugent/easybuild-framework/pull/2047>`__)

**easyblocks**

* various enhancements, including:

  * enhance DL_POLY_Classic easyblock to support building with Plumed support (REVIEW) (`#829 <https://github.com/hpcugent/easybuild-easyblocks/pull/829>`__)
  * make the Allinea easyblock search for the templates in the easyconfig paths (`#1025 <https://github.com/hpcugent/easybuild-easyblocks/pull/1025>`__)
  * make FortranPythonPackage aware of (pre)buildopts (`#1065 <https://github.com/hpcugent/easybuild-easyblocks/pull/1065>`__)
  * update sanity check for Mono to support recent versions (`#1069 <https://github.com/hpcugent/easybuild-easyblocks/pull/1069>`__)
  * fix Eigen sanity check for latest version 3.3.1 (`#1074 <https://github.com/hpcugent/easybuild-easyblocks/pull/1074>`__)

* various bug fixes, including:

  * skip RPATH sanity check for binary installations (`#1056 <https://github.com/hpcugent/easybuild-easyblocks/pull/1056>`__)
  * pass CXXFLAGS and LDFLAGS to Boost bjam (`#1064 <https://github.com/hpcugent/easybuild-easyblocks/pull/1064>`__)
  * make pip ignore already installed versions of the package being installed (`#1066 <https://github.com/hpcugent/easybuild-easyblocks/pull/1066>`__)
  * don't pass empty string as custom installopts for numpy in test_step (`#1067 <https://github.com/hpcugent/easybuild-easyblocks/pull/1067>`__)
  * make the Rosetta EasyBlock work in --module-only mode (`#1073 <https://github.com/hpcugent/easybuild-easyblocks/pull/1073>`__)

**easyconfigs**

* added example easyconfig files for 13 new software packages:

  * CryptoMiniSat (`#3952 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3952>`__), MATSim (`#3902 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3902>`__), Molcas (`#2084 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2084>`__), ne (`#3376 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3376>`__), psmc (`#3910 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3910>`__), PyCogent (`#3897 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3897>`__),
    PyNAST (`#3897 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3897>`__), RASPA2 (`#3903 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3903>`__, `#3946 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3946>`__), SimPEG (`#3876 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3876>`__), SolexaQA++ (`#3892 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3892>`__), taco (`#3882 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3882>`__),
    UCLUST (`#3896 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3896>`__), USPEX (`#3767 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3767>`__)

* added additional easyconfigs for various supported software packages, including:

  * Mono 4.6.2.7, PGI 16.10, ROOT 6.08.02

* various enhancements, including:

  * trivial style fixes (`#3878 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3878>`__, `#3893 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3893>`__, `#3895 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3895>`__)

* various bug fixes, including:

  * add X11 develop libs to ncview easyconfig (`#3881 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3881>`__)
  * fix source_urls in pkg-config easyconfigs (`#3907 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3907>`__)
  * install numpy/scipy as .egg to ensure shadowing of numpy/scipy in parent Python installation (`#3921 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3921>`__)
  * fix broken source URL + homepage for Infernal (`#3928 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3928>`__)
  * fix test that verifies dumped easyconfig, take into account that dumped dependencies may include hardcoded dependency (`#3932 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3932>`__)
  * include libGLU as dependency in freeglut easyconfigs with recent Mesa (`#3936 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3936>`__)
  * add patch for FreeSurfer to fix issue with MATLAB 2013 (`#3954 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3954>`__)


.. _release_notes_eb301:

v3.0.1 (November 30th 2016)
---------------------------

bugfix release

**framework**

* important changes

  * always use Intel-specific MPI compiler wrappers (``mpiicc``, ``mpiicpc``, ``mpiifort``) for toolchains using both Intel compilers and Intel MPI (`#2005 <https://github.com/hpcugent/easybuild-framework/pull/2005>`__)

* various small enhancements, including:

  * use ``setvar`` in ``modules.py`` to define environment variables (`#2011 <https://github.com/hpcugent/easybuild-framework/pull/2011>`__)
  * include output of ``sanity_check_commands`` in the build log (`#2020 <https://github.com/hpcugent/easybuild-framework/pull/2020>`__)

* various bug fixes, including:

  * fix testing of bootstrap script in Travis config (`#2003 <https://github.com/hpcugent/easybuild-framework/pull/2003>`__)
  * use correct module syntax in bootstrap script if Lmod is not used (i.e. Tcl) (`#2007 <https://github.com/hpcugent/easybuild-framework/pull/2007>`__)
  * fix packaging issue with non-Python scripts in easybuild/scripts (`#2015 <https://github.com/hpcugent/easybuild-framework/pull/2015>`__)

    * fixes issue where RPATH wrapper template script (``rpath_wrapper_template.sh.in``) was not included in the v3.0.0 release

  * make tests more robust against running headless (`#2016 <https://github.com/hpcugent/easybuild-framework/pull/2016>`__)
  * avoid rewrapping already wrapped compiler/linker command with RPATH wrapper script (`#2022 <https://github.com/hpcugent/easybuild-framework/pull/2022>`__)
  * fix ``log.error`` traceback due to '``raise EasyBuildError``' involving a '``%s``' in error message (`#2024 <https://github.com/hpcugent/easybuild-framework/pull/2024>`__)
  * make sure '``modules_tool``' attribute is also defined for extensions (`#2026 <https://github.com/hpcugent/easybuild-framework/pull/2026>`__)
  * only dump easyconfig with modified deps due to ``--minimal-toolchains`` to 'reprod' subdir of install dir (`#2028 <https://github.com/hpcugent/easybuild-framework/pull/2028>`__)
  * avoid appending '``-h'`` to sanity check commands specified as a string (`#2030 <https://github.com/hpcugent/easybuild-framework/pull/2030>`__)
  * fix bug in ``list_software_rst``: always include version suffix regardless of value (`#2032 <https://github.com/hpcugent/easybuild-framework/pull/2032>`__)

**easyblocks**

* various enhancements, including:

  * update SAMtools easyblock for recent versions (`#1048 <https://github.com/hpcugent/easybuild-easyblocks/pull/1048>`__)

* various bugfixes, including:

  * fix QuantumESPRESSO easyblock to handle gipaw correctly (`#1041 <https://github.com/hpcugent/easybuild-easyblocks/pull/1041>`__)
  * always specify name of serial Fortran compiler to ALADIN, it already knows to use MPI wrapper commands (`#1050 <https://github.com/hpcugent/easybuild-easyblocks/pull/1050>`__)

**easyconfigs**

* added example easyconfig files for 7 new software packages:

  * Cookiecutter (`#3827 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3827>`__), ETE (`#3857 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3857>`__), findhap (`#3860 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3860>`__), graphviz (Python bindings, `#3826 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3826>`__), LoFreq (`#3856 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3856>`__), PhyloBayes-MPI (`#3859 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3859>`__), XGBoost (`#3849  <https://github.com/hpcugent/easybuild-easyconfigs/pull/3849>`__)

* added additional easyconfigs for various supported software packages

* various enhancements, including:

  * add ``ipywidgets`` and ``widgetsnbextension`` extensions to IPython 5.1.0 easyconfigs (`#3818 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3818>`__, `#3823 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3823>`__)
  * run dadi test suite as a sanity check command (`#3858 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3858>`__)

* various bug fixes, including:

  * fix incorrect descriptions for ifort (`#3817 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3817>`__)
  * fix ``modulename`` for Jinja2 and Pygments (`#3823 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3823>`__)
  * fix download URL in BLAST 2.2.26 easyconfig (`#3861 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3861>`__)


.. _release_notes_eb300:

v3.0.0 (November 16th 2016)
---------------------------

feature release

**framework**

* backward-incompatible changes:

  * make robot always consider subtoolchains, even without ``--minimal-toolchains`` (but in reverse order) (`#1973 <https://github.com/hpcugent/easybuild-framework/pull/1973>`__)
  * clean up behaviour that was deprecated for EasyBuild v3.0 (`#1978 <https://github.com/hpcugent/easybuild-framework/pull/1978>`__)
  * change *default* config to use ``Lmod``/``Lua`` for modules tool/syntax, ``GC3Pie`` as job backend (`#1985 <https://github.com/hpcugent/easybuild-framework/pull/1985>`__)
  * the minimal required version of Lmod was bumped to 5.8 (`#1985 <https://github.com/hpcugent/easybuild-framework/pull/1985>`__)

* major new features:

  * (experimental) support for RPATH linking via ``--rpath`` (`#1942 <https://github.com/hpcugent/easybuild-framework/pull/1942>`__)

    * see http://easybuild.readthedocs.org/en/latest/RPATH-support.html

  * add support for ``--consider-archived-easyconfigs`` (`#1972 <https://github.com/hpcugent/easybuild-framework/pull/1972>`__)

    * see http://easybuild.readthedocs.org/en/latest/Archived-easyconfigs.html

  * stabilize ``--new-pr`` and ``--update-pr`` (`#1979 <https://github.com/hpcugent/easybuild-framework/pull/1979>`__)

    * see http://easybuild.readthedocs.org/en/latest/Integration_with_GitHub.html

* various other small enhancements, including:

  * add support for '``devel``' log level (`#1815 <https://github.com/hpcugent/easybuild-framework/pull/1815>`__)
  * make ``remove_file`` aware of ``--extended-dry-run`` + add dedicated unit test (`#1932 <https://github.com/hpcugent/easybuild-framework/pull/1932>`__)
  * add support for filtering out setting/updating particular environment variables from generated modules (`#1943 <https://github.com/hpcugent/easybuild-framework/pull/1943>`__)

    * see ``--filter-env-vars``

  * clean up output of EasyBuild bootstrap script & add version (`#1944 <https://github.com/hpcugent/easybuild-framework/pull/1944>`__)
  * improved ARM platform/CPU detection (`#1953 <https://github.com/hpcugent/easybuild-framework/pull/1953>`__)
  * use '``0``' as letter dir for funky software names that don't start with a letter, e.g., ``3to2`` (`#1954 <https://github.com/hpcugent/easybuild-framework/pull/1954>`__)
  * make bootstrap script aware of ``vsc-install`` for offline installation (`#1955 <https://github.com/hpcugent/easybuild-framework/pull/1955>`__)
  * add support for ``blas_family()`` and ``lapack_family()`` methods in ``Toolchain`` instances (`#1961 <https://github.com/hpcugent/easybuild-framework/pull/1961>`__)
  * make ``copy_file`` dry-run aware (`#1963 <https://github.com/hpcugent/easybuild-framework/pull/1963>`__)
  * reorganise test easyconfigs to match structure in easyconfigs repo (`#1970 <https://github.com/hpcugent/easybuild-framework/pull/1970>`__)
  * add a toolchain compiler option for enforcing IEEE-754 conformance (`#1975 <https://github.com/hpcugent/easybuild-framework/pull/1975>`__)
  * support for ``intelcuda`` compiler toolchain (`#1976 <https://github.com/hpcugent/easybuild-framework/pull/1976>`__)
  * check that each glob pattern matches at least one file ``expand_glob_paths`` (important for ``--include-*``) (`#1980 <https://github.com/hpcugent/easybuild-framework/pull/1980>`__)
  * enhance bootstrap to auto-skip stage 0 in case a suitable setuptools is already available (`#1946 <https://github.com/hpcugent/easybuild-framework/pull/1946>`__, `#1984 <https://github.com/hpcugent/easybuild-framework/pull/1984>`__)
  * simplify ``GC3Pie`` version check (`#1987 <https://github.com/hpcugent/easybuild-framework/pull/1987>`__)
  * include suggestion on how to change configuration w.r.t. modules tool/syntax (`#1989 <https://github.com/hpcugent/easybuild-framework/pull/1989>`__)

* various bug fixes, including:

  * fix test for ``find_easybuild_easyconfig`` (`#1931 <https://github.com/hpcugent/easybuild-framework/pull/1931>`__)
  * remove existing module file under ``--force``/``--rebuild`` (`#1933 <https://github.com/hpcugent/easybuild-framework/pull/1933>`__)
  * fix combining ``--search`` and ``--try-*`` (`#1937 <https://github.com/hpcugent/easybuild-framework/pull/1937>`__)
  * fix appending to existing ``buildstats`` in ``FileRepository.add_easyconfig`` (`#1948 <https://github.com/hpcugent/easybuild-framework/pull/1948>`__)
  * fix handling of iterate easyconfig parameters, restore them during cleanup (`#1949 <https://github.com/hpcugent/easybuild-framework/pull/1949>`__)
  * fix filtering loads for (hidden) build deps from generated module (`#1959 <https://github.com/hpcugent/easybuild-framework/pull/1959>`__)
  * handle multi-flag compiler options on all types of options (`#1966 <https://github.com/hpcugent/easybuild-framework/pull/1966>`__)
  * fix ``--list-software`` by making ``letter_dir_for`` function aware of '``*``' wildcard name (`#1969 <https://github.com/hpcugent/easybuild-framework/pull/1969>`__)
  * skip dependencies of toolchain marked as external modules when determining module hierarchy (`#1977 <https://github.com/hpcugent/easybuild-framework/pull/1977>`__)
  * bump page limit in ``fetch_latest_commit_sha``, spit out more meaningful error if too many branches were encountered (`#1981 <https://github.com/hpcugent/easybuild-framework/pull/1981>`__)
  * fix CUDA-related issues in ``HierarchicalMNS`` (`#1986 <https://github.com/hpcugent/easybuild-framework/pull/1986>`__)

**easyblocks**

* backwards incompatible changes:

  * remove deprecated GenomeAnalysisTK/GATK easyblock (`#1001 <https://github.com/hpcugent/easybuild-easyblocks/pull/1001>`__)
  * remove deprecated '``get_netcdf_module_set_cmds``' function from netCDF easyblock (`#1015 <https://github.com/hpcugent/easybuild-easyblocks/pull/1015>`__)
  * remove deprecated '``get_blas_lib``' function from LAPACK easyblock (`#1016 <https://github.com/hpcugent/easybuild-easyblocks/pull/1016>`__)
  * remove ``QLogicMPI`` easyblock (`#1023 <https://github.com/hpcugent/easybuild-easyblocks/pull/1023>`__)

* new easyblock for installing Anaconda (`#950 <https://github.com/hpcugent/easybuild-easyblocks/pull/950>`__)
* add generic easyblock for Conda installations (`#950 <https://github.com/hpcugent/easybuild-easyblocks/pull/950>`__)
* various enhancements, including:

  * enable use of ``GCCcore`` as toolchain for Clang, fail if no GCC prefix is found (`#1002 <https://github.com/hpcugent/easybuild-easyblocks/pull/1002>`__)
  * also build Boost MPI library in parallel (`#1005 <https://github.com/hpcugent/easybuild-easyblocks/pull/1005>`__, `#1038 <https://github.com/hpcugent/easybuild-easyblocks/pull/1038>`__)
  * enhance g2clib easyblock to allow to install 1.6.0 or higher (`#1006 <https://github.com/hpcugent/easybuild-easyblocks/pull/1006>`__)
  * update QuantumESPRESSO easyblock to support packaging changes in 6.0 (`#1007 <https://github.com/hpcugent/easybuild-easyblocks/pull/1007>`__)
  * add support to ``Scons`` generic easyblock to provide argument to specify installation prefix (`#1008 <https://github.com/hpcugent/easybuild-easyblocks/pull/1008>`__)
  * update ``IntelBase`` and imkl easyblocks to handle the 2017 versions of compilers/imkl (`#1012 <https://github.com/hpcugent/easybuild-easyblocks/pull/1012>`__)
  * leverage ``toolchain.linalg`` functionality in ScaLAPACK easyblock, use ``copy_file`` (`#1014 <https://github.com/hpcugent/easybuild-easyblocks/pull/1014>`__)
  * allow netCDF-C++4 to be used with ESMF (`#1019 <https://github.com/hpcugent/easybuild-easyblocks/pull/1019>`__)
  * update Advisor easyblock to support latest versions (`#1021 <https://github.com/hpcugent/easybuild-easyblocks/pull/1021>`__)
  * update CBLAS easyblock to build with ``foss`` toolchain (`#1024 <https://github.com/hpcugent/easybuild-easyblocks/pull/1024>`__)
  * update Gurobi easyblock to use ``copy_file`` (`#1028 <https://github.com/hpcugent/easybuild-easyblocks/pull/1028>`__)
  * add support for giving ``/lib`` preference over ``/lib64`` & co in GCC installation (`#1030 <https://github.com/hpcugent/easybuild-easyblocks/pull/1030>`__, `#1035 <https://github.com/hpcugent/easybuild-easyblocks/pull/1035>`__)
  * enable installation of ``libiberty`` by default for binutils (`#1030 <https://github.com/hpcugent/easybuild-easyblocks/pull/1030>`__)
  * avoid CMake fiddling with the RPATHs injected by EasyBuild via ``--rpath`` in CMakeMake and METIS easyblocks (`#1031 <https://github.com/hpcugent/easybuild-easyblocks/pull/1031>`__, `#1034 <https://github.com/hpcugent/easybuild-easyblocks/pull/1034>`__)
  * simplify scipy sanity check to make it more robust w.r.t. version updates (`#1037 <https://github.com/hpcugent/easybuild-easyblocks/pull/1037>`__)

* various bug fixes, including:

  * make sure '``None``' doesn't appear in modules generated with ``--module-only`` (`#998 <https://github.com/hpcugent/easybuild-easyblocks/pull/998>`__)
  * fix ATLAS easyblock for non-x86 systems (`#1003 <https://github.com/hpcugent/easybuild-easyblocks/pull/1003>`__)
  * fix '``usempi``' and '``with_mpi``' usage to allow for a serial build of Amber 16 (`#1013 <https://github.com/hpcugent/easybuild-easyblocks/pull/1013>`__)
  * add both ``lib/python2.7/site-packages/{,wx-3.0-gtk2}`` to ``$PYTHONPATH`` for wxPython (`#1018 <https://github.com/hpcugent/easybuild-easyblocks/pull/1018>`__)
  * only hard inject RPATH for ``/usr/lib*`` directories when building binutils with ``dummy`` toolchain (`#1026 <https://github.com/hpcugent/easybuild-easyblocks/pull/1026>`__)
  * make HDF5 easyblock handle ``--filter-deps`` correctly (`#1027 <https://github.com/hpcugent/easybuild-easyblocks/pull/1027>`__)
  * update Travis config w.r.t. changes framework config defaults and required Lmod version (`#1029 <https://github.com/hpcugent/easybuild-easyblocks/pull/1029>`__)
  * be more patient when running Mathematica Q&A installer (`#1036 <https://github.com/hpcugent/easybuild-easyblocks/pull/1036>`__)

**easyconfigs**

* backwards incompatible changes:

  * archive easyconfigs using old inactive toolchains

    * see `#3725 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3725>`__, `#3728 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3728>`__, `#3729 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3729>`__, `#3730 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3730>`__, `#3731 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3731>`__, `#3732 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3732>`__, `#3733 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3733>`__, `#3735 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3735>`__, `#3736 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3736>`__, `#3737 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3737>`__, `#3738 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3738>`__
    * only taken into account by EasyBuild if ``--consider-archived-easyconfigs`` is enabled
    * no easyconfigs available outside of archive for QLogicMPI + 15 toolchains:

      * ``ClangGCC``, ``cgmpich``, ``cgmpolf``, ``cgmvapich2``, ``cgmvolf``, ``cgompi``, ``cgoolf``, ``gmacml``,
        ``goalf``, ``gpsmpi``, ``gpsolf``, ``iiqmpi``, ``intel-para``, ``ipsmpi``, ``iqacml``

  * fix name in PyTables easyconfigs (was 'pyTables') (`#3785 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3785>`__)

* added example easyconfig files for 32 new software packages:

  * 3to2 (`#3655 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3655>`__), Anaconda2 (`#3337 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3337>`__), Anaconda3 (`#3337 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3337>`__), ART (`#3724 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3724>`__), atools (`#3631 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3631>`__),
    awscli (`#3645 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3645>`__), behave (`#3751 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3751>`__), Blosc (`#3785 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3785>`__), bokeh (`#3790 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3790>`__), Cantera (`#3655 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3655>`__),
    Cargo (`#3764 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3764>`__), dadi v1.7.0, distributed (`#3786 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3786>`__), ea-utils (`#3634 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3634>`__), Elk (`#3644 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3644>`__),
    FGSL (`#3638 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3638>`__), gencore_variant_detection (`#3337 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3337>`__), help2man (`#3768 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3768>`__), lbzip2 (`#3791 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3791>`__),
    Log-Log4perl (`#3574 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3574>`__), Minimac2 (`#3783 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3783>`__), mypy (`#3694 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3694>`__), OBITools (`#3573 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3573>`__),
    perl-app-cpanminus (`#3337 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3337>`__), PGDSpider (`#3625 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3625>`__), prokka (`#3755 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3755>`__), Reads2snp (`#3609 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3609>`__),
    spglib-python (`#3620 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3620>`__), SUNDIALS (`#3654 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3654>`__, `#3655 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3655>`__), SelEstim (`#3626 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3626>`__), XMLStarlet (`#3797 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3797>`__),
    x265 (`#3090 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3090>`__)

* added easyconfigs for new '``intelcuda``' toolchain (`#3750 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3750>`__)

* added new easyconfigs for existing toolchains:

  * ``goolfc/2016.08`` (`#3796 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3796>`__), ``goolfc/2016.10`` (`#3666 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3666>`__, `#3775 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3775>`__), ``intel/2017.00`` (`#3543 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3543>`__), ``intel/2017.01`` (`#3757 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3757>`__),
    ``iomkl/2016.09-GCC-4.9.3-2.25`` (`#3680 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3680>`__), ``iomkl/2016.09-GCC-5.4.0-2.26`` (`#3772 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3772>`__)

* added additional easyconfigs for various supported software packages, including:

  * Advisor 2017 update 1, Amber 16, ATLAS 3.10.2, GROMACS 2016, Octave 4.0.3,
    OpenFOAM 3.0.1, PyTables 3.3.0, QuantumESPRESSO 6.0, Rust v1.12.1

* various other enhancements, including:

  * STREAM builds using ~56GiB and ~111GiB (`#3670 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3670>`__)

* various bug fixes, including:

  * fix source spec in VASP easyconfig, ensure static linking with Intel MKL (`#3381 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3381>`__)
  * fix source URL in GCCcore 6.2.0 easyconfig (`#3608 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3608>`__)
  * correct STAMP dependency in i-cisTarget, must be 1.3 (`#3613 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3613>`__)
  * consistently specify to use ``-fgnu89-inline`` flag in M4 1.4.17 easyconfigs (`#3623 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3623>`__)
  * fix source URLs for Cython (`#3636 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3636>`__)
  * add Bison as build dep and M4 as runtime dep for flex 2.6.0 (`#3656 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3656>`__)
  * enable parallel building of flex 2.6.0 (`#3630 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3630>`__)
  * add zlib and bzip2 dependencies to X11 bundle (`#3662 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3662>`__)
  * use '``letter_dir_for``' function rather than just grabbing 1st letter of software name in easyconfigs tests (`#3664 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3664>`__)
  * add patch to fix typo in GRIT 2.0.5 (`#3675 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3675>`__)
  * fix typo in patch for WRF 3.8.0 (`#3702 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3702>`__)
  * use ``$CC``, ``$CXX`` rather than ``$I_MPI_CC``, ``$I_MPI_CXX`` in patch for OpenFOAM 4.0 (`#3703 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3703>`__)
  * patch FLTK to fix '``undefined symbol``' issue when building Octave (`#3704 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3704>`__)
  * include Pillow as a proper dep for scikit-image rather than as extension, since it has deps itself (`#3723 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3723>`__)
  * update Travis config w.r.t. changes framework config defaults and required Lmod version (`#3773 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3773>`__)
  * don't limit parallellism to 4 in recent GCC easyconfigs (`#3776 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3776>`__, `#3777 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3777>`__, `#3778 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3778>`__)
  * include M4 as dependency in flex 2.5.39 easyconfigs + fix consistency issues (`#3782 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3782>`__)
  * consistently apply patch for ncurses 6.0 (`#3792 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3792>`__)
  * eliminate dependency on ``mpi-mic-rt`` in ifort (`#3793 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3793>`__)
  * include Autotools as build dependency in all beagle-lib and MrBayes easyconfigs (`#3794 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3794>`__)
  * make OpenBLAS use the LAPACK version specified in the easyconfig (v0.2.18 & v0.2.19) (`#3795 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3795>`__)
  * include original download URL for ISL source tarball in GCC easyconfigs (`#3798 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3798>`__)
  * disable installing ``libiberty`` for binutils built with intel toolchain (`#3802 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3802>`__)


.. _release_notes_eb290:

v2.9.0 (September 23rd 2016)
----------------------------

feature release

**framework**

* note: vsc-base 2.5.4 or more recent is now required
* various small enhancements, including:

  * change option ``--color`` choices to auto/always/never (`#1701 <https://github.com/hpcugent/easybuild-framework/pull/1701>`__, `#1898 <https://github.com/hpcugent/easybuild-framework/pull/1898>`__, `#1911 <https://github.com/hpcugent/easybuild-framework/pull/1911>`__)
  * add support for '``hidden``' easyconfig parameter (`#1837 <https://github.com/hpcugent/easybuild-framework/pull/1837>`__)
  * add support for using ``ccache`` and ``f90cache`` compiler caching tools (`#1844 <https://github.com/hpcugent/easybuild-framework/pull/1844>`__, `#1912 <https://github.com/hpcugent/easybuild-framework/pull/1912>`__)

    * see ``--use-ccache`` and ``--use-f90cache``

  * update Cray metadata for 16.06 CrayPE release (`#1851 <https://github.com/hpcugent/easybuild-framework/pull/1851>`__)
  * also include patch files in ``--new-pr`` and ``--update-pr`` (`#1852 <https://github.com/hpcugent/easybuild-framework/pull/1852>`__)
  * handle deleted files in ``--new-pr`` (`#1853 <https://github.com/hpcugent/easybuild-framework/pull/1853>`__)
  * add support for ``--install-latest-eb-release`` (`#1861 <https://github.com/hpcugent/easybuild-framework/pull/1861>`__)
  * add support for hiding toolchains, see ``--hide-toolchains`` and '``hidden``' key in '``toolchain``' spec (`#1871 <https://github.com/hpcugent/easybuild-framework/pull/1871>`__)
  * add template for GitHub source URL (`#1872 <https://github.com/hpcugent/easybuild-framework/pull/1872>`__)
  * add support for combining ``--new-pr``/``--update-pr`` and ``--robot`` (`#1881 <https://github.com/hpcugent/easybuild-framework/pull/1881>`__)
  * add support for ``--list-software`` and ``--list-installed-software`` (`#1883 <https://github.com/hpcugent/easybuild-framework/pull/1883>`__, `#1910 <https://github.com/hpcugent/easybuild-framework/pull/1910>`__, `#1917 <https://github.com/hpcugent/easybuild-framework/pull/1917>`__)
  * print message on which extension is being installed, incl. progress counter (`#1886 <https://github.com/hpcugent/easybuild-framework/pull/1886>`__, `#1914 <https://github.com/hpcugent/easybuild-framework/pull/1914>`__)
  * add support for ``--github-org`` to specify GitHub organisation rather than GitHub user (`#1894 <https://github.com/hpcugent/easybuild-framework/pull/1894>`__)
  * add support for running Lmod in debug mode (`#1895 <https://github.com/hpcugent/easybuild-framework/pull/1895>`__)
  * avoid needless use of deepcopy, speed up support for templating in easyconfigs (`#1897 <https://github.com/hpcugent/easybuild-framework/pull/1897>`__)
  * convert ``all_dependencies`` to a property in ``EasyConfig`` class (`#1909 <https://github.com/hpcugent/easybuild-framework/pull/1909>`__)
  * add support for ``--mpi-cmd-template`` (`#1918 <https://github.com/hpcugent/easybuild-framework/pull/1918>`__)
  * add support for ``--disable-mpi-tests`` (`#1920 <https://github.com/hpcugent/easybuild-framework/pull/1920>`__)

* various bug fixes, including:

  * merge with develop when using ``--from-pr`` (`#1838 <https://github.com/hpcugent/easybuild-framework/pull/1838>`__, `#1867 <https://github.com/hpcugent/easybuild-framework/pull/1867>`__)
  * ensure ``--new-pr`` doesn't open empty pull requests (`#1846 <https://github.com/hpcugent/easybuild-framework/pull/1846>`__)
  * better error handling for outdated ``GitPython`` module in ``--check-github`` (`#1847 <https://github.com/hpcugent/easybuild-framework/pull/1847>`__)
  * fix formatting for generated easyblocks documentation (`#1860 <https://github.com/hpcugent/easybuild-framework/pull/1860>`__)
  * make sure the robot ignores filtered dependencies when creating toolchain cache (`#1862 <https://github.com/hpcugent/easybuild-framework/pull/1862>`__)
  * honor ``--filter-deps`` under ``--minimal-toolchains`` (`#1863 <https://github.com/hpcugent/easybuild-framework/pull/1863>`__)
  * correct format for '``param``' and '``author``' tags in docstrings (`#1866 <https://github.com/hpcugent/easybuild-framework/pull/1866>`__)
  * ignore failing bootstrap test in Travis config file (`#1870 <https://github.com/hpcugent/easybuild-framework/pull/1870>`__)
  * make sure all output of executed command is included in generated temporary log file (`#1873 <https://github.com/hpcugent/easybuild-framework/pull/1873>`__, `#1874 <https://github.com/hpcugent/easybuild-framework/pull/1874>`__)
  * ensure ``--show_hidden`` is used in the correct location for '``avail``' with Lmod (`#1875 <https://github.com/hpcugent/easybuild-framework/pull/1875>`__)
  * make sure ``self.path`` is passed down in copy method of ``EasyConfig`` object (`#1884 <https://github.com/hpcugent/easybuild-framework/pull/1884>`__)
  * take into account possible multi-line modloadmsg in ``ModuleGeneratorLua`` (`#1885 <https://github.com/hpcugent/easybuild-framework/pull/1885>`__)
  * fix extracting ``.bz2`` source files (`#1889 <https://github.com/hpcugent/easybuild-framework/pull/1889>`__)
  * don't resolve path to Lmod command (`#1892 <https://github.com/hpcugent/easybuild-framework/pull/1892>`__)
  * fix skipping of stage 0 in bootstrap script (`#1893 <https://github.com/hpcugent/easybuild-framework/pull/1893>`__)
  * fix function signature of ``log.deprecated`` compared to ``fancylogger.deprecated`` (`#1896 <https://github.com/hpcugent/easybuild-framework/pull/1896>`__, `#1899 <https://github.com/hpcugent/easybuild-framework/pull/1899>`__)
  * apply patch to Tcl/C environment modules tool for Tcl 8.6 support in Travis config (`#1901 <https://github.com/hpcugent/easybuild-framework/pull/1901>`__)
  * fix combining ``--extended-dry-run`` with ``--from-pr`` (`#1902 <https://github.com/hpcugent/easybuild-framework/pull/1902>`__)
  * also template dict keys (`#1904 <https://github.com/hpcugent/easybuild-framework/pull/1904>`__)
  * don't pass '``--try-*``' command-line options to EB instance running within job script (`#1908 <https://github.com/hpcugent/easybuild-framework/pull/1908>`__)
  * add workaround for incorrectly passing command line arguments with ``--job`` (`#1915 <https://github.com/hpcugent/easybuild-framework/pull/1915>`__)
  * fix issues with ``--module-only`` (`#1919 <https://github.com/hpcugent/easybuild-framework/pull/1919>`__, `#1924 <https://github.com/hpcugent/easybuild-framework/pull/1924>`__, `#1925 <https://github.com/hpcugent/easybuild-framework/pull/1925>`__)

    * correctly deal with specified start_dir
    * do not remove installation directory when build-in-installdir is enabled

  * make sure '``which``' function returns path to a file (`#1921 <https://github.com/hpcugent/easybuild-framework/pull/1921>`__)
  * fix ``:param:``, ``:return:`` tags in docstrings & add test for it (`#1923 <https://github.com/hpcugent/easybuild-framework/pull/1923>`__)

**easyblocks**

* new easyblocks for 6 software packages that require customized support:

  * cppcheck (`#983 <https://github.com/hpcugent/easybuild-easyblocks/pull/983>`__), HEALPix (`#982 <https://github.com/hpcugent/easybuild-easyblocks/pull/982>`__), IMOD (`#847 <https://github.com/hpcugent/easybuild-easyblocks/pull/847>`__), IronPython (`#321 <https://github.com/hpcugent/easybuild-easyblocks/pull/321>`__), Mono (`#321 <https://github.com/hpcugent/easybuild-easyblocks/pull/321>`__), MyMediaLite (`#321 <https://github.com/hpcugent/easybuild-easyblocks/pull/321>`__)

* various enhancements, including:

  * extend OpenFoam-Extend sanity check for decomp libaries (`#784 <https://github.com/hpcugent/easybuild-easyblocks/pull/784>`__)
  * enhance Java easyblock to support installing Java 6.x (`#940 <https://github.com/hpcugent/easybuild-easyblocks/pull/940>`__)
  * make QuantumESPRESSO easyblock aware of multithreaded FFT (`#954 <https://github.com/hpcugent/easybuild-easyblocks/pull/954>`__)
  * extend PSI easyblock to use PCMSolver and CheMPS2 (`#967 <https://github.com/hpcugent/easybuild-easyblocks/pull/967>`__)
  * make Boost easyblock add definition for ``$BOOST_ROOT`` to generated module file (`#976 <https://github.com/hpcugent/easybuild-easyblocks/pull/976>`__)
  * add support to Bundle easyblock to install list of components (`#980 <https://github.com/hpcugent/easybuild-easyblocks/pull/980>`__)
  * enhance & clean up libxml2 easyblock to also enable installing without Python bindings (`#984 <https://github.com/hpcugent/easybuild-easyblocks/pull/984>`__)
  * update Libint easyblock for Libint 2.1.x (`#985 <https://github.com/hpcugent/easybuild-easyblocks/pull/985>`__)
  * update sanity check for OpenFOAM to support OpenFOAM 4.x (`#986 <https://github.com/hpcugent/easybuild-easyblocks/pull/986>`__)
  * make easyblocks that run MPI tests aware of '``mpi_tests``' build option (`#993 <https://github.com/hpcugent/easybuild-easyblocks/pull/993>`__)

* various bug fixes, including:

  * fix compatibility of OpenFOAM easyblock with ``--module-only`` (`#784 <https://github.com/hpcugent/easybuild-easyblocks/pull/784>`__)
  * fix testing of ``--module-only`` compatibility for OpenFOAM and IMOD easyblocks (`#784 <https://github.com/hpcugent/easybuild-easyblocks/pull/784>`__)
  * add '``include/libxml2``' to ``$CPATH`` in libxml2 easyblock (`#981 <https://github.com/hpcugent/easybuild-easyblocks/pull/981>`__)
  * fix compatibility of IntelBase generic easyblock with ``--module-only`` (`#994 <https://github.com/hpcugent/easybuild-easyblocks/pull/994>`__)
  * make sure correct config script is used for Tcl/Tk deps of R (`#995 <https://github.com/hpcugent/easybuild-easyblocks/pull/995>`__)

**easyconfigs**

* added example easyconfig files for 88 new software packages:

  * ADMIXTURE (`#3359 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3359>`__), angsd (`#3593 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3593>`__), ASHS (`#3429 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3429>`__), AutoDock (`#3465 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3465>`__), AutoGrid (`#3466 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3466>`__), BayeScan (`#2748 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2748>`__, `#3356 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3356>`__),
    BayPass (`#3451 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3451>`__), Bazel (`#3379 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3379>`__), Blender (`#3553 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3553>`__, `#3558 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3558>`__), bwakit (`#3567 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3567>`__), BXH_XCEDE_TOOLS (`#3410 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3410>`__), CastXML (`#3403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3403>`__),
    CHASE (`#3304 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3304>`__), configparser (`#3368 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3368>`__, `#3424 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3424>`__), configurable-http-proxy (`#3380 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3380>`__), cppcheck (`#3508 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3508>`__), CRPropa (`#779 <https://github.com/hpcugent/easybuild-easyconfigs/pull/779>`__),
    DicomBrowser (`#3432 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3432>`__), DMTCP (`#3422 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3422>`__), entrypoints (`#3368 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3368>`__, `#3424 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3424>`__), f90cache (`#3570 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3570>`__), fastPHASE (`#3343 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3343>`__),
    fastQValidator (`#3192 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3192>`__), FFindex (`#1135 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1135>`__), FragGeneScan (`#1198 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1198>`__), gdc-client (`#3399 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3399>`__), gflags (`#3417 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3417>`__), glog (`#3417 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3417>`__),
    GRIT (`#3561 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3561>`__), H5hut (`#3431 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3431>`__), HAPGEN2 (`#3344 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3344>`__), HEALPix (`#779 <https://github.com/hpcugent/easybuild-easyconfigs/pull/779>`__), IMOD (`#1187 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1187>`__, `#3347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3347>`__), IronPython (`#607 <https://github.com/hpcugent/easybuild-easyconfigs/pull/607>`__),
    jhbuild (`#3476 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3476>`__), jupyterhub (`#3380 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3380>`__), Keras (`#3581 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3581>`__), khmer (`#1158 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1158>`__), LeadIT (`#3345 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3345>`__, `#3599 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3599>`__), LevelDB (`#3417 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3417>`__),
    libbitmask (`#3481 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3481>`__), libcpuset (`#3481 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3481>`__), LMDB (`#3417 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3417>`__), log4cplus (`#1136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1136>`__), MACH (`#3346 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3346>`__), Mako (`#3460 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3460>`__), Maq (`#3428 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3428>`__),
    MetaGeneAnnotator (`#3307 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3307>`__), Metal (`#3324 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3324>`__), Mono (`#607 <https://github.com/hpcugent/easybuild-easyconfigs/pull/607>`__), MyMediaLite (`#607 <https://github.com/hpcugent/easybuild-easyconfigs/pull/607>`__), nco (`#2575 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2575>`__), nose-parameterized (`#3579 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3579>`__),
    OpenEXR (`#3553 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3553>`__), OpenImageIO (`#3553 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3553>`__), path.py (`#3368 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3368>`__, `#3424 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3424>`__), PCRE2 (`#3325 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3325>`__), pftoolsV3 (`#3317 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3317>`__), PHASE (`#3385 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3385>`__),
    PLAST (`#3288 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3288>`__), PLINKSEQ (`#3402 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3402>`__), POV-Ray (`#3551 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3551>`__), ProbABEL (`#3108 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3108>`__), prompt-toolkit (`#3368 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3368>`__, `#3424 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3424>`__),
    protobuf-python (`#3563 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3563>`__), PSORTb (`#3317 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3317>`__), py (`#3403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3403>`__, `#3482 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3482>`__), pygccxml (`#3403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3403>`__, `#3482 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3482>`__), pyGIMLi (`#3403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3403>`__, `#3482 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3482>`__),
    pyplusplus (`#3403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3403>`__, `#3482 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3482>`__), PyQt5 (`#3533 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3533>`__), Pyro4 (`#3527 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3527>`__), pytest (`#3403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3403>`__, `#3482 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3482>`__), QCA (`#3595 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3595>`__), RDMC (`#1137 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1137>`__),
    S.A.G.E. (`#3427 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3427>`__), SDL2 (`#3551 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3551>`__), SHORE (`#3531 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3531>`__), SimVascular (`#3555 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3555>`__), SortMeRNA (`#3326 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3326>`__), SUMACLUST (`#3316 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3316>`__),
    SUMATRA (`#3316 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3316>`__), Text-CSV (`#3323 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3323>`__), Triangle (`#3403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3403>`__), VEGAS (`#3457 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3457>`__), VirSorter (`#3307 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3307>`__), wcwidth (`#3368 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3368>`__, `#3424 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3424>`__),
    X11 (`#3340 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3340>`__)

* added new easyconfigs for existing toolchains:

  * CrayGNU + CrayIntel 2016.06 (`#3377 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3377>`__)
  * foss 2016.07 (`#3517 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3517>`__) + 2016.09 (`#3523 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3523>`__)
  * iomkl 2016.07 (`#3458 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3458>`__)
  * pomkl 2016.09 (`#3516 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3516>`__)

* added additional easyconfigs for various supported software packages, including:

  * FFTW 3.3.5, GCC 4.9.4 + 6.2.0, GROMACS 5.1.4, IPython 5.1.0, LLVM 3.9.0, Mesa 12.0.1, OpenCV 3.1.0, OpenFOAM 4.0,
    OpenMPI 2.0.1, ParaView 5.1.2, PGI 16.7, QuantumESPRESSO 5.4.0, Qt5 5.7.0, R-bundle-Bioconductor 3.3, VTK 7.0.0,
    Yade 2016.06a

* various enhancements, including:

  * adjust PSI4 easyconfigs for updated easyblock (`#3312 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3312>`__)
  * clean up libxml2 easyconfigs according to updated libxml2 easyblock (`#3479 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3479>`__, `#3509 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3509>`__)
  * significantly speed up verifying of dumped easyconfig by resorting to 'shallow' parsing (`#3520 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3520>`__)
  * include sanity checks for all MATIO config files (`#3528 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3528>`__)
  * remove ``--with-tcl-config``/``--with-tk-config`` from R easyconfig, already done in R easyblock (`#3580 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3580>`__)

* various bug fixes, including:

  * disable testing in all ParaView 4.4.0 easyconfigs, required download is too much of a PITA (`#3178 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3178>`__)
  * add SQLite as dep to GDAL 2.1.0 easyconfigs (`#3342 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3342>`__)
  * add zlib/SQLite/LibTIFF as dep to R 3.3.1 easyconfigs (`#3342 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3342>`__)
  * add bzip2 as a dependency of freetype (`#3464 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3464>`__)
  * specify correct MPI target in FDS easyconfigs (`#3488 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3488>`__)
  * add tcsh as OS dep in NAMD easyconfigs (`#3491 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3491>`__)
  * statically link ncurses/libreadline in Lua easyconfig with '``dummy``' toolchain (`#3545 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3545>`__)
  * add M4 as dep for flex 2.6.x (`#3542 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3542>`__, `#3550 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3550>`__)
  * add bzip2 and libxcb dependencies to FFmpeg 3.x easyconfigs (`#3548 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3548>`__)
  * make sure & check that Graphviz does not install Tcl bindings in Tcl install prefix (`#3556 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3556>`__)
  * add missing patches for extensions in Python 3.x easyconfigs (`#3557 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3557>`__)
  * add missing XZ dependency to libxml2 2.9.4 easyconfigs, change gettext dep of XZ to build-only dep (`#3568 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3568>`__)
  * enable running of tests for HPCG (`#3578 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3578>`__)
  * fix ``buildopts`` in tabix easyconfigs (`#3584 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3584>`__)

.. _release_notes_eb282:

v2.8.2 (July 13th 2016)
-----------------------

bugfix release

**framework**

* various small enhancements, including:

  * add support for rst output for ``--list-*`` and ``--avail-*`` (`#1339 <https://github.com/hpcugent/easybuild-framework/pull/1339>`__)
  * add support for '``eb --check-conflicts``' (`#1747 <https://github.com/hpcugent/easybuild-framework/pull/1747>`__, `#1807 <https://github.com/hpcugent/easybuild-framework/pull/1807>`__, `#1833 <https://github.com/hpcugent/easybuild-framework/pull/1833>`__)
  * ensure nice error message when non-existing path is passed to ``apply_regex_substitutions`` (`#1788 <https://github.com/hpcugent/easybuild-framework/pull/1788>`__)
  * add check for module output, empty stdout is a sign of trouble with Lmod (`#1793 <https://github.com/hpcugent/easybuild-framework/pull/1793>`__)
  * add multi-threaded FFT to toolchain (`#1802 <https://github.com/hpcugent/easybuild-framework/pull/1802>`__)
  * avoid special characters like '[', ']' in path to temporary directory (`#1808 <https://github.com/hpcugent/easybuild-framework/pull/1808>`__)
  * add support for ``--zip-logs`` (`#1820 <https://github.com/hpcugent/easybuild-framework/pull/1820>`__)
  * add support for ``--extra-modules`` (`#1821 <https://github.com/hpcugent/easybuild-framework/pull/1821>`__)
  * add type conversion for 'checksums' and 'patches' parameter in .yeb easyconfigs (`#1826 <https://github.com/hpcugent/easybuild-framework/pull/1826>`__, `#1840 <https://github.com/hpcugent/easybuild-framework/pull/1840>`__)
  * add support for filtering tests by name (`#1828 <https://github.com/hpcugent/easybuild-framework/pull/1828>`__)
  * add support for ``--avail-toolchain-opts`` (`#1830 <https://github.com/hpcugent/easybuild-framework/pull/1830>`__, `#1839 <https://github.com/hpcugent/easybuild-framework/pull/1839>`__)
  * use absolute path for robot and easyconfig files (`#1834 <https://github.com/hpcugent/easybuild-framework/pull/1834>`__)
  * add backup URL for tarballs hosted on SourceForge in ``install_eb_dep.sh`` script (`#1843 <https://github.com/hpcugent/easybuild-framework/pull/1843>`__)

* various bug fixes, including:

  * fix installation of Lua in ``install_eb_dep.sh`` script (`#1789 <https://github.com/hpcugent/easybuild-framework/pull/1789>`__)
  * fix OpenMP flag for Cray compiler wrappers (`#1794 <https://github.com/hpcugent/easybuild-framework/pull/1794>`__)
  * only reset ``$MODULEPATH`` before loading a module if environment was reset (`#1795 <https://github.com/hpcugent/easybuild-framework/pull/1795>`__)
  * include vsc-install as dependency in ``setup.py`` (`#1805 <https://github.com/hpcugent/easybuild-framework/pull/1805>`__)
  * cache ``$PATH`` & ``$PYTHONPATH`` in test setUp, restore them in tests where '``eb``' is used (`#1806 <https://github.com/hpcugent/easybuild-framework/pull/1806>`__)
  * don't reset ``$MODULEPATH`` in stage 2 of bootstrap script, support forced installation during stage 2 (`#1810 <https://github.com/hpcugent/easybuild-framework/pull/1810>`__)
  * fix issue with templates defined by deps being required while still parsing deps (`#1812 <https://github.com/hpcugent/easybuild-framework/pull/1812>`__)
  * skip unneeded unuse/use commands on tail of ``$MODULEPATH`` in ``check_module_path`` (`#1813 <https://github.com/hpcugent/easybuild-framework/pull/1813>`__)
  * fix auto-convert for all ``*dependencies`` params in ``.yeb`` easyconfigs, ensure version is a string (`#1818 <https://github.com/hpcugent/easybuild-framework/pull/1818>`__)
  * fix ``keyring`` version in Travis config (`#1819 <https://github.com/hpcugent/easybuild-framework/pull/1819>`__)
  * fix dumping of ``.yeb`` easyconfig files in easyconfigs archive (`#1822 <https://github.com/hpcugent/easybuild-framework/pull/1822>`__)
  * fix format of supported easyconfig templates in help output (`#1825 <https://github.com/hpcugent/easybuild-framework/pull/1825>`__)
  * stick to ``pydot`` 1.1.0 for Python 2.6 in Travis config (`#1827 <https://github.com/hpcugent/easybuild-framework/pull/1827>`__)

**easyblocks**

* new easyblocks for 5 software packages that require customized support:

  * Amber (`#958 <https://github.com/hpcugent/easybuild-easyblocks/pull/958>`__), Extrae (`#955 <https://github.com/hpcugent/easybuild-easyblocks/pull/955>`__), Gurobi (`#962 <https://github.com/hpcugent/easybuild-easyblocks/pull/962>`__), Paraver (`#956 <https://github.com/hpcugent/easybuild-easyblocks/pull/956>`__), Tau (`#887 <https://github.com/hpcugent/easybuild-easyblocks/pull/887>`__)

* various enhancements, including:

  * add support for building & installing old GROMACS versions (`#569 <https://github.com/hpcugent/easybuild-easyblocks/pull/569>`__, `#960 <https://github.com/hpcugent/easybuild-easyblocks/pull/960>`__)
  * add support for building Boost with Cray toolchain (`#849 <https://github.com/hpcugent/easybuild-easyblocks/pull/849>`__)
  * libxsmm support for CP2K (`#942 <https://github.com/hpcugent/easybuild-easyblocks/pull/942>`__)
  * pick up specified components for imkl (`#943 <https://github.com/hpcugent/easybuild-easyblocks/pull/943>`__)
  * add support for building GROMACS with double precision (`#946 <https://github.com/hpcugent/easybuild-easyblocks/pull/946>`__, `#960 <https://github.com/hpcugent/easybuild-easyblocks/pull/960>`__)
  * add support for building GROMACS with CUDA support and using dynamic libraries using ``Cray`` toolchains (`#951 <https://github.com/hpcugent/easybuild-easyblocks/pull/951>`__, `#960 <https://github.com/hpcugent/easybuild-easyblocks/pull/960>`__)
  * also install vsc-install in ``EasyBuildMeta`` easyblock, if tarball is provided (`#957 <https://github.com/hpcugent/easybuild-easyblocks/pull/957>`__)
  * enhance PSI easyblock to support PSI4 1.0 (`#965 <https://github.com/hpcugent/easybuild-easyblocks/pull/965>`__)

* various bug fixes, including:

  * also install scripts with MRtrix 0.3.14 (`#941 <https://github.com/hpcugent/easybuild-easyblocks/pull/941>`__)
  * enhance Qt easyblock to support Qt3 (`#944 <https://github.com/hpcugent/easybuild-easyblocks/pull/944>`__)
  * create '``release``' symlink in MRtrix install dir (`#947 <https://github.com/hpcugent/easybuild-easyblocks/pull/947>`__)
  * fix ``make_installdir`` in Inspector & VTune easyblocks (`#952 <https://github.com/hpcugent/easybuild-easyblocks/pull/952>`__)
  * make ``Binary`` and ``MakeCp`` easyblocks aware of '``keepsymlinks``' (`#959 <https://github.com/hpcugent/easybuild-easyblocks/pull/959>`__)
  * correctly define ``$G4*`` environment variables in Geant4 easyblock (`#961 <https://github.com/hpcugent/easybuild-easyblocks/pull/961>`__, `#970 <https://github.com/hpcugent/easybuild-easyblocks/pull/970>`__)
  * prepend tmp install path to ``$PYTHONPATH`` in numpy test step, move to build dir when removing '``numpy``' subdir (`#963 <https://github.com/hpcugent/easybuild-easyblocks/pull/963>`__)
  * correct full path to ALADIN config file & patch it to use right Fortran compiler flags (`#964 <https://github.com/hpcugent/easybuild-easyblocks/pull/964>`__)
  * ensure correct compiler command/flags are used for SAMtools (`#966 <https://github.com/hpcugent/easybuild-easyblocks/pull/966>`__)

**easyconfigs**

* added example easyconfig files for 54 new software packages:

  * Amber (`#3200 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3200>`__), Bullet (`#3175 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3175>`__), CONTRAlign (`#690 <https://github.com/hpcugent/easybuild-easyconfigs/pull/690>`__), Cluster-Buster (`#3191 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3191>`__), damageproto (`#3222 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3222>`__, `#3308 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3308>`__), DCA++ (`#3219 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3219>`__), EIGENSOFT (`#3147 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3147>`__, `#3163 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3163>`__), Extrae (`#507 <https://github.com/hpcugent/easybuild-easyconfigs/pull/507>`__), fdstools (`#3237 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3237>`__), ffnet (`#3273 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3273>`__), GP2C (`#3257 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3257>`__), Gurobi (`#3239 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3239>`__), gc (`#3202 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3202>`__, `#3261 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3261>`__), gputools (`#546 <https://github.com/hpcugent/easybuild-easyconfigs/pull/546>`__), IMa2p (`#3300 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3300>`__), IOzone (`#3253 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3253>`__), i-cisTarget (`#3191 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3191>`__, `#3194 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3194>`__), icmake (`#3243 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3243>`__), io_lib (`#3255 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3255>`__), Kent_tools (`#3191 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3191>`__), libcmaes (`#3256 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3256>`__), libpsortb (`#3259 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3259>`__), libxsmm (`#3099 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3099>`__), MEGACC (`#3263 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3263>`__), MM-align (`#1428 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1428>`__), MOSAIK (`#880 <https://github.com/hpcugent/easybuild-easyconfigs/pull/880>`__), MView (`#1345 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1345>`__), MySQL-python (`#3172 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3172>`__, `#3189 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3189>`__), magma (`#3219 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3219>`__), mrFAST (`#862 <https://github.com/hpcugent/easybuild-easyconfigs/pull/862>`__), mrsFAST (`#862 <https://github.com/hpcugent/easybuild-easyconfigs/pull/862>`__), mysqlclient (`#3172 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3172>`__, `#3232 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3232>`__), NTL (`#3183 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3183>`__), PARI-GP (`#3257 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3257>`__), Paraver (`#508 <https://github.com/hpcugent/easybuild-easyconfigs/pull/508>`__), psutil (`#3171 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3171>`__, `#3231 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3231>`__), PSI4 (`#3293 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3293>`__), Qwt (`#3157 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3157>`__), RMBlast (`#3142 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3142>`__), STAMP (`#3191 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3191>`__), Seqmagick (`#3264 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3264>`__), splitRef (`#946 <https://github.com/hpcugent/easybuild-easyconfigs/pull/946>`__), TAU (`#509 <https://github.com/hpcugent/easybuild-easyconfigs/pull/509>`__), TRF (`#3141 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3141>`__), TVB (`#3053 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3053>`__, `#3247 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3247>`__, `#3251 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3251>`__), TVB-deps (`#3053 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3053>`__, `#3247 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3247>`__, `#3251 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3251>`__), tvb-data (`#3053 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3053>`__, `#3247 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3247>`__, `#3251 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3251>`__), tvb-framework (`#3053 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3053>`__, `#3247 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3247>`__, `#3251 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3251>`__), tvb-library (`#3053 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3053>`__, `#3247 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3247>`__, `#3251 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3251>`__), VampirTrace (`#509 <https://github.com/hpcugent/easybuild-easyconfigs/pull/509>`__), Voro++ (`#3174 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3174>`__), wheel (`#3235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3235>`__), wxPropertyGrid (`#508 <https://github.com/hpcugent/easybuild-easyconfigs/pull/508>`__), xonsh (`#3159 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3159>`__)

* added easyconfigs for update of common toolchains: ``foss/2016b`` (`#3271 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3271>`__), ``intel/2016b`` (`#3270 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3270>`__)
* added new easyconfigs for existing toolchains: ``CrayGNU/2016.03`` & ``CrayGNU/2016.04`` (`#3291 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3291>`__), ``foss/2016.06`` (`#3184 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3184>`__), ``intel/2016.03-GCC-5.4`` (`#3185 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3185>`__)
* added additional easyconfigs for various supported software packages, including:

  * Boost 1.61.0, GCC 5.4.0, GROMACS 3.3.3, HDF5 1.8.17, netCDF 4.4.1, numpy 1.11.0, Perl 5.24.0, PETSc 3.7.2, Python 2.7.12, Python 3.5.2, Qt 3.3.8, R 3.3.1

* various enhancements, including:

  * use ``check_conflicts`` function in easyconfigs tests (`#2981 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2981>`__)
  * also include vsc-install in list of sources for recent EasyBuild easyconfigs, to support offline installation (`#3203 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3203>`__)
  * enable building of ``libmysqld.*`` in MariaDB easyconfigs (`#3230 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3230>`__)
  * add ALDEx2, phyloseq to bundles for Bioconductor 3.2 (`#3211 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3211>`__, `#3241 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3241>`__)
  * add biom, geepack, lubridate, pim to list of R 3.2.3 extensions (`#3186 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3186>`__, `#3211 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3211>`__, `#3275 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3275>`__)

* various bug fixes, including:

  * add patch for Boost 1.60.0 to fix bug resulting in ``TypeError`` (`#3162 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3162>`__)
  * add fftw dependency to CP2K 2.6.0 easyconfigs using CrayGNU (`#3176 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3176>`__)
  * fix location of ``libelf.h``, only (also) installed as ``include/libelf.h`` is there's no ``/usr/include/libelf.h`` (`#3201 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3201>`__)
  * fix software name for Guile & GnuTLS (was 'guile' & 'gnutls') (`#3207 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3207>`__)
  * added missing space in Geant4 configopts to specify ``-DGEANT4_INSTALL_DATA`` (`#3209 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3209>`__)
  * fix Cython download URL in Python 2.7.11 easyconfigs (`#3212 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3212>`__)
  * add missing build deps for X stack in easyconfigs using ``foss/2016a`` or ``intel/2016a`` (`#3222 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3222>`__, `#3308 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3308>`__)
  * fix overruling of exts_list in Perl 5.22.2 easyconfig (`#3224 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3224>`__)
  * add missing dependency on GMP in R 3.2.3 easyconfigs (`#3226 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3226>`__)
  * don't hard specify toolchain for binutils build dep in likwid easyconfig, since it matches parent toolchain (`#3240 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3240>`__)
  * fix ``homepage`` & ``source_urls`` in HMMER easyconfigs (`#3246 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3246>`__)
  * stick to ``pydot`` 1.1.0 for Python 2.6 in Travis config (`#3282 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3282>`__)
  * add ``python-dev(el)`` to OS deps in GC3Pie easyconfigs (`#3310 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3310>`__)

.. _release_notes_eb281:

v2.8.1 (May 30th 2016)
----------------------

bugfix release

**framework**

* various bug fixes, including:

  * fix error message on missing module command in bootstrap script (`#1772 <https://github.com/hpcugent/easybuild-framework/pull/1772>`__)
  * expand '``~``' in paths specified to ``--include-*`` (`#1774 <https://github.com/hpcugent/easybuild-framework/pull/1774>`__)
  * break after deleting cache entry to avoid attempt to delete cache entry again (`#1776 <https://github.com/hpcugent/easybuild-framework/pull/1776>`__)
  * avoid changing ``$MODULEPATH`` when prepending with symlink of path already at head of ``$MODULEPATH`` (`#1777 <https://github.com/hpcugent/easybuild-framework/pull/1777>`__)
  * filter out duplicates in ``find_flexlm_license`` (`#1779 <https://github.com/hpcugent/easybuild-framework/pull/1779>`__)
  * stick with GitPython < 2.0 with Py2.6 in Travis configuration (`#1781 <https://github.com/hpcugent/easybuild-framework/pull/1781>`__)
  * don't use ``LooseVersion`` to define ``version_major``/``version_minor`` (`#1783 <https://github.com/hpcugent/easybuild-framework/pull/1783>`__)


**easyblocks**

* various enhancements, including:

  * update MRtrix easyblock for version 0.3.14 (`#932 <https://github.com/hpcugent/easybuild-easyblocks/pull/932>`__)
  * update Inspector easyblock for recent versions (`#934 <https://github.com/hpcugent/easybuild-easyblocks/pull/934>`__)
  * update VTune easyblock for recent versions (`#935 <https://github.com/hpcugent/easybuild-easyblocks/pull/935>`__)
  * add debug message to IntelBase easyblock w.r.t. switching to 'exist_lic' (`#936 <https://github.com/hpcugent/easybuild-easyblocks/pull/936>`__)


**easyconfigs**

* added example easyconfig files for 13 new software packages:

  * drFAST (`#906 <https://github.com/hpcugent/easybuild-easyconfigs/pull/906>`__), git-lfs (`#2478 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2478>`__), grabix (`#3127 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3127>`__), JWM (`#3007 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3007>`__), libcroco (`#3007 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3007>`__), librsvg (`#3007 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3007>`__), MaCH (`#3136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3136>`__), mayavi (`#3106 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3106>`__), OpenMM (`#2762 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2762>`__), Pysam (`#3080 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3080>`__), SeqPrep (`#3097 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3097>`__), vt (`#3128 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3128>`__), wkhtmltopdf (`#3098 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3098>`__)

* added new easyconfigs for existing toolchains: ``intel/2016.03-GCC-4.9`` (`#3088 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3088>`__)
* added additional easyconfigs for various supported software packages, including:

  * Boost 1.61.0, ESMF 7.0.0, Inspector 2016 update 3, IPython 4.2, netCDF-C++4 4.3.0, netCDF-Fortran 4.4.4,
    Perl 5.22.2, VTune 2016 update 3

* various bug fixes, including:

  * apply libreadline patch to fix bug triggering segmentation fault (`#3086 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3086>`__)

.. _release_notes_eb280:

v2.8.0 (May 18th 2016)
----------------------

feature + bugfix release

**framework**

* significant speedup improvements of EasyBuild itself, thanks to:

  * stop creating ``ModulesTool`` instances over and over again (`#1735 <https://github.com/hpcugent/easybuild-framework/pull/1735>`__)
  * cache result of '``module avail``' calls (`#1742 <https://github.com/hpcugent/easybuild-framework/pull/1742>`__)

* add support for using PGI as toolchain compiler (`#1342 <https://github.com/hpcugent/easybuild-framework/pull/1342>`__, `#1664 <https://github.com/hpcugent/easybuild-framework/pull/1664>`__, `#1759 <https://github.com/hpcugent/easybuild-framework/pull/1759>`__, `#1761 <https://github.com/hpcugent/easybuild-framework/pull/1761>`__, `#1764 <https://github.com/hpcugent/easybuild-framework/pull/1764>`__)

  * incl. new toolchain definitions ``pompi`` and ``pomkl`` (`#1724 <https://github.com/hpcugent/easybuild-framework/pull/1724>`__)

* add test configuration for Travis (`#1733 <https://github.com/hpcugent/easybuild-framework/pull/1733>`__, `#1737 <https://github.com/hpcugent/easybuild-framework/pull/1737>`__, `#1743 <https://github.com/hpcugent/easybuild-framework/pull/1743>`__, `#1767 <https://github.com/hpcugent/easybuild-framework/pull/1767>`__)
* various other enhancements, including:

  * add ``get_total_memory()`` function in ``systemtools`` module (`#1623 <https://github.com/hpcugent/easybuild-framework/pull/1623>`__)
  * ignore ``__init__.py`` files in ``--include-*`` (`#1704 <https://github.com/hpcugent/easybuild-framework/pull/1704>`__)
  * use ``-fopenmp`` rather than ``-openmp`` for Intel compilers, since ``-openmp`` is deprecated (`#1718 <https://github.com/hpcugent/easybuild-framework/pull/1718>`__)
  * add modules to metadata for Cray modules (`#1721 <https://github.com/hpcugent/easybuild-framework/pull/1721>`__)
  * make sure user write permissions are set after failed removal attempt of installation directory (`#1722 <https://github.com/hpcugent/easybuild-framework/pull/1722>`__)
  * escape special characters in software name in ``find_related_easyconfigs`` (`#1726 <https://github.com/hpcugent/easybuild-framework/pull/1726>`__)
  * add support for ``CrayPGI`` compiler toolchain (`#1729 <https://github.com/hpcugent/easybuild-framework/pull/1729>`__)
  * ensure read permission to all installed files for everybody (unless other options specify otherwise) (`#1731 <https://github.com/hpcugent/easybuild-framework/pull/1731>`__)
  * also consider ``$LMOD_CMD`` in bootstrap script (`#1736 <https://github.com/hpcugent/easybuild-framework/pull/1736>`__)
  * translate PyPI download URL to alternate URL with a hash (`#1749 <https://github.com/hpcugent/easybuild-framework/pull/1749>`__)
  * make ``get_software_libdir`` compatible with ``-x`` (`#1750 <https://github.com/hpcugent/easybuild-framework/pull/1750>`__)
  * set ``$LMOD_REDIRECT`` to '``no``' when initialising Lmod (`#1755 <https://github.com/hpcugent/easybuild-framework/pull/1755>`__)
  * add test for broken modules tool setup affecting '``module use``' (`#1758 <https://github.com/hpcugent/easybuild-framework/pull/1758>`__)

* various bug fixes, including:

  * isolate '``options``' tests from easyblocks other than the ones included in the tests (`#1699 <https://github.com/hpcugent/easybuild-framework/pull/1699>`__)
  * don't run '``module purge``' in tests, since EasyBuild may be made available through a module (`#1702 <https://github.com/hpcugent/easybuild-framework/pull/1702>`__)
  * avoid rehandling ``--include-*`` options over and over again during ``--show-config`` (`#1705 <https://github.com/hpcugent/easybuild-framework/pull/1705>`__)
  * remove useless ``test_cwd`` (`#1706 <https://github.com/hpcugent/easybuild-framework/pull/1706>`__)
  * fix bootstrap script: make sure setuptools installed in stage0 is still available at end of stage1 (`#1727 <https://github.com/hpcugent/easybuild-framework/pull/1727>`__)
  * forcibly create target branch in ``--update-pr`` (`#1728 <https://github.com/hpcugent/easybuild-framework/pull/1728>`__)
  * remove check whether '``easybuild``' is being imported from dir that contains ``easybuild/__init__.py`` (`#1730 <https://github.com/hpcugent/easybuild-framework/pull/1730>`__)
  * (re)install vsc-base during stage1 using ``--always-copy`` in bootstrap script, if needed (`#1732 <https://github.com/hpcugent/easybuild-framework/pull/1732>`__)
  * use ``os.path.realpath`` in ``test_wrong_modulepath`` to avoid symlinked path breaking the test (`#1740 <https://github.com/hpcugent/easybuild-framework/pull/1740>`__)
  * unset ``$PYTHONPATH`` in before tested bootstrapped EasyBuild module (`#1743 <https://github.com/hpcugent/easybuild-framework/pull/1743>`__)
  * take into account that paths in modulepath may be symlinks in ``test_module_caches`` (`#1745 <https://github.com/hpcugent/easybuild-framework/pull/1745>`__)
  * change to install dir rather than buildpath in sanity check of extension, latter may not exist (`#1746 <https://github.com/hpcugent/easybuild-framework/pull/1746>`__, `#1748 <https://github.com/hpcugent/easybuild-framework/pull/1748>`__)
  * only load modules using short module names (`#1754 <https://github.com/hpcugent/easybuild-framework/pull/1754>`__)
  * (re)load modules for build deps in extensions_step (`#1762 <https://github.com/hpcugent/easybuild-framework/pull/1762>`__)
  * fix ``modpath_extensions_for method``: take into account modules in Lua syntax (`#1766 <https://github.com/hpcugent/easybuild-framework/pull/1766>`__)
  * fix broken link to VSC website in license headers (`#1768 <https://github.com/hpcugent/easybuild-framework/pull/1768>`__)

**easyblocks**

* add test configuration for Travis (`#895 <https://github.com/hpcugent/easybuild-easyblocks/pull/895>`__, `#897 <https://github.com/hpcugent/easybuild-easyblocks/pull/897>`__, `#900 <https://github.com/hpcugent/easybuild-easyblocks/pull/900>`__, `#926 <https://github.com/hpcugent/easybuild-easyblocks/pull/926>`__)
* new easyblocks for 4 software packages that require customized support:

  * binutils (`#907 <https://github.com/hpcugent/easybuild-easyblocks/pull/907>`__), libQGLViewer (`#890 <https://github.com/hpcugent/easybuild-easyblocks/pull/890>`__), SuperLU (`#860 <https://github.com/hpcugent/easybuild-easyblocks/pull/860>`__), wxPython (`#883 <https://github.com/hpcugent/easybuild-easyblocks/pull/883>`__)

* various other enhancements, including:

  * update SuiteSparse easyblock for version >= 4.5 (`#863 <https://github.com/hpcugent/easybuild-easyblocks/pull/863>`__)
  * enhance imkl easyblock to install on top of PGI (`#866 <https://github.com/hpcugent/easybuild-easyblocks/pull/866>`__, `#916 <https://github.com/hpcugent/easybuild-easyblocks/pull/916>`__)
  * enable runtime logging of install cmd in ``IntelBase`` (`#874 <https://github.com/hpcugent/easybuild-easyblocks/pull/874>`__)
  * enhance Qt easyblock to support installing with ``dummy`` toolchain (`#881 <https://github.com/hpcugent/easybuild-easyblocks/pull/881>`__)
  * delete libnuma symbolic links in PGI installation directory (`#888 <https://github.com/hpcugent/easybuild-easyblocks/pull/888>`__)
  * enhance PDT easyblock to support installing with ``dummy`` toolchain (`#894 <https://github.com/hpcugent/easybuild-easyblocks/pull/894>`__)
  * add support for building Clang with OpenMP support (`#898 <https://github.com/hpcugent/easybuild-easyblocks/pull/898>`__)
  * update Score-P easyblock for additional compilers, MPI libraries & dependencies (`#889 <https://github.com/hpcugent/easybuild-easyblocks/pull/889>`__)
  * drop deprecated '``testrb``' from sanity check in Ruby easyblock (`#901 <https://github.com/hpcugent/easybuild-easyblocks/pull/901>`__)
  * enhance WRF easyblock to support versions >= 3.7 (`#902 <https://github.com/hpcugent/easybuild-easyblocks/pull/902>`__)
  * update QuantumESPRESSO easyblock for version 5.3.0 (`#904 <https://github.com/hpcugent/easybuild-easyblocks/pull/904>`__)
  * add support in PythonPackage easyblock to use '``setup.py develop``' (`#905 <https://github.com/hpcugent/easybuild-easyblocks/pull/905>`__)
  * update Qt easyblock for Qt 5.6.0 (`#908 <https://github.com/hpcugent/easybuild-easyblocks/pull/908>`__)
  * extend bzip2 easyblock to also build dynamic libraries (`#910 <https://github.com/hpcugent/easybuild-easyblocks/pull/910>`__)
  * make threading an explicit option rather than relying on MPI library in SCOTCH easyblock (`#914 <https://github.com/hpcugent/easybuild-easyblocks/pull/914>`__)
  * update PGI easyblock to install siterc file so PGI picks up ``$LIBRARY_PATH`` (`#919 <https://github.com/hpcugent/easybuild-easyblocks/pull/919>`__)
  * enhance sanity check paths for compiler commands in PGI easyblock (`#919 <https://github.com/hpcugent/easybuild-easyblocks/pull/919>`__)
  * also filter out ``-ldl`` from $LIBBLAS & co for Intel MKL in numpy easyblock (`#920 <https://github.com/hpcugent/easybuild-easyblocks/pull/920>`__)
  * define ``$MIC_LD_LIBRARY_PATH`` for impi (`#925 <https://github.com/hpcugent/easybuild-easyblocks/pull/925>`__)

* various bug fixes, including:

  * don't hardcode Python version in ``test_make_module_pythonpackage`` (`#876 <https://github.com/hpcugent/easybuild-easyblocks/pull/876>`__)
  * make PythonPackage easyblock compatible with ``--module-only`` (`#884 <https://github.com/hpcugent/easybuild-easyblocks/pull/884>`__, `#906 <https://github.com/hpcugent/easybuild-easyblocks/pull/906>`__)
  * remove check whether '``easybuild``' is being imported from dir that contains ``easybuild/__init__.py`` (`#891 <https://github.com/hpcugent/easybuild-easyblocks/pull/891>`__)
  * fix passing compiler configure option in PDT easyblock (`#894 <https://github.com/hpcugent/easybuild-easyblocks/pull/894>`__)
  * fix bug in Score-P easyblock w.r.t. ``--with-libbfd`` (`#889 <https://github.com/hpcugent/easybuild-easyblocks/pull/889>`__)
  * fix extension filter for Ruby (`#901 <https://github.com/hpcugent/easybuild-easyblocks/pull/901>`__)
  * fix ``ACTIVATION_TYPES`` list in IntelBase + minor style change (`#913 <https://github.com/hpcugent/easybuild-easyblocks/pull/913>`__)
  * correctly define ``$MIC_LD_LIBRARY_PATH`` in imkl 11.3.x and newer (`#915 <https://github.com/hpcugent/easybuild-easyblocks/pull/915>`__)
  * fix broken link to VSC website in license headers (`#927 <https://github.com/hpcugent/easybuild-easyblocks/pull/927>`__)

**easyconfigs**

* added example easyconfig files for 69 new software packages:

  * ALPS (`#2888 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2888>`__), annovar (`#3010 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3010>`__), BayeScEnv (`#2765 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2765>`__), BayesAss (`#2870 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2870>`__), BerkeleyGW (`#2925 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2925>`__), Blitz++ (`#2784 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2784>`__, `#3004 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3004>`__), bam-readcount (`#2850 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2850>`__), Commet (`#2938 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2938>`__), CrossTalkZ (`#2939 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2939>`__), cuDNN (`#2882 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2882>`__), DBus (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), DFT-D3 (`#2107 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2107>`__), DIAL (`#3056 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3056>`__), dask (`#2885 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2885>`__), dbus-glib (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), FFLAS-FFPACK (`#2793 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2793>`__), FLAC (`#2824 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2824>`__), FLANN (`#3015 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3015>`__, `#3029 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3029>`__), FLEUR (`#3043 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3043>`__), GConf (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), GROMOS++ (`#1297 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1297>`__), GST-plugins-base (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), GStreamer (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), GTOOL (`#2805 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2805>`__), Givaro (`#2793 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2793>`__), gdist (`#2935 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2935>`__), gromosXX (`#1297 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1297>`__), HISAT2 (`#2809 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2809>`__), i-PI (`#2940 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2940>`__), Kraken (`#3037 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3037>`__, `#3041 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3041>`__), LAME (`#2823 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2823>`__), LASTZ (`#3002 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3002>`__), LinBox (`#2793 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2793>`__), Loki (`#2839 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2839>`__), libQGLViewer (`#2923 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2923>`__, `#3008 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3008>`__), libXxf86vm (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), MDSplus (`#2787 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2787>`__, `#2838 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2838>`__, `#3027 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3027>`__), MRIcron (`#2831 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2831>`__), Mawk (`#2732 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2732>`__), minieigen (`#2839 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2839>`__), mpmath (`#3058 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3058>`__), NBO (`#3047 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3047>`__, 3048), NGS (`#2803 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2803>`__), NGS-Python (`#2810 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2810>`__), ncbi-vdb (`#2808 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2808>`__), OptiX (`#2795 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2795>`__), PCL (`#3024 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3024>`__), PEAR (`#2731 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2731>`__), PLplot (`#2990 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2990>`__), Postgres-XL (`#2891 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2891>`__), PyGTS (`#2969 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2969>`__), RSeQC (`#2788 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2788>`__), Rust (`#2920 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2920>`__, `#2943 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2943>`__), rainbow (`#2730 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2730>`__), SHAPEIT (`#2806 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2806>`__), SIONlib (`#2908 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2908>`__), Saxon-HE (`#2773 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2773>`__), Singularity (`#2901 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2901>`__), SoX (`#2825 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2825>`__), Subread (`#2790 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2790>`__), SuperLU (`#2665 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2665>`__), travis (`#2953 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2953>`__), VASP (`#2950 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2950>`__), Wannier90 (`#2906 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2906>`__, `#3042 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3042>`__), wget (`#3041 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3041>`__), wxPython (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), xf86vidmodeproto (`#2855 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2855>`__), Yade (`#2839 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2839>`__), Yambo (`#2932 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2932>`__)

* add test configuration for Travis (`#2942 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2942>`__, `#2944 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2944>`__, `#2954 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2954>`__, `#3061 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3061>`__)
* added easyconfigs for new PGI-based toolchains

  * ``pomkl/2016.03`` (`#2899 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2899>`__, `#2900 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2900>`__, `#3046 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3046>`__), ``pomkl/2016.04`` (`#3044 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3044>`__), ``CrayPGI/2016.04`` (`#2927 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2927>`__)

* added new easyconfigs for existing toolchains:

  * ``foss/2016.04`` (`#3013 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3013>`__), ``intel/2016.02-GCC-5.3`` (`#2523 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2523>`__), ``intel/2016.03-GCC-5.3`` (`#3009 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3009>`__)

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * incl. CGAL 4.8, Clang 3.8.0, icc/ifort 2016.2.181 & 2016.3.210, imkl 11.3.2.181 & 11.3.3.210, impi 5.1.3.181,
    LLVM 3.8.0, OpenCV 2.4.12, pandas 0.18.0, Qt 5.6.0, Scalasca 2.3, Score-P 2.0.1, SuiteSparse 4.5.2, WRF 3.8

* various other enhancements, including:

  * enhance ORCA easyconfig for compatibility with SLURM (`#1819 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1819>`__)
  * enable ``-fPIC`` in GraphicsMagick easyconfig, required by Octave (`#2764 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2764>`__)
  * clean up binutils easyconfigs to use binutils easyblock (`#3006 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3006>`__)
  * add ``include/GraphicsMagick`` to ``$CPATH`` in GraphicsMagick easyconfigs (`#3034 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3034>`__)
  * update SuiteSparse easyconfigs according to updated SuiteSparse easyblock (`#3050 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3050>`__)

* various bug fixes, including:

  * fix Perl extensions download urls (`#2738 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2738>`__)
  * add Autoconf as build dep for ``GCCcore`` (`#2772 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2772>`__)
  * fix versions of extensions in Bioconductor 3.2 bundles (`#2769 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2769>`__)
  * fix (build) deps for ``intel/2016a`` easyconfigs of cairo, libXext, libXrender (`#2785 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2785>`__, `#2874 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2874>`__)
  * use '``env``' wherever preconfig/build/installopts is used to set environmental variables (`#2807 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2807>`__, `#2811 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2811>`__, `#2812 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2812>`__)
  * add zlib as explicit dep in Tk easyconfigs (`#2815 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2815>`__)
  * consistently specify to use ``-fgnu89-inline`` flag in M4 1.4.17 easyconfigs (`#2774 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2774>`__, `#2779 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2779>`__, `#2816 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2816>`__)
  * fix homepage and description in Pygments easyconfigs (`#2822 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2822>`__)
  * include pkg-config as build dependencies for libXau, libXdmcp, libxcb (`#2827 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2827>`__)
  * consistently use ``XORG_*_SOURCE`` constants (`#2829 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2829>`__, `#2830 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2830>`__, `#2848 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2848>`__)
  * update source URLs in ScientificPython easyconfig files (`#2847 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2847>`__)
  * add checksums in SuiteSparse easyconfigs (`#2849 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2849>`__)
  * fix build deps for GObject-Introspection (`#2852 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2852>`__)
  * correctly specify Perl location in git easyconfig (`#2866 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2866>`__)
  * fix bitstring 3.1.3 download URL in Python easyconfigs, source tarball on PyPI disappeared (`#2880 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2880>`__)
  * fix Perl dependency in worker easyconfigs, it requires non-standard Perl modules (`#2884 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2884>`__)
  * add XZ as dependency in Python 3.5.1 easyconfigs, required for lzma (`#2887 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2887>`__)
  * fix download URL for packmol (`#2902 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2902>`__)
  * drop ``usempi`` toolchain in numexpr easyconfigs, not needed (`#2937 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2937>`__)
  * fix use of ``resolve_dependencies`` in tests according to changes in framework (`#2952 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2952>`__)
  * add dependency extensions for MarkupSafe and jsonscheme in IPython 3.2.3 easyconfigs (`#2967 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2967>`__)
  * add patch for matplotlib 1.5.1 to fix Tcl/Tk library paths being used (`#2971 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2971>`__)
  * add xproto build dependency for makedepend v1.0.5 (`#2982 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2982>`__)
  * disable parallel build for Doxygen (`#2986 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2986>`__)
  * fix source URLs for ``FreezeThaw`` and ``Tie::Function`` extensions for Perl v5.22.1 (`#2988 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2988>`__)
  * add ``sed`` command in worker easyconfig files to fix module_path in conf/worker.conf (`#2997 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2997>`__, `#3000 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3000>`__)
  * drop toolchainopts from Eigen easyconfigs, since it is headers-only (`#3025 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3025>`__)
  * clean up dummy bzip2 easyconfig, define buildopts rather than defining ``$CC`` and ``$CFLAGS`` via ``os.environ`` (`#3036 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3036>`__)
  * use ``%(pyshortver)s`` template rather than hardcoding 2.7 in VTK easyconfigs (`#3052 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3052>`__)
  * correct install location of OpenCV Python bindings (`#3054 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3054>`__)
  * include XZ as dependency for libunwind (`#3055 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3055>`__)
  * add patch to fix broken OpenSSL tests due to expired certificates (`#3057 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3057>`__)
  * fix broken link to VSC website in license headers (`#3062 <https://github.com/hpcugent/easybuild-easyconfigs/pull/3062>`__)

.. _release_notes_eb270:

v2.7.0 (March 20th 2016)
------------------------

feature + bugfix release

**framework**

* stabilize Cray support

  * enable '``dynamic``' toolchain option by default for ``Cray*`` toolchains (`#1581 <https://github.com/hpcugent/easybuild-framework/pull/1581>`__)
  * remove FFTW from the Cray toolchains definition (`#1585 <https://github.com/hpcugent/easybuild-framework/pull/1585>`__)
  * add external modules metadata for Cray systems (`#1638 <https://github.com/hpcugent/easybuild-framework/pull/1638>`__)
  * fix independency of Cray toolchains w.r.t. toolchain build environment (`#1641 <https://github.com/hpcugent/easybuild-framework/pull/1641>`__, `#1647 <https://github.com/hpcugent/easybuild-framework/pull/1647>`__)
  * remove requirement to use ``--experimental`` for Cray toolchains (`#1663 <https://github.com/hpcugent/easybuild-framework/pull/1663>`__)

* enable Python optimization mode in '``eb``' (`#1357 <https://github.com/hpcugent/easybuild-framework/pull/1357>`__)
* improved GitHub integration

  * improve error handling on git commands + better logging for ``--new-pr``/``--update-pr`` (`#1590 <https://github.com/hpcugent/easybuild-framework/pull/1590>`__)
  * use ``git`` rather than ``https`` in ``--new-pr``/``--update-pr`` (`#1602 <https://github.com/hpcugent/easybuild-framework/pull/1602>`__)
  * add ``-u`` as shorthand for ``--upload-test-report`` (`#1605 <https://github.com/hpcugent/easybuild-framework/pull/1605>`__)
  * fix ``--from-pr`` for PRs that include renamed/deleted files (`#1615 <https://github.com/hpcugent/easybuild-framework/pull/1615>`__)
  * add support for ``--install-github-token`` and ``--check-github`` (`#1616 <https://github.com/hpcugent/easybuild-framework/pull/1616>`__)
  * fix ``fetch_easyconfigs_from_pr`` w.r.t. duplicate files in PRs (`#1628 <https://github.com/hpcugent/easybuild-framework/pull/1628>`__)

* various other enhancements, including:

  * add support for ``--search-filename`` and ``--terse`` (`#1577 <https://github.com/hpcugent/easybuild-framework/pull/1577>`__)
  * support complete bash completion (`#1580 <https://github.com/hpcugent/easybuild-framework/pull/1580>`__)
  * add support for ``%(*ver)s`` and ``%(*shortver)s`` templates (`#1595 <https://github.com/hpcugent/easybuild-framework/pull/1595>`__, `#1604 <https://github.com/hpcugent/easybuild-framework/pull/1604>`__)

    * incl. ``%(javaver)s``, ``%(javashortver)s``, ``%(perlver)s``, ``%(perlshortver)s``, ``%(pyver)s``, ``%(pyshortver)s``, ``%(rver)s``, ``%(rshortver)s``

  * define ``HOME`` constant that can be used in easyconfig files (`#1607 <https://github.com/hpcugent/easybuild-framework/pull/1607>`__)
  * implement support for generating '``swap``' statements in module files (`#1609 <https://github.com/hpcugent/easybuild-framework/pull/1609>`__)
  * add support for ``--show-config`` (`#1611 <https://github.com/hpcugent/easybuild-framework/pull/1611>`__, `#1620 <https://github.com/hpcugent/easybuild-framework/pull/1620>`__)
  * simplified support for ``--minimal-toolchains`` (`#1614 <https://github.com/hpcugent/easybuild-framework/pull/1614>`__, `#1619 <https://github.com/hpcugent/easybuild-framework/pull/1619>`__, `#1622 <https://github.com/hpcugent/easybuild-framework/pull/1622>`__, `#1625 <https://github.com/hpcugent/easybuild-framework/pull/1625>`__, `#1646 <https://github.com/hpcugent/easybuild-framework/pull/1646>`__)
  * add support for ``--dump-env-script`` (`#1624 <https://github.com/hpcugent/easybuild-framework/pull/1624>`__)
  * enhance ModulesTool.exist to also recognize partial module names (`#1630 <https://github.com/hpcugent/easybuild-framework/pull/1630>`__)
  * improve error message for toolchain definition errors (`#1631 <https://github.com/hpcugent/easybuild-framework/pull/1631>`__)
  * make default is_short_modname_for check less strict to support versionless external modules as deps (`#1632 <https://github.com/hpcugent/easybuild-framework/pull/1632>`__)
  * mention hostname in comment made by ``--upload-test-report`` (`#1635 <https://github.com/hpcugent/easybuild-framework/pull/1635>`__)
  * support providing additional relative path for prefix in external module metadata (`#1637 <https://github.com/hpcugent/easybuild-framework/pull/1637>`__)
  * add ``ThematicModuleNamingScheme`` (`#1645 <https://github.com/hpcugent/easybuild-framework/pull/1645>`__)
  * enhance logging format: remove logger name, mention location instead (`#1649 <https://github.com/hpcugent/easybuild-framework/pull/1649>`__, `#1654 <https://github.com/hpcugent/easybuild-framework/pull/1654>`__)
  * update kernel versions for SLES12 (`#1659 <https://github.com/hpcugent/easybuild-framework/pull/1659>`__)
  * raise ``EasyBuildError`` rather than ``ImportError`` in ``only_if_module_is_available`` decorator (`#1662 <https://github.com/hpcugent/easybuild-framework/pull/1662>`__)

* various bug fixes, including:

  * fix Lmod spider output in generated modules (`#1583 <https://github.com/hpcugent/easybuild-framework/pull/1583>`__)
  * correctly define '``easybuild``' namespaces (`#1593 <https://github.com/hpcugent/easybuild-framework/pull/1593>`__, `#1666 <https://github.com/hpcugent/easybuild-framework/pull/1666>`__, `#1680 <https://github.com/hpcugent/easybuild-framework/pull/1680>`__)

    * this change requires that the ``setuptools`` Python package is available (at runtime)
    * using custom easyblocks by adding them in the Python search path (``$PYTHONPATH``) may require adjustments,
      i.e. also using ``pkg_resources.declare_namespace`` in the ``__init__.py`` files;
      *we highly recommend to use* ``--include-easyblocks`` *instead*,
      see http://easybuild.readthedocs.org/en/latest/Including_additional_Python_modules.html
    * note: this has the side-effect of not being able anymore to reliably use '``eb``' in the parent directory of
      the easybuild-framework repository (`#1667 <https://github.com/hpcugent/easybuild-framework/pull/1667>`__)

  * fix template for ``savannah.gnu.org`` source URL (`#1601 <https://github.com/hpcugent/easybuild-framework/pull/1601>`__)
  * stop running '``module purge``', only restore environment (`#1608 <https://github.com/hpcugent/easybuild-framework/pull/1608>`__)
  * fix license headers: Hercules foundation is now FWO (`#1629 <https://github.com/hpcugent/easybuild-framework/pull/1629>`__)
  * avoid that ``fancylogger`` tries to import ``mpi4py`` to determine MPI rank (`#1648 <https://github.com/hpcugent/easybuild-framework/pull/1648>`__)
  * fix error in tests when '``file``' backend is not available in Python keyring (`#1650 <https://github.com/hpcugent/easybuild-framework/pull/1650>`__)
  * update develop install script (`#1651 <https://github.com/hpcugent/easybuild-framework/pull/1651>`__)
  * handle allowed system deps during ``prepare_step`` rather than during parsing of easyconfig (`#1652 <https://github.com/hpcugent/easybuild-framework/pull/1652>`__)
  * add function to find FlexLM licenses: ``find_flexlm_license`` (`#1633 <https://github.com/hpcugent/easybuild-framework/pull/1633>`__, `#1653 <https://github.com/hpcugent/easybuild-framework/pull/1653>`__)
  * fix availability check for external modules with partial module name (`#1634 <https://github.com/hpcugent/easybuild-framework/pull/1634>`__, `#1643 <https://github.com/hpcugent/easybuild-framework/pull/1643>`__)
  * fix bootstrap script to ensure ``setuptools`` is also installed (`#1655 <https://github.com/hpcugent/easybuild-framework/pull/1655>`__)
  * fix issue in bootstrap script with ``vsc-base`` being picked up from the OS (`#1656 <https://github.com/hpcugent/easybuild-framework/pull/1656>`__)
  * fix bootstrap script for environment where '``python``' is Python 3.x (`#1660 <https://github.com/hpcugent/easybuild-framework/pull/1660>`__)
  * remove ``--experimental`` for tests related to ``--package`` (`#1665 <https://github.com/hpcugent/easybuild-framework/pull/1665>`__)
  * ensure path to setuptools is included in ``$PYTHONPATH`` being used to test scripts (`#1671 <https://github.com/hpcugent/easybuild-framework/pull/1671>`__)
  * sanitize environment before initializing easyblocks (`#1676 <https://github.com/hpcugent/easybuild-framework/pull/1676>`__)
  * remove ``reload`` statements in ``include.py``, since they are not required and break ``--include-toolchains`` (`#1679 <https://github.com/hpcugent/easybuild-framework/pull/1679>`__)


**easyblocks**

* new easyblocks for 6 software packages that require customized support:

  *  ADF (`#826 <https://github.com/hpcugent/easybuild-easyblocks/pull/826>`__), MPICH (`#844 <https://github.com/hpcugent/easybuild-easyblocks/pull/844>`__, `#852 <https://github.com/hpcugent/easybuild-easyblocks/pull/852>`__, `#868 <https://github.com/hpcugent/easybuild-easyblocks/pull/868>`__), mutil (`#859 <https://github.com/hpcugent/easybuild-easyblocks/pull/859>`__), pplacer (`#835 <https://github.com/hpcugent/easybuild-easyblocks/pull/835>`__), psmpi (`#852 <https://github.com/hpcugent/easybuild-easyblocks/pull/852>`__), SNPhylo (`#865 <https://github.com/hpcugent/easybuild-easyblocks/pull/865>`__)

* various other enhancements, including:

  * implement support for '``use_pip``' in PythonPackage easyblock (`#719 <https://github.com/hpcugent/easybuild-easyblocks/pull/719>`__, `#831 <https://github.com/hpcugent/easybuild-easyblocks/pull/831>`__)
  * add support in CUDA easyblock to install wrappers for host compilers (`#758 <https://github.com/hpcugent/easybuild-easyblocks/pull/758>`__)
  * update sanity check for picard version 1.124 and above (`#796 <https://github.com/hpcugent/easybuild-easyblocks/pull/796>`__)
  * use '``module swap``' for all components in ``CrayToolchain`` (`#823 <https://github.com/hpcugent/easybuild-easyblocks/pull/823>`__)
  * update PSI4 easyblock to cope with changed name of PSI4 data dir (`#824 <https://github.com/hpcugent/easybuild-easyblocks/pull/824>`__)
  * use ``find_flexlm_license`` function and avoid defining ``$CPATH`` in PGI easyblock (`#837 <https://github.com/hpcugent/easybuild-easyblocks/pull/837>`__)
  * use ``find_flexlm_license`` function in ``IntelBase`` generic easyblock (`#839 <https://github.com/hpcugent/easybuild-easyblocks/pull/839>`__)
  * add unit test to check module file generated by ``PythonPackage`` easyblock (`#841 <https://github.com/hpcugent/easybuild-easyblocks/pull/841>`__)
  * rework MVAPICH2 easyblock on top of new MPICH easyblock (`#844 <https://github.com/hpcugent/easybuild-easyblocks/pull/844>`__)
  * add CUDA support in CP2K easyblock (`#850 <https://github.com/hpcugent/easybuild-easyblocks/pull/850>`__)
  * also define ``$LD`` in ``buildopts`` for GATE (`#855 <https://github.com/hpcugent/easybuild-easyblocks/pull/855>`__)
  * use ``find_flexlm_license`` function in TotalView easyblock (`#839 <https://github.com/hpcugent/easybuild-easyblocks/pull/839>`__)
  * enhance ``MakeCp`` easyblock to also support renaming of files while copying them (`#859 <https://github.com/hpcugent/easybuild-easyblocks/pull/859>`__)
  * hunt for usable '``python``' command in ``PythonPackage`` easyblock when system Python is used (`#861 <https://github.com/hpcugent/easybuild-easyblocks/pull/861>`__)
  * add sanity check in ``easybuild/__init__.py`` w.r.t. current working dir (`#869 <https://github.com/hpcugent/easybuild-easyblocks/pull/869>`__)
  * change suffix of original file to ``.easybuild`` when using ``fileinput`` in impi easyblock (`#870 <https://github.com/hpcugent/easybuild-easyblocks/pull/870>`__)

* various bug fixes, including:

  * make sure Python unicode settings match that of the system Python (`#817 <https://github.com/hpcugent/easybuild-easyblocks/pull/817>`__)
  * remove FFTW related statements in HPL easyblock, since HPL doesn't require FFTW at all (`#822 <https://github.com/hpcugent/easybuild-easyblocks/pull/822>`__)
  * use ``pkg_resources.declare_namespace`` rather than ``pkgutil.extend_path`` to declare '``easybuild``' namespaces (`#827 <https://github.com/hpcugent/easybuild-easyblocks/pull/827>`__)
  * fix license headers: Hercules foundation is now FWO (`#836 <https://github.com/hpcugent/easybuild-easyblocks/pull/836>`__)
  * fix check for non-empty lib dirs in ``PythonPackage`` easyblock (`#840 <https://github.com/hpcugent/easybuild-easyblocks/pull/840>`__)
  * consider all Python lib dirs in sanity check for libxml2 (`#842 <https://github.com/hpcugent/easybuild-easyblocks/pull/842>`__)
  * correctly handle deprecated configure options (``--with-hwloc``/``--enable-mpe``) in MVAPICH2 easyblock (`#853 <https://github.com/hpcugent/easybuild-easyblocks/pull/853>`__)
  * use correct configure option for checkpoint/restart in MVAPICH2 easyblock (`#854 <https://github.com/hpcugent/easybuild-easyblocks/pull/854>`__)
  * ensure list of Python lib dirs always has a '``lib/...``' entry (`#858 <https://github.com/hpcugent/easybuild-easyblocks/pull/858>`__)
  * check whether ``rpm``/``rpmrebuild`` commands are available using '``which``', rather than checking for OS deps (`#864 <https://github.com/hpcugent/easybuild-easyblocks/pull/864>`__)
  * fix ``test_step`` in UFC easyblock (`#872 <https://github.com/hpcugent/easybuild-easyblocks/pull/872>`__)

**easyconfigs**

* added example easyconfig files for 63 new software packages:

  * ATSAS (`#616 <https://github.com/hpcugent/easybuild-easyconfigs/pull/616>`__, `#2587 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2587>`__), astropy (`#2724 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2724>`__, `#2727 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2727>`__), attr (`#2706 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2706>`__), BamUtil (`#2654 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2654>`__), BBMap (`#2322 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2322>`__), BH (`#2508 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2508>`__),
    CheMPS2 (`#2445 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2445>`__), CosmoloPy (`#2723 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2723>`__, `#2727 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2727>`__), csvkit (`#2639 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2639>`__), Firefox (`#2648 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2648>`__), FreeXL (`#2422 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2422>`__), GL2PS (`#2667 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2667>`__),
    Glade (`#2631 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2631>`__), htop (`#2538 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2538>`__), IGV (`#2019 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2019>`__), IGVTools (`#2019 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2019>`__), ImageMagick (`#2438 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2438>`__), jModelTest (`#2529 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2529>`__),
    KEALib (`#2420 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2420>`__), libcerf (`#2656 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2656>`__), libgcrypt (`#2201 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2201>`__), libglade (`#2631 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2631>`__), libgpg-error (`#2201 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2201>`__), libspatialite (`#2431 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2431>`__),
    LittleCMS (`#2438 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2438>`__), MAST (`#2542 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2542>`__), MLC (`#2577 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2577>`__), MPJ-Express (`#2529 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2529>`__), mutil (`#2201 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2201>`__), neon (`#758 <https://github.com/hpcugent/easybuild-easyconfigs/pull/758>`__), NextClip (`#2544 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2544>`__),
    npstat (`#2686 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2686>`__, `#2703 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2703>`__), Octopus (`#2643 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2643>`__), QuickFF (`#2721 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2721>`__), p4vasp (`#2328 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2328>`__), PCMSolver (`#2445 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2445>`__), PFFT (`#2643 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2643>`__),
    PHYLIP (`#2694 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2694>`__), pkgconfig (`#2475 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2475>`__, `#2476 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2476>`__), Platypus (`#2618 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2618>`__), pplacer (`#1056 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1056>`__), PRINSEQ (`#2437 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2437>`__, `#2444 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2444>`__, `#2585 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2585>`__),
    PyFFmpeg (`#2501 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2501>`__, `#2519 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2519>`__), PyGObject (`#2443 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2443>`__), PyGTK (`#2443 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2443>`__), PyOpenGL (`#2628 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2628>`__), pyringe (`#2533 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2533>`__), qrupdate (`#2675 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2675>`__),
    rgeos (`#2635 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2635>`__), rpmrebuild (`#2402 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2402>`__), shift (`#2201 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2201>`__), SNAPE-pooled (`#2688 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2688>`__), SNPhylo (`#2701 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2701>`__), sratoolkit (`#2715 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2715>`__),
    STAR-Fusion (`#2463 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2463>`__), statsmodels (`#2719 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2719>`__), StringTie (`#2527 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2527>`__), synchronicity (`#2508 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2508>`__), testpath (`#2461 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2461>`__),
    USEARCH (`#2537 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2537>`__), VarScan (`#2464 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2464>`__), vsc-install (`#2165 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2165>`__), Whoosh (`#2725 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2725>`__), xprop (`#2645 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2645>`__)

* added new easyconfigs for existing toolchains:

  * ``intel/2016.02-GCC-4.9`` (`#2620 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2620>`__), ``gmpolf/2016a`` & ``gmvolf/2016a`` (`#2589 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2589>`__)

* stable Cray-specific easyconfigs

  * delete deprecated Cray toolchains and easyconfig files (`#2400 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2400>`__)
  * don't hardcode ``PrgEnv`` version, remove ``craype`` and ``fftw`` components in Cray toolchains (`#2554 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2554>`__)
  * remove ``-XC`` versionsuffix for stable definitions for ``Cray*`` toolchains (`#2714 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2714>`__)
  * support for various software packages with ``CrayGNU`` and ``CrayIntel`` toolchains: CP2K, GROMACS, WRF

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including BWA 0.7.13, CMake 3.4.3, GATE 7.2, GROMACS 5.1.2, Mesa 11.1.2, netCDF 4.4.0, Perl 5.22.1, Python 3.5.1,
    R 3.2.3, R-bundle-Bioconductor 3.2, scipy 0.17.0, SuiteSparse 4.5.1

* various other enhancements, including:

  * copy ``contrib`` dir in Velvet easyconfigs so scripts are also available (`#2456 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2456>`__)
  * redefine matplotlib 1.5.1 easyconfig as a bundle, also include ``cycler`` extension (dep for matplotlib) (`#2470 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2470>`__)
  * add bitstring extension to Python 2.7.11 easyconfigs (`#2471 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2471>`__)
  * enable building of MetaVelvet in Velvet 1.2.10 easyconfigs (`#2473 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2473>`__)
  * add custom sanity check for libjpeg-turbo (`#2480 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2480>`__)
  * add Velvet easyconfigs that include BioPerl dependency, so VelvetOptimizer can use it (`#2495 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2495>`__, `#2729 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2729>`__, `#2733 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2733>`__)
  * add source URL in RAxML 7.2.6 easyconfigs (`#2536 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2536>`__)
  * update MPICH easyconfigs to use new MPICH easyblock (`#2589 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2589>`__)
  * free libX11 & co from unneeded Python dependency/versionsuffix (`#2549 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2549>`__, `#2563 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2563>`__, `#2605 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2605>`__, `#2664 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2664>`__)
  * add '``--enable-utf --enable-unicode-properties``' configure options in PCRE easyconfigs (`#2561 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2561>`__)
    * required for latest R versions
  * add HCsnip, metagenomeSeq in Bioconductor 3.1 bundles (`#2553 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2553>`__, `#2578 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2578>`__)
  * add additional extensions in R 3.2.x easyconfigs that are required for extra Bioconductor extensions (`#2547 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2547>`__, `#2556 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2556>`__)
  * update psmpi easyconfig files to use the new psmpi easyblock (`#2619 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2619>`__)
  * add easyconfig for Python 2.7.11 on top of X11-enabled Tk (`#2614 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2614>`__, `#2621 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2621>`__)
  * add virtualenv as extension in Python 2.7.11 easyconfigs (`#2660 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2660>`__)

* various bug fixes, including:

  * fix software name for GTK+ (was 'gtk+'), PyCairo (was 'pycairo') and Gdk-Pixbuf (was 'gdk-pixbuf') (`#2468 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2468>`__)
  * don't hardcode ``CC``/``CXX`` in OpenMPI easyconfigs (`#2472 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2472>`__)
  * remove Google Code source URL for mpi4py (`#2474 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2474>`__)
  * rename ffmpeg to FFmpeg (`#2425 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2425>`__, `#2481 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2481>`__)
  * use available easyblock for flex (`#2486 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2486>`__)
  * fix determining list of easyconfigs in unit test suite, don't assume locations are correct (`#2530 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2530>`__)
  * fix specifying DB dependency in DB_File easyconfigs (`#2539 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2539>`__)
  * remove hard-coded ``-xSSE4.2`` for numpy/scipy with Intel compilers (`#2546 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2546>`__)
  * fix license headers: Hercules foundation is now FWO (`#2550 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2550>`__)
  * add ``--with-zlib`` configure argument in libxml easyconfigs (`#2555 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2555>`__)
  * don't hardcode ``optarch=True`` in xextproto/xtrans easyconfigs (`#2601 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2601>`__)
  * change toolchain version to '' in easyconfigs that use ``dummy`` toolchain and include dependencies (`#2612 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2612>`__)
  * GLib doesn't require libxml2 with Python bindings (`#2632 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2632>`__)
  * add patch file to imkl 10.2.6.038 32-bit easyconfig to fix installer not being able to deal with '``--``' in build path (`#2634 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2634>`__)
  * add missing 'pkgconfig' dependency for h5py (`#2476 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2476>`__, `#2650 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2650>`__)
  * correct software name in FastQC easyconfigs (was 'fastqc'), use '``dummy``' toolchain for all FastQC version (`#2657 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2657>`__, `#2666 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2666>`__)
  * add missing libxml2 dependencies in GLib easyconfigs (`#2658 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2658>`__)
  * fix Xerces-C++ download location (`#2668 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2668>`__)
  * enable ``XML::Bare`` extension in all Perl easyconfigs (`#2672 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2672>`__)
  * update dead link for SuiteSparse (`#2679 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2679>`__)
  * remove custom ``exts_filter`` in easyconfigs used ``PythonPackage`` easyblock (`#2683 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2683>`__, `#2685 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2685>`__)
  * add M4 as build dep for binutils & flex (`#2681 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2681>`__)
  * add missing dependencies in Python 3.5.x easyconfigs: SQLite, Tk, GMP (`#2704 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2704>`__)
  * fix (OS) deps, add checksums, remove parameter definition with default values in MVAPICH2 easyconfigs (`#2707 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2707>`__)

* style cleanup in various easyconfigs (`#2378 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2378>`__, `#2387 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2387>`__, `#2395 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2395>`__, `#2396 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2396>`__, `#2488 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2488>`__-`#2493 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2493>`__, `#2496 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2496>`__-`#2500 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2500>`__, `#2502 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2502>`__-`#2504 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2504>`__, `#2602 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2602>`__)

  * working towards automated style review of pull requests

.. _release_notes_eb260:

v2.6.0 (January 26th 2016)
--------------------------

feature + bugfix release

**framework**

* add (experimental) support for opening/updating (easyconfigs) pull requests (``--new-pr``, ``--update-pr``) (`#1528 <https://github.com/hpcugent/easybuild-framework/pull/1528>`__)
* sanitize environment before each installation by undefining ``$PYTHON*`` (`#1569 <https://github.com/hpcugent/easybuild-framework/pull/1569>`__, `#1572 <https://github.com/hpcugent/easybuild-framework/pull/1572>`__)
* various other enhancements, including:

  * allow user-local modules with hierarchical naming schemes (``--subdir-user-modules``) (`#1472 <https://github.com/hpcugent/easybuild-framework/pull/1472>`__)
  * enhance ``--extended-dry-run`` output to include paths for requirements in ``make_module_req`` (`#1520 <https://github.com/hpcugent/easybuild-framework/pull/1520>`__)
  * rewrite read_file to use '``with``' (`#1534 <https://github.com/hpcugent/easybuild-framework/pull/1534>`__)
  * add support for ``eb --last-log`` (`#1541 <https://github.com/hpcugent/easybuild-framework/pull/1541>`__)
  * support using fixed install dir scheme (``--fixed-installdir-naming-scheme``) (`#1546 <https://github.com/hpcugent/easybuild-framework/pull/1546>`__)
  * add edge attributes for build dependencies in ``--dep-graph`` output (`#1548 <https://github.com/hpcugent/easybuild-framework/pull/1548>`__)
  * check whether dependencies marked as external module are hidden (`#1552 <https://github.com/hpcugent/easybuild-framework/pull/1552>`__)
  * implement support for ``--modules-header`` (`#1558 <https://github.com/hpcugent/easybuild-framework/pull/1558>`__)
  * add support to specify '``else``' body for conditional statements in modules (`#1559 <https://github.com/hpcugent/easybuild-framework/pull/1559>`__)
  * add extra test for ``--include-easyblocks`` for generic easyblocks (`#1562 <https://github.com/hpcugent/easybuild-framework/pull/1562>`__)
  * allow user to define the default compiler optimization level (``--default-opt-level``) (`#1565 <https://github.com/hpcugent/easybuild-framework/pull/1565>`__)
  * make ``toolchain.get_variable`` more robust w.r.t. dummy toolchain (`#1566 <https://github.com/hpcugent/easybuild-framework/pull/1566>`__)

* various bug fixes, including:

  * fix missing '``yaml``' module check in tests (`#1525 <https://github.com/hpcugent/easybuild-framework/pull/1525>`__)
  * fix 'develop' install script (`#1529 <https://github.com/hpcugent/easybuild-framework/pull/1529>`__)
  * correctly quote FPM option values in packagin support (`#1530 <https://github.com/hpcugent/easybuild-framework/pull/1530>`__)
  * correctly handle '``.``' in software name w.r.t. ``$EB*`` environment variables (`#1538 <https://github.com/hpcugent/easybuild-framework/pull/1538>`__)
  * exclude logs and test reports from packages (`#1544 <https://github.com/hpcugent/easybuild-framework/pull/1544>`__)
  * also pass down ``--job-cores`` for ``pbs_python`` job backend (`#1547 <https://github.com/hpcugent/easybuild-framework/pull/1547>`__)
  * skip dependencies marked as external modules when packaging (`#1550 <https://github.com/hpcugent/easybuild-framework/pull/1550>`__)
  * fix syntax for ``set_alias`` statement in Lua syntax (`#1554 <https://github.com/hpcugent/easybuild-framework/pull/1554>`__)
  * handle the case of all 'offline' nodes correctly for ``--job`` (`#1560 <https://github.com/hpcugent/easybuild-framework/pull/1560>`__)
  * fix ``test_modules_tool_stateless`` unit test for stateless ModulesTool with Lmod as modules tool (`#1570 <https://github.com/hpcugent/easybuild-framework/pull/1570>`__)

**easyblocks**

* add generic easyblock for Cray toolchains (`#766 <https://github.com/hpcugent/easybuild-easyblocks/pull/766>`__)
* new easyblocks for 2 software packages that require customized support:

  * EggLib (`#811 <https://github.com/hpcugent/easybuild-easyblocks/pull/811>`__), PGI (`#658 <https://github.com/hpcugent/easybuild-easyblocks/pull/658>`__)

* various other enhancements, including:

  * update BamTools easyblock for versions 2.3.x and newer: some shared libraries are now static) (`#785 <https://github.com/hpcugent/easybuild-easyblocks/pull/785>`__)
  * don't hardcode ``.so``, use ``get_shared_lib_ext`` instead (`#789 <https://github.com/hpcugent/easybuild-easyblocks/pull/789>`__, `#790 <https://github.com/hpcugent/easybuild-easyblocks/pull/790>`__, `#791 <https://github.com/hpcugent/easybuild-easyblocks/pull/791>`__, `#793 <https://github.com/hpcugent/easybuild-easyblocks/pull/793>`__, `#794 <https://github.com/hpcugent/easybuild-easyblocks/pull/794>`__, `#803 <https://github.com/hpcugent/easybuild-easyblocks/pull/803>`__, `#815 <https://github.com/hpcugent/easybuild-easyblocks/pull/815>`__)
  * enhance CPLEX easyblock by adding more subdirs to ``$PATH``, define ``$LD_LIBRARY`` and ``$CPLEXDIR`` (`#797 <https://github.com/hpcugent/easybuild-easyblocks/pull/797>`__)
  * make sanity check for netcdf4-python work with both egg and non-egg installs (`#799 <https://github.com/hpcugent/easybuild-easyblocks/pull/799>`__)
  * update sanity check in PETSc/SLEPc easyblocks for v3.6.x (`#800 <https://github.com/hpcugent/easybuild-easyblocks/pull/800>`__)
  * update Trinity easyblock for 2.x versions (`#802 <https://github.com/hpcugent/easybuild-easyblocks/pull/802>`__)
  * update DOLFIN easyblock for v1.6.0 (`#804 <https://github.com/hpcugent/easybuild-easyblocks/pull/804>`__)
  * check for ``libkokkoscore.a`` rather than ``libkokkos.a`` for Trilinos 12.x (`#805 <https://github.com/hpcugent/easybuild-easyblocks/pull/805>`__)
  * add an option to skip the sanitizer tests of Clang (`#806 <https://github.com/hpcugent/easybuild-easyblocks/pull/806>`__)
  * update Molpro easyblock to support binary installs and 2015 version (`#807 <https://github.com/hpcugent/easybuild-easyblocks/pull/807>`__)
  * make ``ConfigureMake`` more robust w.r.t. custom easyconfig parameters (`#810 <https://github.com/hpcugent/easybuild-easyblocks/pull/810>`__)

* various bug fixes, including:

  * add back support for Eigen 2.x in Eigen easyblock (`#798 <https://github.com/hpcugent/easybuild-easyblocks/pull/798>`__)
  * fix for vsc-base being picked up from OS in EasyBuildMeta easyblock (`#813 <https://github.com/hpcugent/easybuild-easyblocks/pull/813>`__)
  * remove ``setuptools.pth`` if it includes absolute paths after installing EasyBuild (`#813 <https://github.com/hpcugent/easybuild-easyblocks/pull/813>`__)

**easyconfigs**

* add easyconfigs for ``foss/2016a`` and ``intel/2016`` common toolchains (`#2310 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2310>`__, `#2311 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2311>`__, `#2339 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2339>`__, `#2363 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2363>`__)

  * incl. easyconfigs for Boost, CMake, Python, Perl using these toolchains

* added example easyconfig files for 21 new software packages:

  * BLASR (`#922 <https://github.com/hpcugent/easybuild-easyconfigs/pull/922>`__), BioKanga (`#2247 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2247>`__), BoltzTraP (`#2365 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2365>`__), basemap (`#2221 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2221>`__), CppUnit (`#2271 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2271>`__), EggLib (`#2335 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2335>`__), FLASH (`#2281 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2281>`__), GLM (`#2288 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2288>`__), hub (`#2249 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2249>`__), MACS2 (`#1983 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1983>`__), MotEvo (`#843 <https://github.com/hpcugent/easybuild-easyconfigs/pull/843>`__), numba (`#2243 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2243>`__), PGI (`#1833 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1833>`__, `#2367 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2367>`__), PLY (`#2305 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2305>`__), PaStiX (`#2319 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2319>`__, `#2326 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2326>`__), patchelf (`#2327 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2327>`__), pip (`#2284 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2284>`__), RSEM (`#2316 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2316>`__), RcppArmadillo (`#2289 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2289>`__), SCDE (`#2289 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2289>`__), slepc4py (`#2318 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2318>`__)
* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including BamTools 2.4.0, Boost 1.60.0, Clang 3.7.1, DOLFIN/FFC/FIAT/Instant/UFL 1.6.0, GATE 7.0, GCC 5.3.0, LLVM 3.7.1, pandas 0.17.1, PETSc 3.6.3, SAMtools 1.3, scipy 0.16.1, SLEPc 3.6.2, Trilinos 12.4.2, Trinity 2.1.1, VTK 6.3.0

* various other enhancements, including:

  * added new ``Cray*`` toolchain versions with pinned dependency versions (`#2222 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2222>`__)
  * don't hardcode ``.so``, use ``SHLIB_EXT`` constant instead (`#2245 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2245>`__)
  * add custom sanity check in GEOS easyconfigs (`#2285 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2285>`__)

* various bug fixes, including:

  * add Autotools (M4) as a build dependency in GMP v6.x easyconfigs (`#2096 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2096>`__)
  * remove argparse from list of extensions in Python 3.2+ easyconfigs, since it became part of stdlib (`#2323 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2323>`__)

* various style fixes, including:

  * get rid of tabs (`#2302 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2302>`__)
  * remove trailing whitespace (`#2341 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2341>`__)

.. _release_notes_eb250:

v2.5.0 (December 17th 2015)
---------------------------

feature + bugfix release

**framework**

* add support for IBM XL compilers on Power7 and PowerPC (BlueGene) (`#1470 <https://github.com/hpcugent/easybuild-framework/pull/1470>`__)
* add support fo generic compilation using ``--optarch=GENERIC`` (`#1471 <https://github.com/hpcugent/easybuild-framework/pull/1471>`__)

  * see also :ref:`controlling_compiler_optimization_flags`

* update experimental support for ``.yeb`` easyconfigs (`#1515 <https://github.com/hpcugent/easybuild-framework/pull/1515>`__)

  * support clean way to specify toolchain + dependencies in ``.yeb`` easyconfigs

* various other enhancements, including:

  * add support for '``whatis``' easyconfig parameter (`#1271 <https://github.com/hpcugent/easybuild-framework/pull/1271>`__)
  * add support for SLES 12 and kernel 3.12.x (`#1412 <https://github.com/hpcugent/easybuild-framework/pull/1412>`__)
  * add GCCcore toolchain definition (`#1451 <https://github.com/hpcugent/easybuild-framework/pull/1451>`__)
  * use '``diff --git``' lines to determine patched files in pull request with ``--from-pr`` (`#1460 <https://github.com/hpcugent/easybuild-framework/pull/1460>`__)
  * add proper option parser to bootstrap script (`#1468 <https://github.com/hpcugent/easybuild-framework/pull/1468>`__)
  * add ``get_gcc_version()`` function in systemtools module (`#1496 <https://github.com/hpcugent/easybuild-framework/pull/1496>`__)
  * don't load fake module in sanity_check_step during a dry run (`#1499 <https://github.com/hpcugent/easybuild-framework/pull/1499>`__)
  * allow string values to be passed in ``make_module_req`` by hoisting them into a list (`#1502 <https://github.com/hpcugent/easybuild-framework/pull/1502>`__)
  * add support for listing build dependencies as hidden dependencies (`#1503 <https://github.com/hpcugent/easybuild-framework/pull/1503>`__)
  * also consider ``lib32/pkgconfig`` and ``lib64/pkgconfig`` for ``$PKG_CONFIG_PATH`` (`#1505 <https://github.com/hpcugent/easybuild-framework/pull/1505>`__)
  * add support to ``make_module_dep`` to specify module to unload before loading a dependency module (`#1506 <https://github.com/hpcugent/easybuild-framework/pull/1506>`__)
  * add support to ``make_module_extra`` to specify alternative root/version for ``$EBROOT``/``$EBVERSION`` (`#1508 <https://github.com/hpcugent/easybuild-framework/pull/1508>`__)
  * packaging support is no longer considered experimental (`#1510 <https://github.com/hpcugent/easybuild-framework/pull/1510>`__)

* various bug fixes, including:

  * also consider ``lib64`` in sanity check performed during EasyBuild bootstrap (`#1464 <https://github.com/hpcugent/easybuild-framework/pull/1464>`__)
  * also add description/homepage to packages created with FPM (`#1469 <https://github.com/hpcugent/easybuild-framework/pull/1469>`__)
  * fix develop setup script to install EasyBuild-develop module in subdirectory (`#1480 <https://github.com/hpcugent/easybuild-framework/pull/1480>`__)
  * don't create a whole set of temporary '``minimal-easyconfigs``' subdirs with ``--minimal-toolchains`` (`#1484 <https://github.com/hpcugent/easybuild-framework/pull/1484>`__)
  * only keep polling if exit code is ``None`` in ``run_cmd_qa``, to correctly deal with negative exit codes (`#1486 <https://github.com/hpcugent/easybuild-framework/pull/1486>`__)
  * fix bootstrap script for missing sys_platform by using newer distribute 0.6.49 in stage 0 (`#1490 <https://github.com/hpcugent/easybuild-framework/pull/1490>`__)
  * make sure that extra custom easyconfig parameters are known for extensions (`#1498 <https://github.com/hpcugent/easybuild-framework/pull/1498>`__)
  * add missing import for ``EasyBuildError`` in ``easybuild/toolchains/linalg/libsci.py`` (`#1512 <https://github.com/hpcugent/easybuild-framework/pull/1512>`__)
  * isolate tests from possible system-wide configuration files (`#1513 <https://github.com/hpcugent/easybuild-framework/pull/1513>`__)
  * only use ``glob`` in ``make_module_req`` on non-empty strings (`#1519 <https://github.com/hpcugent/easybuild-framework/pull/1519>`__)
    * this fixes the problem where ``$CUDA_HOME`` and ``$CUDA_PATH`` are not defined in module files for CUDA

**easyblocks**

* update easyblocks for Intel tools to support 2016 versions (`#691 <https://github.com/hpcugent/easybuild-easyblocks/pull/691>`__, `#745 <https://github.com/hpcugent/easybuild-easyblocks/pull/745>`__, `#756 <https://github.com/hpcugent/easybuild-easyblocks/pull/756>`__, `#777 <https://github.com/hpcugent/easybuild-easyblocks/pull/777>`__)

  * IntelBase easyblock has been enhanced to support specifying which components to install

* new easyblocks for 3 software packages that require customized support:

  * Intel Advisor (`#767 <https://github.com/hpcugent/easybuild-easyblocks/pull/767>`__), DIRAC (`#778 <https://github.com/hpcugent/easybuild-easyblocks/pull/778>`__), MRtrix (`#772 <https://github.com/hpcugent/easybuild-easyblocks/pull/772>`__)

* various other enhancements, including:

  * update numpy and SuiteSparse easyblock to use scikit-umfpack (`#718 <https://github.com/hpcugent/easybuild-easyblocks/pull/718>`__)
  * add an option to allow removal of the ``-Dusethreads`` flag in Perl easyblock (`#724 <https://github.com/hpcugent/easybuild-easyblocks/pull/724>`__)
  * update Doxygen easyblock for 1.10.x (CMake) (`#734 <https://github.com/hpcugent/easybuild-easyblocks/pull/734>`__)
  * update sanity check in Qt easyblock for Qt 5.x (`#740 <https://github.com/hpcugent/easybuild-easyblocks/pull/740>`__)
  * add support for multilib build of GCC on PowerPC (`#741 <https://github.com/hpcugent/easybuild-easyblocks/pull/741>`__)
  * add support to OpenFOAM and SCOTCH easyblocks to support 64-bit integers, via 'i8' toolchain option (`#744 <https://github.com/hpcugent/easybuild-easyblocks/pull/744>`__)
  * fix sanity check to support numpy 1.10 (dropped _dotblas.so) (`#757 <https://github.com/hpcugent/easybuild-easyblocks/pull/757>`__, `#761 <https://github.com/hpcugent/easybuild-easyblocks/pull/761>`__, `#762 <https://github.com/hpcugent/easybuild-easyblocks/pull/762>`__)
  * update IPP easyblock for v9.x (`#759 <https://github.com/hpcugent/easybuild-easyblocks/pull/759>`__)
  * cleaner output for PythonPackage under dry run, make numpy easyblock dry-run aware (`#760 <https://github.com/hpcugent/easybuild-easyblocks/pull/760>`__, `#671 <https://github.com/hpcugent/easybuild-easyblocks/pull/671>`__)
  * add support for using netCDF-Fortran as dependency in ALADIN easyblock (`#764 <https://github.com/hpcugent/easybuild-easyblocks/pull/764>`__)
  * add support for tbb 4.4.x in tbb easyblock (`#769 <https://github.com/hpcugent/easybuild-easyblocks/pull/769>`__)
  * add support for specifying altroot/altversion in Bundle easyblock (`#773 <https://github.com/hpcugent/easybuild-easyblocks/pull/773>`__)
  * update OpenFOAM easyblock for OpenFOAM-Extend 3.2 + use apply_regex_substitutions (`#770 <https://github.com/hpcugent/easybuild-easyblocks/pull/770>`__)

* various bug fixes, including:

  * fix module path extension of system compiler in HMNS setup (`#742 <https://github.com/hpcugent/easybuild-easyblocks/pull/742>`__)
  * only restore ``$PYTHONPATH`` if it was defined in EasyBuildMeta easyblock (`#743 <https://github.com/hpcugent/easybuild-easyblocks/pull/743>`__)
  * make sure ``$PYTHONPATH`` is defined correctly in module file for Python packages created with ``--module-only`` (`#748 <https://github.com/hpcugent/easybuild-easyblocks/pull/748>`__)
  * fix WRF easyblock to produce correct module under ``--module-only --force`` (`#746 <https://github.com/hpcugent/easybuild-easyblocks/pull/746>`__, `#752 <https://github.com/hpcugent/easybuild-easyblocks/pull/752>`__)
  * don't hardcode '``openPBS``' in GATE easyblock, use value for ``default_platform`` easyconfig parameter (`#753 <https://github.com/hpcugent/easybuild-easyblocks/pull/753>`__)
  * avoid adding lib subdirs to ``$*LIBRARY_PATH`` if no libraries are there in ``PythonPackage`` easyblock (`#755 <https://github.com/hpcugent/easybuild-easyblocks/pull/755>`__)
  * fix installing Python bindings for libxml2 to correct installation prefix (`#765 <https://github.com/hpcugent/easybuild-easyblocks/pull/765>`__)

**easyconfigs**

* add GCCcore easyconfig that can be used as base for all compilers (without getting in the way) (`#2214 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2214>`__)

  * along with easyconfig for ``GCC/4.9.3-2.25``: bundle of GCCcore 4.9.3 and binutils 2.25
  * intended to replace the GNU toolchain

* added example easyconfig files for 39 new software packages:

  * DIRAC (`#2212 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2212>`__), GeoIP (`#2172 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2172>`__, `#2185 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2185>`__), GeoIP-C (`#2172 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2172>`__, `#2185 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2185>`__), graph-tool (`#1591 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1591>`__), gtkglext (`#2217 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2217>`__), Intel Advisor (`#2210 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2210>`__), InterProScan (`#2225 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2225>`__, `#2227 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2227>`__, `#2234 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2234>`__), intltool (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), kallisto (`#2173 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2173>`__), LibUUID (`#1930 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1930>`__), LuaJIT (`#2153 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2153>`__), libXcursor (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), libXrandr (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), libXtst (`#2143 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2143>`__), libdap (`#1930 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1930>`__), libtasn1 (`#2208 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2208>`__), libxkbcommon (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), MRtrix (`#2217 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2217>`__, `#2218 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2218>`__), MultiNest (`#2166 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2166>`__, `#2168 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2168>`__), Nipype (`#2150 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2150>`__), PPfold (`#2183 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2183>`__, `#2187 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2187>`__), p11-kit (`#2208 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2208>`__), pangox-compat (`#2217 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2217>`__), Qt5 (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), randrproto (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), rhdf5 (`#2175 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2175>`__), Stampy (`#2180 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2180>`__, `#2182 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2182>`__), scikit-umfpack (`#2061 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2061>`__), scp (Python pkg) (`#2196 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2196>`__), sleuth (`#2175 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2175>`__), traits (`#2150 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2150>`__), vincent (`#2169 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2169>`__, `#2185 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2185>`__), XKeyboardConfig (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), xcb-util (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), xcb-util-image (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), xcb-util-keysyms (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), xcb-util-renderutil (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), xcb-util-wm (`#2136 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2136>`__), zlibbioc (`#2175 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2175>`__)

* added new easyconfigs for existing toolchains:
    ``intel/2015.08`` (`#2194 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2194>`__), ``intel/2016.00`` (`#2209 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2209>`__), ``intel/2016.01`` (`#2219 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2219>`__), ``iomkl/2015.03`` (`#2155 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2155>`__)

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including CMake 3.4.1, HDF5 1.8.16, netCDF 4.3.3.1, netCDF-Fortran 4.4.2, numpy 1.10.1, Octave 4.0.0,
    OpenFOAM 3.0.0, OpenFOAM-Extend 3.2, Python 2.7.11

* various other enhancements, including:

  * add tidyr to R 3.2.1 easyconfigs (`#2174 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2174>`__)
  * enable C++ support in MIGRATE-N (`#2178 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2178>`__)
  * also installed shared libraries for AMD and UMFPACK in SuiteSparse (`#2061 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2061>`__)
  * fix software name for ParaView (was: Paraview) (`#2132 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2132>`__)
  * enable building of shared libraries for binutils (`#2133 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2133>`__)
  * harden binutils built with dummy toolchain by linking to system libraries via ``RPATH`` (`#2228 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2228>`__)
  * enhance easyconfig unit tests to check that each easyconfig file is in the right subdirectory (`#2232 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2232>`__)

* various bug fixes, including:

  * fix ALADIN patch file to not use relative paths, and adjust list of ALADIN sources accordingly ((`#2207 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2207>`__), (`#2213 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2213>`__))
  * rename patch files for OpenFOAM to be in line with other patches (`#2226 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2226>`__)
  * fix typo in bzip2 source URLs (`#2204 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2204>`__)
  * force linking of ncurses in libreadline (`#2206 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2206>`__)
  * enable ``-fPIC`` in all zlib 1.2.8 easyconfigs (`#2220 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2220>`__)
  * move Net-LibIDN/SRA-Toolkit/bbftpPRO/o2scl easyconfigs to right location (`#2232 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2232>`__)
  * restrict parallel build in OpenFOAM-Extend easyconfigs via '``maxparallel``', not '``parallel``' (`#2233 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2233>`__)


.. _release_notes_eb240:

v2.4.0 (November 10th 2015)
---------------------------

feature + bugfix release

**framework**

* add support for ``--extended-dry-run``/``-x`` (`#1388 <https://github.com/hpcugent/easybuild-framework/pull/1388>`__, `#1450 <https://github.com/hpcugent/easybuild-framework/pull/1450>`__, `#1453 <https://github.com/hpcugent/easybuild-framework/pull/1453>`__, `#1455 <https://github.com/hpcugent/easybuild-framework/pull/1455>`__)

  * detailed documentation is available at :ref:`extended_dry_run`

* fix checking of sanity check paths w.r.t. discriminating between files and directories (`#1436 <https://github.com/hpcugent/easybuild-framework/pull/1436>`__)

  * this impacts several easyconfig files where ``sanity_check_paths`` was not 100% correct

* make '``eb``' script aware of Python v3.x, fall back to using ``python2`` if required (`#1411 <https://github.com/hpcugent/easybuild-framework/pull/1411>`__)
* add experimental support for parsing .yeb easyconfig files in YAML syntax (`#1447 <https://github.com/hpcugent/easybuild-framework/pull/1447>`__, `#1448 <https://github.com/hpcugent/easybuild-framework/pull/1448>`__, `#1449 <https://github.com/hpcugent/easybuild-framework/pull/1449>`__)

  * see also :ref:`easyconfig_yeb_format`

* add experimental support for resolving dependencies with minimal toolchains (`#1306 <https://github.com/hpcugent/easybuild-framework/pull/1306>`__)

  * see also :ref:`minimal_toolchains`

* various other enhancements, including:

  * refactor ``extract_cmd`` function to get rid of if/elif/else spaghetti blob (`#1382 <https://github.com/hpcugent/easybuild-framework/pull/1382>`__)
  * add support for ``--review-pr`` (`#1383 <https://github.com/hpcugent/easybuild-framework/pull/1383>`__)
  * add ``apply_regex_substitutions`` function to perform runtime patching from easyblocks (`#1388 <https://github.com/hpcugent/easybuild-framework/pull/1388>`__, `#1458 <https://github.com/hpcugent/easybuild-framework/pull/1458>`__)
  * add support for specifying alternate name to be part of generated module name (`#1389 <https://github.com/hpcugent/easybuild-framework/pull/1389>`__)
    * via '``modaltsoftname``' easyconfig parameter
  * support overriding # used cores via ``--parallel`` (`#1393 <https://github.com/hpcugent/easybuild-framework/pull/1393>`__)
  * also define ``$FC`` and ``$FCFLAGS`` in build environment (`#1394 <https://github.com/hpcugent/easybuild-framework/pull/1394>`__)
  * add support extracting for ``.tar.Z`` files (`#1396 <https://github.com/hpcugent/easybuild-framework/pull/1396>`__)
  * include easybuild/scripts in instalation (`#1397 <https://github.com/hpcugent/easybuild-framework/pull/1397>`__)
  * ignore hidden directories in find_base_dir (`#1413 <https://github.com/hpcugent/easybuild-framework/pull/1413>`__, `#1415 <https://github.com/hpcugent/easybuild-framework/pull/1415>`__)
  * add ``only_if_module_is_available`` decorator function to guard functionality that uses optional dependencies (`#1416 <https://github.com/hpcugent/easybuild-framework/pull/1416>`__)
  * give easyblocks the possibility to choose ``maxhits`` for ``run_cmd_qa`` (`#1417 <https://github.com/hpcugent/easybuild-framework/pull/1417>`__)
  * use class name (string) rather than License instances as values for software license constants (`#1418 <https://github.com/hpcugent/easybuild-framework/pull/1418>`__)
  * support controlling recursive unloading of dependencies via '``recursive_module_unload``' easyconfig parameter (`#1425 <https://github.com/hpcugent/easybuild-framework/pull/1425>`__)
  * implement basic support for type checking of easyconfig parameters (`#1427 <https://github.com/hpcugent/easybuild-framework/pull/1427>`__)
  * support auto-converting to expected value type for easyconfig parameters (enabled by default) (`#1428 <https://github.com/hpcugent/easybuild-framework/pull/1428>`__, `#1437 <https://github.com/hpcugent/easybuild-framework/pull/1437>`__)
  * add support for ``--rebuild`` command line option, alternative for ``--force`` which doesn't imply ``--ignore-osdeps`` (`#1435 <https://github.com/hpcugent/easybuild-framework/pull/1435>`__)
  * add support for Mercurial easyconfig repository (`#979 <https://github.com/hpcugent/easybuild-framework/pull/979>`__, `#1446 <https://github.com/hpcugent/easybuild-framework/pull/1446>`__)
  * add dedicated class for psmpi toolchain MPI component, and use it in gpsmpi and ipsmpi toolchains (`#1454 <https://github.com/hpcugent/easybuild-framework/pull/1454>`__)

* various bug fixes, including:

  * fix extracting of comments from an easyconfig file that includes 'tail' comments (`#1381 <https://github.com/hpcugent/easybuild-framework/pull/1381>`__)
  * fix dev version to follow PEP-440, as required by recent setuptools versions (`#1403 <https://github.com/hpcugent/easybuild-framework/pull/1403>`__)

    * required to avoid that setuptools transforms the version itself
    * see also https://www.python.org/dev/peps/pep-0440/#developmental-releases

  * allow ``get_cpu_speed`` to return ``None`` if CPU freq could not be determined (`#1421 <https://github.com/hpcugent/easybuild-framework/pull/1421>`__)
  * relax ``sanity_check_paths`` in EasyBuild bootstrap script to deal with possible zipped .egg (`#1422 <https://github.com/hpcugent/easybuild-framework/pull/1422>`__)
  * use empty list as default value for src/patches in Extension class (`#1434 <https://github.com/hpcugent/easybuild-framework/pull/1434>`__)
  * skip symlinked files in ``adjust_permissions`` function (`#1439 <https://github.com/hpcugent/easybuild-framework/pull/1439>`__)
  * fix HierarchicalMNS to always use full version number (`#1440 <https://github.com/hpcugent/easybuild-framework/pull/1440>`__)

**easyblocks**

* 3 new generic easyblocks: OCamlPackage (`#467 <https://github.com/hpcugent/easybuild-easyblocks/pull/467>`__), SCons (`#689 <https://github.com/hpcugent/easybuild-easyblocks/pull/689>`__, `#700 <https://github.com/hpcugent/easybuild-easyblocks/pull/700>`__), Waf (`#722 <https://github.com/hpcugent/easybuild-easyblocks/pull/722>`__)
* new easyblocks for 2 software packages that require customized support:

  * OCaml (`#467 <https://github.com/hpcugent/easybuild-easyblocks/pull/467>`__), Samcef (`#678 <https://github.com/hpcugent/easybuild-easyblocks/pull/678>`__)

* various other enhancements, including:

  * add support for installing OpenFOAM with external METIS, CGAL and Paraview (`#497 <https://github.com/hpcugent/easybuild-easyblocks/pull/497>`__)
  * update netCDF easyblock updated for netCDF v4.3.3.1 (`#674 <https://github.com/hpcugent/easybuild-easyblocks/pull/674>`__)
  * update Rosetta easyblock for recent Rosetta versions (`#677 <https://github.com/hpcugent/easybuild-easyblocks/pull/677>`__)
  * make unpacked source dir detection in easyblock for VSC-tools a little bit more flexible (`#679 <https://github.com/hpcugent/easybuild-easyblocks/pull/679>`__)
  * add support for building with Plumed support enabled in CP2K easyblock (`#681 <https://github.com/hpcugent/easybuild-easyblocks/pull/681>`__)
  * update Go easyblock for Go v1.5 (`#683 <https://github.com/hpcugent/easybuild-easyblocks/pull/683>`__)
  * use ``apply_regex_substitutions`` function in WRF easyblock (`#685 <https://github.com/hpcugent/easybuild-easyblocks/pull/685>`__)
  * update MUMPS easyblock for 5.x (`#686 <https://github.com/hpcugent/easybuild-easyblocks/pull/686>`__)
  * implement runtime patching of ``$WM_*`` and compiler variables for OpenFOAM (`#688 <https://github.com/hpcugent/easybuild-easyblocks/pull/688>`__)
  * specify sequential compiler to use in compiler command that gets injected in OpenFOAM easyblock (`#692 <https://github.com/hpcugent/easybuild-easyblocks/pull/692>`__)
  * make ``PythonPackage`` and WRF easyblocks dry-run aware (`#696 <https://github.com/hpcugent/easybuild-easyblocks/pull/696>`__)

    * see also :ref:`extended_dry_run_guidelines_easyblocks`

  * add support in ``PythonPackage`` for installing with ``easy_install`` + installing zipped eggs (`#698 <https://github.com/hpcugent/easybuild-easyblocks/pull/698>`__, `#711 <https://github.com/hpcugent/easybuild-easyblocks/pull/711>`__, `#715 <https://github.com/hpcugent/easybuild-easyblocks/pull/715>`__)
  * update Bowtie easyblock for recent Bowtie versions (`#707 <https://github.com/hpcugent/easybuild-easyblocks/pull/707>`__)
  * update CUDA easyblock for CUDA 7.x(`#708 <https://github.com/hpcugent/easybuild-easyblocks/pull/708>`__)
  * also consider ``config/make.sys.in`` for want in QuantumESRESSO easyblock (`#714 <https://github.com/hpcugent/easybuild-easyblocks/pull/714>`__)
  * define ``$NWCHEM_LONG_PATH`` if needed in NWChem easyblock (`#720 <https://github.com/hpcugent/easybuild-easyblocks/pull/720>`__)
  * remove custom post-install step in PDT easyblock (`#723 <https://github.com/hpcugent/easybuild-easyblocks/pull/723>`__)

    * no longer needed now that ``adjust_permissions`` functions ignores symlinks

  * use ``$LIBS`` in HPL easyblock (`#727 <https://github.com/hpcugent/easybuild-easyblocks/pull/727>`__, `#736 <https://github.com/hpcugent/easybuild-easyblocks/pull/736>`__)

* various bug fixes, including:

  * also define ``$MCRROOT`` for MCR in module (`#687 <https://github.com/hpcugent/easybuild-easyblocks/pull/687>`__)
  * add missing '``super``' call in ``configure_step`` of easyblock for python-meep (`#694 <https://github.com/hpcugent/easybuild-easyblocks/pull/694>`__)
  * only prepend existing non-empty paths to ``$PYTHONPATH`` in ``PythonPackage`` easyblock (`#697 <https://github.com/hpcugent/easybuild-easyblocks/pull/697>`__)
  * fix extra_options definition in ``CMakePythonPackage`` easyblock (`#698 <https://github.com/hpcugent/easybuild-easyblocks/pull/698>`__)
  * fix dev version to follow PEP-440, as required by recent setuptools versions (`#702 <https://github.com/hpcugent/easybuild-easyblocks/pull/702>`__, `#703 <https://github.com/hpcugent/easybuild-easyblocks/pull/703>`__, `#704 <https://github.com/hpcugent/easybuild-easyblocks/pull/704>`__)

    * required to avoid that setuptools transforms the version itself
    * see also https://www.python.org/dev/peps/pep-0440/#developmental-releases

  * consider both ``lib`` and ``lib64`` in sanity check paths for flex (`#705 <https://github.com/hpcugent/easybuild-easyblocks/pull/705>`__)
  * also copy signature file and don't copy CMake files in Eigen easyblock (`#709 <https://github.com/hpcugent/easybuild-easyblocks/pull/709>`__)
  * fix directory names in ``make_module_req_guess`` of ANSYS easyblock (`#713 <https://github.com/hpcugent/easybuild-easyblocks/pull/713>`__)
  * fix imports for ``set_tmpdir`` in easyblock unit tests after function was moved in EasyBuild framework (`#726 <https://github.com/hpcugent/easybuild-easyblocks/pull/726>`__)
  * use ``--with-tcltk*`` configure options for Python to point to ensure Tcl/Tk deps are picked up (`#729 <https://github.com/hpcugent/easybuild-easyblocks/pull/729>`__)
  * fix order of subdirs for QuantumESPRESSO binaries (`#730 <https://github.com/hpcugent/easybuild-easyblocks/pull/730>`__)
  * correctly handle having both ``$FC``/``$FCFLAGS`` and ``$F90``/``$F90FLAGS`` defined when building MVAPICH2 (`#732 <https://github.com/hpcugent/easybuild-easyblocks/pull/732>`__)
  * fix OpenSSL sanity check paths: lib/engines is a directory (`#731 <https://github.com/hpcugent/easybuild-easyblocks/pull/731>`__, `#733 <https://github.com/hpcugent/easybuild-easyblocks/pull/733>`__)
  * fix sanity check paths for netcdf-python (`#735 <https://github.com/hpcugent/easybuild-easyblocks/pull/735>`__)

**easyconfigs**

* added example easyconfig files for 45 new software packages:

  * animation (`#2007 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2007>`__), ANSYS CFD (`#1969 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1969>`__), ANTLR (`#1191 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1191>`__, `#1980 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1980>`__), APR (`#1970 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1970>`__), APR-util (`#1970 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1970>`__), Aspera Connect (`#2005 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2005>`__), ChIP-Seq (`#2119 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2119>`__), deap (`#2082 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2082>`__), DISCOVARdenovo (`#1932 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1932>`__), FastQC (`#1984 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1984>`__), fontsproto (`#1618 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1618>`__, `#2038 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2038>`__), GraphicsMagick (`#2007 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2007>`__), HBase (`#1990 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1990>`__), ISIS (`#1972 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1972>`__), libedit (`#293 <https://github.com/hpcugent/easybuild-easyconfigs/pull/293>`__), libfontenc (`#1618 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1618>`__, `#2038 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2038>`__), libGLU (`#1627 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1627>`__), libXdamage (`#1618 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1618>`__, `#2038 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2038>`__), libXfont (`#1618 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1618>`__, `#2038 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2038>`__), LLVM (`#1620 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1620>`__, `#1989 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1989>`__, `#2031 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2031>`__), MIGRATE-N (`#1944 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1944>`__), MIRA (`#1938 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1938>`__), mympingpong (`#2049 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2049>`__), MySQLdb (`#2011 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2011>`__), NCO (`#1191 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1191>`__, `#1980 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1980>`__), NIPY (`#2064 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2064>`__), Nilearn (`#2064 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2064>`__), NiBabel (`#2064 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2064>`__), PBZIP2 (`#1038 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1038>`__), PIL (`#2062 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2062>`__), PhyloCSF (`#2018 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2018>`__), pycairo (`#2085 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2085>`__), pydicom (`#2063 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2063>`__), Salmon (`#2051 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2051>`__), Samcef (`#1941 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1941>`__), scikit-image (`#1974 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1974>`__, `#2006 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2006>`__), Serf (`#1970 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1970>`__), SSAHA2 (`#1039 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1039>`__), Subversion (`#1970 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1970>`__), SWASH (`#2059 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2059>`__), time (`#1954 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1954>`__), Trim_Galore (`#1984 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1984>`__), Trimmomatic (`#1987 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1987>`__), WEKA (`#1986 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1986>`__), x264 (`#2017 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2017>`__)

* added new easyconfigs for existing toolchains: ``gimkl/2.11.5`` (`#2093 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2093>`__)
* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including Clang + LLVM 3.7.0, CMake 3.3.2, CUDA 7.5.18, hanythingondemand v3.0.1, Mesa 11.0.2, mpi4py v2.0.0,
    ncurses 6.0, OpenFOAM 2.4.0, Paraview 4.4.0, Python 3.5.0, QuantumESPRESSO v5.2.1

* various other enhancements, including:

  * enable '``pic``' toolchain option in libxml2 easyconfigs (`#1993 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1993>`__)
  * extend list of R libraries included in R v3.2.1 easyconfigs (`#2042 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2042>`__, `#2046 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2046>`__, `#2067 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2067>`__, `#2072 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2072>`__)
  * add Rsubread in Bioconductor easyconfigs (`#1971 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1971>`__)

* various bug fixes, including:

  * fix software name for ``BEEF`` (was '``libbeef``') (`#1679 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1679>`__)
  * add patch to install ``qhull.pc`` (pkgconfig) file with Qhull (`#1975 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1975>`__)
  * don't enable experimental nouveau API in libdrm easyconfigs (`#1994 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1994>`__)
  * fix dev version to follow PEP-440, as required by recent setuptools versions (`#1997 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1997>`__)

    * required to avoid that setuptools transforms the version itself
    * see also https://www.python.org/dev/peps/pep-0440/#developmental-releases

  * correct homepage in Cufflinks easyconfigs (`#2060 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2060>`__)
  * fix imports for ``set_tmpdir`` in easyblock unit tests after function was moved in EasyBuild framework (`#2097 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2097>`__)
  * add patch for Tk 8.6.4 to fix problem with ``tk.tcl`` not being found (`#2102 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2102>`__)
  * don't use ``%(version)s`` template in toolchain version, causes problems with HierarchicalMNS (`#2104 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2104>`__)
  * fix sanity check paths in several easyconfig (`#2109 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2109>`__, `#2120 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2120>`__, `#2121 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2121>`__, `#2125 <https://github.com/hpcugent/easybuild-easyconfigs/pull/2125>`__)

    * required because of bug fix in ``sanity_check_step`` implementation
    * CVXOPT, h5py, LIBSVM, libunistring, MDP, monty, PhyloCSF, Pyke, pandas, pycosat, pyhull, pymatgen,
      python-dateutils, Seaborn, Theano, XML-LibXML, XML-Simple

.. _release_notes_eb230:

v2.3.0 (September 2nd 2015)
---------------------------

feature + bugfix release

**framework**

* requires vsc-base v2.2.4 or more recent (`#1343 <https://github.com/hpcugent/easybuild-framework/pull/1343>`__)

  * required for ``mk_rst_table`` function in ``vsc.utils.docs``

* various other enhancements, including:

  * add support for generating documentation for (generic) easyblocks in ``.rst`` format (`#1317 <https://github.com/hpcugent/easybuild-framework/pull/1317>`__)
  * preserve comments in easyconfig file in ``EasyConfig.dump()`` method (`#1327 <https://github.com/hpcugent/easybuild-framework/pull/1327>`__)
  * add ``--cleanup-tmpdir`` option (`#1365 <https://github.com/hpcugent/easybuild-framework/pull/1365>`__)

    * enables to preserve the used temporary directory via ``--disable-cleanup-tmpdir``

  * enhance ``EasyConfig.dump()`` to reformat dumped easyconfig according to style guidelines (`#1345 <https://github.com/hpcugent/easybuild-framework/pull/1345>`__)
  * add support for extracting ``.iso`` files using 7z (p7zip) (`#1375 <https://github.com/hpcugent/easybuild-framework/pull/1375>`__)

* various bug fixes, including:

  * correctly deal with special characters in template strings in ``EasyConfig.dump()`` method (`#1323 <https://github.com/hpcugent/easybuild-framework/pull/1323>`__)
  * rework ``easybuild.tools.module_generator`` module to avoid keeping state w.r.t. fake modules (`#1348 <https://github.com/hpcugent/easybuild-framework/pull/1348>`__)
  * fix dumping of hidden deps (`#1354 <https://github.com/hpcugent/easybuild-framework/pull/1354>`__)
  * fix use of ``--job`` with hidden dependencies: include ``--hidden`` in submitted job script when needed (`#1356 <https://github.com/hpcugent/easybuild-framework/pull/1356>`__)
  * fix ``ActiveMNS.det_full_module_name()`` for external modules (`#1360 <https://github.com/hpcugent/easybuild-framework/pull/1360>`__)
  * fix ``EasyConfig.all_dependencies`` definition, fix tracking of job dependencies (`#1359 <https://github.com/hpcugent/easybuild-framework/pull/1359>`__, `#1361 <https://github.com/hpcugent/easybuild-framework/pull/1361>`__)
  * fix ``ModulesTool.exist()`` for hidden Lua module files (`#1364 <https://github.com/hpcugent/easybuild-framework/pull/1364>`__)
  * only call ``EasyBlock.sanity_check_step`` for non-extensions (`#1366 <https://github.com/hpcugent/easybuild-framework/pull/1366>`__)

    * this results in significant speedup when installing easyconfigs with lots of extensions, but also
      results in checking the default sanity check paths if none were defined for extensions installed as a module

  * fix using module naming schemes that were included via ``--include-module-naming-schemes`` (`#1370 <https://github.com/hpcugent/easybuild-framework/pull/1370>`__)

**easyblocks**

* new easyblocks for 2 software packages that require customized support:

  * MCR (`#623 <https://github.com/hpcugent/easybuild-easyblocks/pull/623>`__), Molpro (`#665 <https://github.com/hpcugent/easybuild-easyblocks/pull/665>`__)

* various other enhancements, including:

  * enhance BWA easyblock to also install man pages (`#650 <https://github.com/hpcugent/easybuild-easyblocks/pull/650>`__)
  * enhance tbb easyblock to consider lib dirs in order and also define ``$CPATH``, ``$LIBRARY_PATH``, ``$TBBROOT`` (#653, #654)
  * call ``PythonPackage.configure_step`` in ``ConfigureMakePythonPackage.configure_step`` (`#668 <https://github.com/hpcugent/easybuild-easyblocks/pull/668>`__)
  * add '``foldx3b6``' as possible binary name in FoldX easyblock (`#671 <https://github.com/hpcugent/easybuild-easyblocks/pull/671>`__)
  * enhance/cleanup MATLAB easyblock (`#672 <https://github.com/hpcugent/easybuild-easyblocks/pull/672>`__)
  * move preparing of '``intel``' subdir in ``$HOME`` to ``configure_step`` in ``IntelBase`` easyblock (`#673 <https://github.com/hpcugent/easybuild-easyblocks/pull/673>`__)

* various bug fixes, including:

  * add missing super call in ``post_install_step`` of imkl easyblock (`#648 <https://github.com/hpcugent/easybuild-framework/pull/648>`__, `#660 <https://github.com/hpcugent/easybuild-framework/pull/660>`__)
  * fix regex used to correct ``I_MPI_ROOT`` in impi ``mpivars.sh`` scripts (`#662 <https://github.com/hpcugent/easybuild-easyblocks/pull/662>`__)
  * fix regex used to patch ``.mk`` file in configure step of SuiteSparse easyblock (`#666 <https://github.com/hpcugent/easybuild-easyblocks/pull/666>`__)
  * correctly specify installation prefix via ``$GEM_HOME`` in ``RubyGem`` easyblock (`#667 <https://github.com/hpcugent/easybuild-easyblocks/pull/667>`__)
  * add custom sanity check in scipy easyblock (`#669 <https://github.com/hpcugent/easybuild-easyblocks/pull/669>`__)
  * specify to always use the bfd linker for OpenFOAM, to stay away from using ``ld.gold`` (`#670 <https://github.com/hpcugent/easybuild-easyblocks/pull/670>`__)

**easyconfigs**

* added example easyconfig files for 19 new software packages:

  * ATK (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), Atkmm (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), cairomm (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), GLibmm (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), GlobalArrays (`#1868 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1868>`__), gdk-pixbuf (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__),
    gtk+ (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), Gtkmm (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), libbeef (`#1827 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1827>`__), libsigc++ (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), libsodium (`#1876 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1876>`__), MACS (`#1869 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1869>`__), MCR (`#1677 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1677>`__),
    Molpro (`#1880 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1880>`__), NFFT (`#1921 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1921>`__), p7zip (`#1931 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1931>`__), Pangomm (`#1780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1780>`__), pygraphviz (`#1861 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1861>`__), pycosat (`#1859 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1859>`__)

* added new easyconfigs for existing toolchains: GNU/4.9.3-2.25 (`#1836 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1836>`__), foss/2015b (`#1695 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1695>`__), intel/2015b (`#1696 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1696>`__)

  * add easyconfigs using this toolchain for BLAST+ 2.2.31, Boost 1.58.0, CP2K 2.6.1, OpenFOAM 2.3.1,
    Perl 5.20.2 + 5.22.0 (bare), Python 2.7.10, R 3.2.1

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including Boost 1.59.0, CP2K 2.6.1, GCC 5.2.0

* various other enhancements, including:

  * enhance texinfo easyconfig w.r.t. ``texmf``, only use it as a build dependency (`#1840 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1840>`__)
  * enable building of ``ld.gold`` in binutils 2.25 (`#1885 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1885>`__)

* various bug fixes, including:

  * fix enabling MPI support for h5py 2.5.0 (`#1825 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1825>`__)
  * fix versions of Bioconductor packages + add a couple extra (`#1828 <https://github.com/hpcugent/easybuild-framework/pull/1828>`__, `#1852 <https://github.com/hpcugent/easybuild-framework/pull/1852>`__, `#1895 <https://github.com/hpcugent/easybuild-framework/pull/1895>`__, `#1917 <https://github.com/hpcugent/easybuild-framework/pull/1917>`__)
  * put dummy values in place for ``builddir``/``installdir`` templates in easyconfigs unit tests (`#1835 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1835>`__)
  * fix easyconfigs unit tests w.r.t. changes made in framework (`#1853 <https://github.com/hpcugent/easybuild-framework/pull/1853>`__, `#1870 <https://github.com/hpcugent/easybuild-framework/pull/1870>`__, `#1874 <https://github.com/hpcugent/easybuild-framework/pull/1874>`__, `#1875 <https://github.com/hpcugent/easybuild-framework/pull/1875>`__)
  * add GMP as missing dep in Python 2.7.10 easyconfigs, required for pycrypto extension (`#1858 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1858>`__)
  * specify installation prefix for SIP (`#1888 <https://github.com/hpcugent/easybuild-framework/pull/1888>`__, `#1892 <https://github.com/hpcugent/easybuild-framework/pull/1892>`__)
  * add custom sanity check paths in various easyconfigs (`#1889 <https://github.com/hpcugent/easybuild-framework/pull/1889>`__, `#1894 <https://github.com/hpcugent/easybuild-framework/pull/1894>`__, `#1897 <https://github.com/hpcugent/easybuild-framework/pull/1897>`__ - `#1909 <https://github.com/hpcugent/easybuild-framework/pull/1909>`__)

    * required because of fix in EasyBuild framework, causing default sanity check paths to be considered
      for extensions that are installed as a module
    * affected easyconfigs include: AnalyzeFMRI, Biggus, bibtexparser, DB_File, DBD-Pg, DBD-SQLite, DBD-mysql, evmix,
      fmri, FPM, GraphViz, gsl, GSSAPI, MDP, mpi4py, ncdf, ncdf4, netifaces, NetLibIDN, networkx, ordereddict,
      Parallel-ForkManager,  paycheck, PyQuante, Pyke, PyQt, r2py, rjags, runjags, scikit-learn, SOBAcl,
      vsc-processcontrol, vsc-mympirun-scoop, XML, XML-Dumper, XML-Parser, XML-Twig, YAML-Syck

  * don't enable '``static``' toolchain option in SuiteSparse 4.4.3 easyconfig (`#1911 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1911>`__)
  * add --exclude unpack options for OpenFOAM 2.3.1 to avoid cyclic symlink causing problems when unpacking (`#1925 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1925>`__)


.. _release_notes_eb220:

v2.2.0 (July 15th 2015)
-----------------------

feature + bugfix release

**framework**

* add support for using GC3Pie as a backend for ``--job`` (`#1008 <https://github.com/hpcugent/easybuild-framework/pull/1008>`__)

  * see also :ref:`submitting_jobs`

* add support for ``--include-*`` configuration options to include additional easyblocks, toolchains, etc. (`#1301 <https://github.com/hpcugent/easybuild-framework/pull/1301>`__)

  * see :ref:`including_additional_python_modules`

* add (experimental) support for packaging installed software using FPM (`#1224 <https://github.com/hpcugent/easybuild-framework/pull/1224>`__)

  * see :ref:`packaging_support`

* various other enhancements, including:

  * use https for PyPI URL templates (`#1286 <https://github.com/hpcugent/easybuild-framework/pull/1286>`__)
  * add GNU toolchain definition (`#1287 <https://github.com/hpcugent/easybuild-framework/pull/1287>`__)
  * make bootstrap script more robust (`#1289 <https://github.com/hpcugent/easybuild-framework/pull/1289>`__, `#1325 <https://github.com/hpcugent/easybuild-framework/pull/1325>`__):

    * exclude 'easyblocks' pkg from ``sys.path`` to avoid that ``setup.py`` for easybuild-easyblocks picks up wrong version
    * undefine ``$EASYBUILD_BOOTSTRAP*`` environment variables, since they do not correspond with known config options

  * improve error reporting/robustness in ``fix_broken_easyconfigs.py`` script (`#1290 <https://github.com/hpcugent/easybuild-framework/pull/1290>`__)
  * reset keep toolchain component class 'constants' every time (`#1294 <https://github.com/hpcugent/easybuild-framework/pull/1294>`__)
  * make ``--strict`` also a build option (`#1295 <https://github.com/hpcugent/easybuild-framework/pull/1295>`__)
  * fix purging of loaded modules in unit tests' setup method (`#1297 <https://github.com/hpcugent/easybuild-framework/pull/1297>`__)
  * promote ``MigrateFromEBToHMNS`` to a 'production' MNS (`#1302 <https://github.com/hpcugent/easybuild-framework/pull/1302>`__)
  * add support for ``--read-only-installdir`` and ``--group-writable-installdir`` configuration options (`#1304 <https://github.com/hpcugent/easybuild-framework/pull/1304>`__)
  * add support for *not* expanding relative paths in ``prepend_paths`` (`#1310 <https://github.com/hpcugent/easybuild-framework/pull/1310>`__)
  * enhance ``EasyConfig.dump()`` method to use easyconfig templates where possible (`#1314 <https://github.com/hpcugent/easybuild-framework/pull/1314>`__), `#1319 <https://github.com/hpcugent/easybuild-framework/pull/1319>`__), `#1320 <https://github.com/hpcugent/easybuild-framework/pull/1320>`__), `#1321 <https://github.com/hpcugent/easybuild-framework/pull/1321>`__)

* various bug fixes, including:

  * fix issue with cleaning up (no) logfile if ``--logtostdout``/``-l`` is used (`#1298 <https://github.com/hpcugent/easybuild-framework/pull/1298>`__)
  * stop making ``ModulesTool`` class a singleton since it causes problems when multilple toolchains are in play (`#1299 <https://github.com/hpcugent/easybuild-framework/pull/1299>`__)
  * don't modify values of 'paths' list passed as argument to prepend_paths in ``ModuleGenerator`` (`#1300 <https://github.com/hpcugent/easybuild-framework/pull/1300>`__)
  * fix issue with ``EasyConfig.dump()`` + cleanup (`#1308 <https://github.com/hpcugent/easybuild-framework/pull/1308>`__), `#1311 <https://github.com/hpcugent/easybuild-framework/pull/1311>`__)
  * reenable (and fix) accidentally disabled test (`#1316 <https://github.com/hpcugent/easybuild-framework/pull/1316>`__)

**easyblocks**

* modified easybuild.easyblocks package declaration to support giving preference to custom easyblocks (`#617 <https://github.com/hpcugent/easybuild-easyblocks/pull/617>`__)
* 2 new generic easyblocks: RubyGem (`#565 <https://github.com/hpcugent/easybuild-easyblocks/pull/565>`__), SystemCompiler (`#633 <https://github.com/hpcugent/easybuild-easyblocks/pull/633>`__)
* new easyblocks for 5 software packages that require customized support:

  * NEMO (`#564 <https://github.com/hpcugent/easybuild-easyblocks/pull/564>`__), pbdMPI (`#612 <https://github.com/hpcugent/easybuild-framework/pull/612>`__), `#620 <https://github.com/hpcugent/easybuild-framework/pull/620>`__), pbdSLAP (`#620 <https://github.com/hpcugent/easybuild-easyblocks/pull/620>`__), PDT (`#624 <https://github.com/hpcugent/easybuild-easyblocks/pull/624>`__), Ruby (`#565 <https://github.com/hpcugent/easybuild-easyblocks/pull/565>`__)

* various other enhancements, including:

  * update CUDA easyblock for v6.x (`#476 <https://github.com/hpcugent/easybuild-easyblocks/pull/476>`__)
  * make METIS easyblock take into account configopts (`#494 <https://github.com/hpcugent/easybuild-easyblocks/pull/494>`__)
  * enable building of EOMIP and EOMEA for NWChem versions 6.5 and up (`#508 <https://github.com/hpcugent/easybuild-easyblocks/pull/508>`__)
  * make out-of-source build with CMake truly out-of-source (`#615 <https://github.com/hpcugent/easybuild-easyblocks/pull/615>`__)
  * add support in Bundle easyblock to run full sanity check (`#627 <https://github.com/hpcugent/easybuild-easyblocks/pull/627>`__)
  * also take platform-specific Python lib dirs into account in PythonPackage easyblock (`#628 <https://github.com/hpcugent/easybuild-easyblocks/pull/628>`__)
  * fix mpivars scripts in Intel MPI installation for versions where the installation is moved (`#629 <https://github.com/hpcugent/easybuild-easyblocks/pull/629>`__)
  * don't restrict ``det_pylibdir`` function to only EasyBuild-provided Python (`#631 <https://github.com/hpcugent/easybuild-framework/pull/631>`__), `#641 <https://github.com/hpcugent/easybuild-framework/pull/641>`__)
  * support snappy and other optional native libs in Hadoop easyblock (`#632 <https://github.com/hpcugent/easybuild-framework/pull/632>`__), `#638 <https://github.com/hpcugent/easybuild-framework/pull/638>`__), `#640 <https://github.com/hpcugent/easybuild-framework/pull/640>`__), `#642 <https://github.com/hpcugent/easybuild-framework/pull/642>`__)

* various bug fixes, including:

  * fix Xmipp easyblock, use provided ``install.sh`` script (`#630 <https://github.com/hpcugent/easybuild-easyblocks/pull/630>`__)
  * update Clang easyblock to disable tests that may fail when unlimited stack size is used (`#622 <https://github.com/hpcugent/easybuild-easyblocks/pull/622>`__)
  * fix setting of ``$INTEL_LICENSE_FILE`` for port@server values (`#635 <https://github.com/hpcugent/easybuild-easyblocks/pull/635>`__)

**easyconfigs**

* added example easyconfig files for **62** new software packages:

  * ADF (`#899 <https://github.com/hpcugent/easybuild-easyconfigs/pull/899>`__), AutoDock_Vina (`#808 <https://github.com/hpcugent/easybuild-easyconfigs/pull/808>`__), bibtexparser (`#1726 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1726>`__), Biggus (`#1770 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1770>`__), Bismark (`#990 <https://github.com/hpcugent/easybuild-easyconfigs/pull/990>`__), blasr (`#1662 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1662>`__), BSMAP (`#1171 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1171>`__),
    Check (`#811 <https://github.com/hpcugent/easybuild-easyconfigs/pull/811>`__), Circuitscape (`#1222 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1222>`__), CONTRAfold (`#689 <https://github.com/hpcugent/easybuild-easyconfigs/pull/689>`__), cramtools (`#1741 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1741>`__), DBD-Pg (`#1066 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1066>`__), DendroPy (`#995 <https://github.com/hpcugent/easybuild-easyconfigs/pull/995>`__),
    EMAN2 (`#1737 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1737>`__), ETSF_IO (`#727 <https://github.com/hpcugent/easybuild-easyconfigs/pull/727>`__), eudev (`#1578 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1578>`__), fastqc (`#1636 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1636>`__), FDS (`#814 <https://github.com/hpcugent/easybuild-framework/pull/814>`__), `#1617 <https://github.com/hpcugent/easybuild-framework/pull/1617>`__), `#1625 <https://github.com/hpcugent/easybuild-framework/pull/1625>`__), FPM (`#1440 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1440>`__),
    frealign (`#1619 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1619>`__), g2log (`#1035 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1035>`__), GC3Pie (`#1692 <https://github.com/hpcugent/easybuild-framework/pull/1692>`__), `#1756 <https://github.com/hpcugent/easybuild-framework/pull/1756>`__), `#1768 <https://github.com/hpcugent/easybuild-framework/pull/1768>`__), GenotypeHarmonizer (`#1672 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1672>`__), gensim (`#1762 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1762>`__),
    GraphViz (`#1658 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1658>`__), hisat (`#1674 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1674>`__), IDBA-UD (`#1045 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1045>`__), IMa2 (`#828 <https://github.com/hpcugent/easybuild-easyconfigs/pull/828>`__), IMPUTE2 (`#824 <https://github.com/hpcugent/easybuild-easyconfigs/pull/824>`__), JUBE (`#1396 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1396>`__), LAMARC (`#760 <https://github.com/hpcugent/easybuild-easyconfigs/pull/760>`__),
    libXScrnSaver (`#1653 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1653>`__), MATIO (`#1004 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1004>`__), MuTect (`#1483 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1483>`__), ncdf (`#617 <https://github.com/hpcugent/easybuild-easyconfigs/pull/617>`__), NEMO (`#1640 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1640>`__), ngspice (`#1116 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1116>`__),
    ordereddict (`#1774 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1774>`__), OSU Micro-Benchmarks (`#1777 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1777>`__), Parallel-ForkManager (`#847 <https://github.com/hpcugent/easybuild-easyconfigs/pull/847>`__), pBWA (`#1009 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1009>`__), PeakSeq (`#1412 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1412>`__),
    Pillow (`#1702 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1702>`__), Pindel (`#1126 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1126>`__), PLUMED (`#1596 <https://github.com/hpcugent/easybuild-framework/pull/1596>`__), `#1665 <https://github.com/hpcugent/easybuild-framework/pull/1665>`__), PostgreSQL (`#1066 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1066>`__), PROJ (`#1006 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1006>`__), PyAMG (`#1222 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1222>`__), Pyke (`#1776 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1776>`__),
    rpy2 (`#1775 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1775>`__), Sailfish (`#1035 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1035>`__), SCANMS (`#1386 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1386>`__), Seaborn (`#1763 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1763>`__), snpEff (`#1680 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1680>`__), SOBAcl (`#1658 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1658>`__),
    SPIDER (`#1624 <https://github.com/hpcugent/easybuild-framework/pull/1624>`__), `#1723 <https://github.com/hpcugent/easybuild-framework/pull/1723>`__), STAR (`#1043 <https://github.com/hpcugent/easybuild-framework/pull/1043>`__), `#1676 <https://github.com/hpcugent/easybuild-framework/pull/1676>`__), system GCC (`#1778 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1778>`__), tabix (`#1059 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1059>`__), tecplot360ex (`#1100 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1100>`__), Vampir (`#512 <https://github.com/hpcugent/easybuild-easyconfigs/pull/512>`__),
    VampirServer (`#512 <https://github.com/hpcugent/easybuild-easyconfigs/pull/512>`__), verifyBamID (`#1675 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1675>`__)

* added easyconfigs for 4 new software bundles:

  * R-bundle-Bioconductor (`#1573 <https://github.com/hpcugent/easybuild-framework/pull/1573>`__), `#1795 <https://github.com/hpcugent/easybuild-framework/pull/1795>`__), R-bundle-devtools (`#1621 <https://github.com/hpcugent/easybuild-framework/pull/1621>`__), `#1759 <https://github.com/hpcugent/easybuild-framework/pull/1759>`__), R-bundle-extra (`#1387 <https://github.com/hpcugent/easybuild-framework/pull/1387>`__), `#1759 <https://github.com/hpcugent/easybuild-framework/pull/1759>`__), R-bundle-pbd (`#1659 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1659>`__)

* added easyconfigs for new GNU toolchain (`#1346 <https://github.com/hpcugent/easybuild-framework/pull/1346>`__), `#1669 <https://github.com/hpcugent/easybuild-framework/pull/1669>`__)
* added new easyconfigs for existing toolchains: goolf/1.5.16, intel/2014.06
* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including BLAST 2.2.31+, Clang 3.6.1, CUDA 6.x, GCC 4.9.3, GROMACS 5.0.5, HDF5 1.8.15 + 1.8.15-patch1,
    Python 2.7.10, R 3.2.0 + 3.2.1, WRF 3.6.1

* various other enhancements, including:

  * update all ncurses easyconfigs to enable ncursesw and use ConfigureMake easyblock (`#1337 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1337>`__)
  * update PDT easyconfigs to use PDT easyblock (`#1687 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1687>`__)
  * add custom ``sanity_check_paths`` in libxml2 easyconfigs (`#1690 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1690>`__)
  * enhance unit tests to also cover EasyConfig.dump() method on all easyconfigs (`#1761 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1761>`__)
  * include snappy as dependency in Hadoop easyconfigs (`#1758 <https://github.com/hpcugent/easybuild-framework/pull/1758>`__), `#1773 <https://github.com/hpcugent/easybuild-framework/pull/1773>`__)
  * enable SSL support in CMake v3.2.3 easyconfigs (`#1784 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1784>`__)
  * add additional extensions in R easyconfigs (`#1637 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1637>`__)

* various bug fixes, including:

  * add patch file required for correct CUDA-aware OpenMPI v1.7.3 build (`#631 <https://github.com/hpcugent/easybuild-easyconfigs/pull/631>`__)
  * fix issue with OpenMPI dependency in ECore easyconfigs (`#777 <https://github.com/hpcugent/easybuild-easyconfigs/pull/777>`__)
  * don't run the Bloom tests for Jellyfish, they can randomly fail (`#1016 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1016>`__)
  * fix source URLs in BioPerl easyconfigs (`#1075 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1075>`__)
  * patch out svnversion command in Python 2.5.6 to fix build on recent systems (`#1576 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1576>`__)
  * consistently use https for PyPI URLs in homepage/source_urls (`#1616 <https://github.com/hpcugent/easybuild-framework/pull/1616>`__), `#1722 <https://github.com/hpcugent/easybuild-framework/pull/1722>`__)
  * include Tcl and Tk as dependencies in R easyconfig (`#1623 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1623>`__)
  * add patch for installing paycheck as Py3 extension (`#1629 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1629>`__)
  * add Perl dependency in git 2.x easyconfigs (`#1631 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1631>`__)
  * fix easyconfig for GMP 6.0.0, don't use 6.0.0a sources (`#1635 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1635>`__)
  * fix source_urls in QuantumESPRESSO 5.0.2 easyconfigs (`#1652 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1652>`__)
  * include Tk as dependency in Python 2.7.9 easyconfigs (`#1654 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1654>`__)
  * include tk-devel is list of OS deps for Python 2.7.9 Cray easyconfigs, make sure '``import Tkinter``' works (`#1655 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1655>`__)
  * drop gpfs versionsuffix and stop using no longer existing ``--enable-gpfs`` configopt for recent HDF5 versions (`#1657 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1657>`__)
  * include missing libxml2 dep in GLib easyconfigs (`#1666 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1666>`__)
  * fix source URLs in Qt easyconfigs (`#1673 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1673>`__)
  * fix source URLs for argparse Python extension (`#1697 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1697>`__)
  * fix source URLs for deap Python extension (`#1699 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1699>`__)
  * fix easyconfigs unit tests after making ModulesTool a non-singleton class (`#1708 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1708>`__)
  * fix names for Xmipp easyconfigs and patches (`#1719 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1719>`__)
  * add patch for Qt 4.8.6 to fix build issue on RHEL6 with intel/2015a (`#1734 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1734>`__)
  * add M4 as build dep for GCC 5.1.0 (`#1735 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1735>`__)
  * fix Bioconductor extension versions in R 3.1.3 easyconfigs (`#1748 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1748>`__)
  * remove custom exts_filter definition from Python 3.4.3 easyconfig (`#1765 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1765>`__)
  * fix source_urls in netCDF easyconfigs (`#1766 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1766>`__)
  * fix source_urls in netCDF-C++ and netCDF-Fortran easyconfigs (`#1767 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1767>`__)

.. _release_notes_eb211:

v2.1.1 (May 18th 2015)
----------------------

bugfix release

**framework**

* fix issue with missing load statements when ``--module-only`` is used, don't skip ready/prepare steps (`#1276 <https://github.com/hpcugent/easybuild-framework/pull/1276>`__)
* enhance ``--search``: only consider actual filename (not entire path), use regex syntax (`#1281 <https://github.com/hpcugent/easybuild-framework/pull/1281>`__)
* various other bug fixes, including:

  * fix ``generate_software_list.py`` script w.r.t. dependencies marked as external modules (`#1273 <https://github.com/hpcugent/easybuild-framework/pull/1273>`__)
  * only use ``$LMOD_CMD`` value if ``lmod`` binary can't be found in $PATH (`#1275 <https://github.com/hpcugent/easybuild-framework/pull/1275>`__)
  * fix location of ``module_only`` build option w.r.t. default value (`#1277 <https://github.com/hpcugent/easybuild-framework/pull/1277>`__)
  * fix combined use of ``--hide-deps`` and ``hiddendependencies`` (`#1280 <https://github.com/hpcugent/easybuild-framework/pull/1280>`__)
  * remove log handlers that were added during tests, to ensure effective cleanup of log files (`#1282 <https://github.com/hpcugent/easybuild-framework/pull/1282>`__)

    * this makes the unit test suite run ~3x faster!

  * define ``$CRAYPE_LINK_TYPE`` if '``dynamic``' toolchain option is enabled for Cray compiler wrappers (`#1283 <https://github.com/hpcugent/easybuild-framework/pull/1283>`__)

**easyblocks**

* fix compatibility of easyblocks with ``--module-only`` + dedicated unit test module (`#610 <https://github.com/hpcugent/easybuild-easyblocks/pull/610>`__)
* minor enhancements, including:

  * update GROMACS easyblock for version 5 (`#513 <https://github.com/hpcugent/easybuild-easyblocks/pull/513>`__)

* various other bug fixes, including:

  * only check compiler being used if FFTW interfaces are being built in Intel MKL easyblock (`#606 <https://github.com/hpcugent/easybuild-easyblocks/pull/606>`__)

**easyconfigs**

* added example easyconfig files for **3** new software packages:

  * networkx (`#1592 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1592>`__), Platanus (`#1597 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1597>`__), SaguaroGW (`#1600 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1600>`__)

* added new easyconfigs for existing toolchains: ``ictce/7.3.5``, ``CrayCCE/5.2.40``, ``CrayGNU/5.2.40``, ``CrayIntel/5.2.40``
* added easyconfigs using ``CrayGNU/5.2.25`` and ``CrayGNU/5.2.40`` toolchains (`#1610 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1610>`__, `#1611 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1611>`__)
* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including Boost 1.58.0, GROMACS 5.0.4, Python 3.4.3

* various bug fixes, including:

  * enable usempi in GROMACS easyconfig using CrayGNU toolchain (as required by GROMACS easyblock) (`#1590 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1590>`__)
  * use system-provided tcsh when building WRF on Cray systems, to avoid hanging build (`#1595 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1595>`__)
  * only use '``dynamic``' toolchain option, not '``shared``', in easyconfigs using Cray toolchain (`#1609 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1609>`__)

.. _release_notes_v2.1.0:

v2.1.0 (April 30th 2015)
------------------------

feature + bugfix release

**framework**

* requires vsc-base v2.2.0 or more recent

  * added support for LoggedException (`vsc-base#160 <https://github.com/hpcugent/vsc-base/pull/160>`__, `vsc-base#163 <https://github.com/hpcugent/vsc-base/pull/163>`__, `vsc-base#165 <https://github.com/hpcugent/vsc-base/pull/165>`__, `vsc-base#167 <https://github.com/hpcugent/vsc-base/pull/167>`__)
  * added support for add_flex action in GeneralOption (`vsc-base#162 <https://github.com/hpcugent/vsc-base/pull/162>`__)
  * added support to GeneralOption to act on unknown configuration environment variables (`vsc-base#162 <https://github.com/hpcugent/vsc-base/pull/162>`__)

* add support for only (re)generating module files: ``--module-only`` (`#1018 <https://github.com/hpcugent/easybuild-framework/pull/1018>`__)

  * module naming scheme API is enhanced to include det_install_subdir method
  * see :ref:`module_only`

* add support for generating module files in Lua syntax (note: requires Lmod as modules tool) (`#1060 <https://github.com/hpcugent/easybuild-framework/pull/1060>`__, `#1255 <https://github.com/hpcugent/easybuild-framework/pull/1255>`__, `#1256 <https://github.com/hpcugent/easybuild-framework/pull/1256>`__, `#1270 <https://github.com/hpcugent/easybuild-framework/pull/1270>`__)

  * see ``--module-syntax`` configuration option and :ref:`module_syntax`

* deprecate ``log.error`` method in favor of raising ``EasyBuildError`` exception (`#1218 <https://github.com/hpcugent/easybuild-framework/pull/1218>`__)

  * see :ref:`depr_error_reporting`

* add support for using external modules as dependencies, and to provide metadata for external modules (`#1230 <https://github.com/hpcugent/easybuild-framework/pull/1230>`__, `#1265 <https://github.com/hpcugent/easybuild-framework/pull/1265>`__, `#1267 <https://github.com/hpcugent/easybuild-framework/pull/1267>`__)

  * see :ref:`using_external_modules`

* add experimental support for Cray toolchains on top of PrgEnv modules: ``CrayGNU``, ``CrayIntel``, ``CrayCCE`` (`#1234 <https://github.com/hpcugent/easybuild-framework/pull/1234>`__, `#1268 <https://github.com/hpcugent/easybuild-framework/pull/1268>`__)

  *  see https://github.com/hpcugent/easybuild/wiki/EasyBuild-on-Cray

* various other enhancements, including:

  * clear list of checksums when using ``--try-software-version`` (`#1169 <https://github.com/hpcugent/easybuild-framework/pull/1169>`__)
  * sort the results of searching for files (e.g., ``--search`` output) (`#1214 <https://github.com/hpcugent/easybuild-framework/pull/1214>`__)
  * enhance test w.r.t. use of templates in cfgfile (`#1217 <https://github.com/hpcugent/easybuild-framework/pull/1217>`__)
  * define '``%(DEFAULT_REPOSITORYPATH)s``' template for cfgfiles (see ``eb --avail-cfgfile-constants``) (`#1220 <https://github.com/hpcugent/easybuild-framework/pull/1220>`__)
  * also reset ``$LD_PRELOAD`` when running module commands, in case module defined ``$LD_PRELOAD`` (`#1222 <https://github.com/hpcugent/easybuild-framework/pull/1222>`__)
  * move location of '``module use``' statements in generated module file (*after* '``module load``' statements) (`#1232 <https://github.com/hpcugent/easybuild-framework/pull/1232>`__)
  * add support for ``--show-default-configfiles`` (`#1240 <https://github.com/hpcugent/easybuild-framework/pull/1240>`__)

    * see :ref:`default_configuration_files`

  * report error on missing configuration files, rather than ignoring them (`#1240 <https://github.com/hpcugent/easybuild-framework/pull/1240>`__)
  * clean up commit message used in easyconfig git repository (`#1248 <https://github.com/hpcugent/easybuild-framework/pull/1248>`__)
  * add ``--hide-deps`` configuration option to specify names of software that must be installed as hidden modules (`#1250 <https://github.com/hpcugent/easybuild-framework/pull/1250>`__)

    * see :ref:`hide_deps`

  * add support for appending/prepending to ``--robot-paths`` to avoid overwriting default robot search path (`#1252 <https://github.com/hpcugent/easybuild-framework/pull/1252>`__)

    * see :ref:`robot_search_path_prepend_append`

  * enable detection of use of unknown ``$EASYBUILD``-prefixed environment variables (`#1253 <https://github.com/hpcugent/easybuild-framework/pull/1253>`__)

    * see :ref:`configuration_env_vars`

  * add ``--installpath-modules`` and ``--installpath-software`` configuration options (`#1258 <https://github.com/hpcugent/easybuild-framework/pull/1258>`__)

    * see :ref:`installpath`

  * use dedicated subdirectory in temporary directory for each test to ensure better cleanup (`#1260 <https://github.com/hpcugent/easybuild-framework/pull/1260>`__)
  * get rid of ``$PROFILEREAD`` hack when running commands, not needed anymore (`#1264 <https://github.com/hpcugent/easybuild-framework/pull/1264>`__)

* various bug fixes, including:

  * make bootstrap script robust against having ``vsc-base`` already available in Python search path (`#1212 <https://github.com/hpcugent/easybuild-framework/pull/1212>`__, `#1215 <https://github.com/hpcugent/easybuild-framework/pull/1215>`__)
  * set default value for unpack_options easyconfig parameter to ``''``, so ``self.cfg.update`` works on it (`#1229 <https://github.com/hpcugent/easybuild-framework/pull/1229>`__)
  * also copy rotated log files (`#1238 <https://github.com/hpcugent/easybuild-framework/pull/1238>`__)
  * fix parsing of ``--download-timeout`` value (`#1242 <https://github.com/hpcugent/easybuild-framework/pull/1242>`__)
  * make ``test_XDG_CONFIG_env_vars`` unit test robust against existing user config file in default location (`#1259 <https://github.com/hpcugent/easybuild-framework/pull/1259>`__)
  * fix minor robustness issues w.r.t. ``$XDG_CONFIG*`` and ``$PYTHONPATH`` in unit tests (`#1262 <https://github.com/hpcugent/easybuild-framework/pull/1262>`__)
  * fix issue with handling empty toolchain variables (`#1263 <https://github.com/hpcugent/easybuild-framework/pull/1263>`__)

**easyblocks**

* replace '``log.error``' with '``raise EasyBuildError``' in all easyblocks (`#588 <https://github.com/hpcugent/easybuild-easyblocks/pull/588>`__)
* one new generic easyblock: ``ConfigureMakePythonPackage`` (`#540 <https://github.com/hpcugent/easybuild-easyblocks/pull/540>`__)
* new easyblocks for 2 software packages that require customized support:

  * TINKER (`#578 <https://github.com/hpcugent/easybuild-easyblocks/pull/578>`__), Xmipp (`#581 <https://github.com/hpcugent/easybuild-easyblocks/pull/581>`__)

* various other enhancements, including:

  * enhance WIEN2k easyblock for recent versions + cleanup (`#486 <https://github.com/hpcugent/easybuild-easyblocks/pull/486>`__)
  * define ``$PYTHONNOUSERSITE`` in PythonPackage easyblock so user-installed packages are not picked up (`#577 <https://github.com/hpcugent/easybuild-easyblocks/pull/577>`__)
  * add support in CP2K easyblock for building on top of MPICH/MPICH2 (`#579 <https://github.com/hpcugent/easybuild-easyblocks/pull/579>`__)
  * enhance Hadoop easyblock to support parallel builds (`#580 <https://github.com/hpcugent/easybuild-easyblocks/pull/580>`__)
  * drop ``-noroot`` for recent FLUENT versions, honor ``installopts``, enable ``-debug`` (`#582 <https://github.com/hpcugent/easybuild-easyblocks/pull/582>`__)
  * include ``prebuildopts`` in build command for Python packages (`#585 <https://github.com/hpcugent/easybuild-easyblocks/pull/585>`__)
  * also install ``rosetta_tools`` subdirectory for Rosetta (`#586 <https://github.com/hpcugent/easybuild-easyblocks/pull/586>`__)
  * update SLEPc easyblock for v3.5 + style cleanup (`#593 <https://github.com/hpcugent/easybuild-easyblocks/pull/593>`__)
  * minor fix in HPL easyblock w.r.t. checking defined environment variables (`#595 <https://github.com/hpcugent/easybuild-easyblocks/pull/595>`__)
  * tweak CP2K easyblock w.r.t. LAPACK/FFTW support (`#596 <https://github.com/hpcugent/easybuild-easyblocks/pull/596>`__)
  * minor update to GCC easyblock to support GCC v5.x (`#598 <https://github.com/hpcugent/easybuild-easyblocks/pull/598>`__)
  * update sanity check in R easyblock for version 3.2.0 (`#602 <https://github.com/hpcugent/easybuild-easyblocks/pull/602>`__)

* various bug fixes, including:

  * fix Score-P easyblock for compiler-only toolchains, include Qt as optional dependecy (`#552 <https://github.com/hpcugent/easybuild-easyblocks/pull/552>`__)
  * fix definition of ``$MKLROOT``, should be set to '``mkl``' subdir of install dir (`#576 <https://github.com/hpcugent/easybuild-easyblocks/pull/576>`__)
  * add ``-libmpichf90`` to list of MPI libraries in NWChem easyblock (`#584 <https://github.com/hpcugent/easybuild-easyblocks/pull/584>`__)
  * stop using '``$root``' to make easyblocks compatible with module files in Lua syntax (`#590 <https://github.com/hpcugent/easybuild-easyblocks/pull/590>`__)
  * also set ``$PYTHONPATH`` before installing Python package in temporary directory in ``test_step`` (`#591 <https://github.com/hpcugent/easybuild-easyblocks/pull/591>`__)
  * unset ``buildopts``/``installopts`` before installing Python extensions in Python easyblock (`#597 <https://github.com/hpcugent/easybuild-easyblocks/pull/597>`__)
  * allow not including vsc-base sources when installing EasyBuild (gets installed with easybuild-framework) (`#600 <https://github.com/hpcugent/easybuild-easyblocks/pull/600>`__)
  * use ``self.initial_environ`` rather than ``self.orig_environ`` in EasyBuildMeta easyblock (`#600 <https://github.com/hpcugent/easybuild-easyblocks/pull/600>`__)
  * make GCC easyblock compatible with ``--module-only`` by setting default value for ``self.platform_lib`` in constructor (`#603 <https://github.com/hpcugent/easybuild-easyblocks/pull/603>`__)


**easyconfigs**

* added example easyconfig files for **27** new software packages:

  * AFNI (`#1322 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1322>`__, `#1521 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1521>`__), BCFtools (`#1492 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1492>`__), getdp (`#1518 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1518>`__), gmsh (`#1518 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1518>`__), gtest (`#1244 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1244>`__), hanythingondemand (`#1530 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1530>`__), mawk (`#1369 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1369>`__), Minimac (`#815 <https://github.com/hpcugent/easybuild-easyconfigs/pull/815>`__), Minimac3 (`#1502 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1502>`__), monty (`#1548 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1548>`__), Octave (`#1563 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1563>`__), pbs_python (`#1530 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1530>`__), pigz (`#1036 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1036>`__), Pygments (`#1536 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1536>`__), pyhull (`#1539 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1539>`__), pymatgen (`#1549 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1549>`__), PyQt (`#1322 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1322>`__, `#1521 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1521>`__), Ray (`#1494 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1494>`__), requests (`#1536 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1536>`__), seqtk (`#1524 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1524>`__), SIP (`#1322 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1322>`__, `#1521 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1521>`__), S-Lang (`#1369 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1369>`__), Spark (`#1554 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1554>`__), spglib (`#1549 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1549>`__), TINKER (`#1465 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1465>`__), tmux (`#1369 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1369>`__), Xmipp (`#1489 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1489>`__)

* added easyconfigs for new (Cray-specific) toolchains (`#1538 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1538>`__): ``CrayGNU``, ``CrayIntel``, ``CrayCCE``

  * initially supported software (using CrayGNU toolchains): CP2K, GROMACS, HPL, Python + numpy/scipy, WRF (`#1558 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1558>`__)
  * see also https://github.com/hpcugent/easybuild/wiki/EasyBuild-on-Cray

* added new easyconfigs for existing toolchains: ``goolf/1.5.16``, ``intel/2014.06``
* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including GCC v5.1.0, OpenFOAM v2.3.1, R v3.1.3 and v3.2.0, PETSc/SLEPc v3.5.3, WIEN2k v14.1

* various other enhancements, including:

  * include pbr dependency for lockfile Python extension in Python v2.7.9 easyconfigs + mock/pytz/pandas (`#1462 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1462>`__, `#1540 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1540>`__)
  * include SQLite as dependency in Python v2.7.9 easyconfigs (`#1468 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1468>`__)
  * set ``$LD_PRELOAD`` for Hoard and jemalloc (`#1470 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1470>`__)
  * fix homepage in SCOTCH easyconfigs (`#1485 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1485>`__)
  * adding missing six/ecdsa dependencies for dateutil/paramiko Python packages in Python easyconfigs (`#1504 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1504>`__, `#1505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1505>`__, `#1506 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1506>`__, `#1507 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1507>`__, `#1508 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1508>`__, `#1509 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1509>`__, `#1510 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1510>`__)
  * enable ``pic`` toolchain option in expat easyconfigs (`#1562 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1562>`__)
  * extend list of source URLs for Bioconductor packages in R easyconfigs to include 'release' source URLs (`#1568 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1568>`__)

* various bug fixes, including:

  * adding missing zlib dependency in all Tcl easyconfig files (`#1344 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1344>`__)
  * fix homepage in FLUENT easyconfigs (`#1472 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1472>`__)
  * use ``--with-verbs`` rather than deprecated ``--with-openib`` in OpenMPI configure options (`#1511 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1511>`__)
  * stop relying on ``OS_NAME`` constant to specify OS dependencies in OpenMPI easyconfigs (`#1512 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1512>`__)
  * replace use of '``$root``' with '``%(installdir)s``' to ensure compatibility with module files in Lua syntax (`#1532 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1532>`__)
  * stop relying on '``$MKLROOT``' in ROOT easyconfigs (`#1537 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1537>`__)
  * use proper Bundle easyblock for biodeps/PRACE (`#1566 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1566>`__)
  * make source_urls in Cube and Scalasca easyconfigs compatible with --try-software-version (`#1574 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1574>`__)
  * add patch for Cube to fix configure script w.r.t. Qt dependency, add --without-java-reader configure option (`#1574 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1574>`__)

.. _release_notes_v2.0.0:

v2.0.0 (March 6th 2015)
-----------------------

feature + bugfix release

**framework**

* requires vsc-base v2.0.3 or more recent

  * avoid deprecation warnings w.r.t. use of ``message`` attribute (`vsc-base#155 <https://github.com/hpcugent/vsc-base/pull/155>`__)
  * fix typo in log message rendering ``--ignoreconfigfiles`` unusable (`vsc-base#158 <https://github.com/hpcugent/vsc-base/pull/158>`__)
* removed functionality that was deprecated for EasyBuild version 2.0 (`#1143 <https://github.com/hpcugent/easybuild-framework/pull//1143>`__)

  * see :ref:`removed_functionality`
  * the fix_broken_easyconfigs.py script can be used to update easyconfig files suffering from this (`#1151 <https://github.com/hpcugent/easybuild-framework/pull//1151>`__, `#1206 <https://github.com/hpcugent/easybuild-framework/pull//1206>`__, `#1207 <https://github.com/hpcugent/easybuild-framework/pull//1207>`__)
  * for more information about this script, see :ref:`fix_broken_easyconfigs_script`
* stop including a crippled copy of vsc-base, include vsc-base as a proper dependency instead (`#1160 <https://github.com/hpcugent/easybuild-framework/pull//1160>`__, `#1194 <https://github.com/hpcugent/easybuild-framework/pull//1194>`__)

  * vsc-base is automatically installed as a dependency for easybuild-framework, if a Python installation tool is used
  * see :ref:`required_python_packages`
* various other enhancements, including:

  * add support for Linux/POWER systems (`#1044 <https://github.com/hpcugent/easybuild-framework/pull//1044>`__)
  * major cleanup in ``tools/systemtools.py`` + significantly enhanced tests (`#1044 <https://github.com/hpcugent/easybuild-framework/pull//1044>`__)
  * add support for '``eb -a rst``', list available easyconfig parameters in ReST format (`#1131 <https://github.com/hpcugent/easybuild-framework/pull//1131>`__)
  * add support for specifying one or more easyconfigs in combination with ``--from-pr`` (`#1132 <https://github.com/hpcugent/easybuild-framework/pull//1132>`__)

    * see :ref:`from_pr_specifying_easyconfigs`
  * define ``__contains__`` in EasyConfig class (`#1155 <https://github.com/hpcugent/easybuild-framework/pull//1155>`__)
  * restore support for downloading over a proxy (`#1158 <https://github.com/hpcugent/easybuild-framework/pull//1158>`__)

    * i.e., use ``urllib2`` rather than ``urllib``
    * this involved sacrificing the download progress report (which was only visible in the log file)
  * let ``mpi_family`` return ``None`` if MPI is not supported by a toolchain (`#1164 <https://github.com/hpcugent/easybuild-framework/pull//1164>`__)
  * include support for specifying system-level configuration files for EasyBuild via ``$XDG_CONFIG_DIRS`` (`#1166 <https://github.com/hpcugent/easybuild-framework/pull//1166>`__)

    * see :ref:`default_configuration_files`
  * make unit tests more robust (`#1167 <https://github.com/hpcugent/easybuild-framework/pull//1167>`__, `#1196 <https://github.com/hpcugent/easybuild-framework/pull//1196>`__)

    * see :ref:`unit_tests`
  * add hierarchical module naming scheme categorizing modules by ``moduleclass`` (`#1176 <https://github.com/hpcugent/easybuild-framework/pull//1176>`__)
  * enhance bootstrap script to allow bootstrapping using supplied tarballs (`#1184 <https://github.com/hpcugent/easybuild-framework/pull//1184>`__)

    * see :ref:`bootstrap_advanced_options`
  * disable updating of Lmod user cache by default, add configuration option ``--update-modules-tool-cache`` (`#1185 <https://github.com/hpcugent/easybuild-framework/pull//1185>`__)

    * for now, only the Lmod user cache can be updated using ``--update-modules-tool-cache``
  * use available ``which()`` function, rather than running '``which``' via ``run_cmd`` (`#1192 <https://github.com/hpcugent/easybuild-framework/pull//1192>`__)
  * fix ``install-EasyBuild-develop.sh`` script w.r.t. vsc-base dependency (`#1193 <https://github.com/hpcugent/easybuild-framework/pull//1193>`__)
  * also consider robot search path when looking for specified easyconfigs (`#1201 <https://github.com/hpcugent/easybuild-framework/pull//1201>`__)

    * see :ref:`specifying_easyconfigs`
* various bug fixes, including:

  * stop triggering deprecated/no longer support functionality in unit tests (`#1126 <https://github.com/hpcugent/easybuild-framework/pull//1126>`__)
  * fix ``from_pr`` test by including dummy easyblocks for HPL and ScaLAPACK (`#1133 <https://github.com/hpcugent/easybuild-framework/pull//1133>`__)
  * escape use of '``%``' in string with command line options with ``--job`` (`#1135 <https://github.com/hpcugent/easybuild-framework/pull//1135>`__)
  * fix handling specified patch level 0 (+ enhance tests for fetch_patches method) (`#1139 <https://github.com/hpcugent/easybuild-framework/pull//1139>`__)
  * fix formatting issues in generated easyconfig file obtained via ``--try-X`` (`#1144 <https://github.com/hpcugent/easybuild-framework/pull//1144>`__)
  * use ``log.error`` in ``tools/toolchain/toolchain.py`` where applicable (`#1145 <https://github.com/hpcugent/easybuild-framework/pull//1145>`__)
  * stop hardcoding ``/tmp`` in ``mpi_cmd_for`` function (`#1146 <https://github.com/hpcugent/easybuild-framework/pull//1146>`__, `#1200 <https://github.com/hpcugent/easybuild-framework/pull//1200>`__)
  * correctly determine variable name for ``$EBEXTLIST`` when generating module file (`#1156 <https://github.com/hpcugent/easybuild-framework/pull//1156>`__)
  * do not ignore exit code of failing postinstall commands (`#1157 <https://github.com/hpcugent/easybuild-framework/pull//1157>`__)
  * fix rare case in which used easyconfig and copied easyconfig are the same (`#1159 <https://github.com/hpcugent/easybuild-framework/pull//1159>`__)
  * always filter hidden deps from list of dependencies (`#1161 <https://github.com/hpcugent/easybuild-framework/pull//1161>`__)
  * fix implementation of ``path_matches`` function in ``tools/filetools.py`` (`#1163 <https://github.com/hpcugent/easybuild-framework/pull//1163>`__)
  * make sure plain text keyring is used by unit tests (`#1165 <https://github.com/hpcugent/easybuild-framework/pull//1165>`__)
  * suppress creation of module symlinks for ``HierarchicalMNS`` (`#1173 <https://github.com/hpcugent/easybuild-framework/pull//1173>`__)
  * sort all lists obtained via ``glob.glob``, since they are in arbitrary order (`#1187 <https://github.com/hpcugent/easybuild-framework/pull//1187>`__)
  * stop modifying ``$MODULEPATH`` directly in ``setUp``/``tearDown`` of toolchain tests (`#1191 <https://github.com/hpcugent/easybuild-framework/pull//1191>`__)

**easyblocks**

* one new generic easyblock for installing a bundle of modules: ``Bundle`` (`#550 <https://github.com/hpcugent/easybuild-easyblocks/pull/550>`__)

  * and let the ``Toolchain`` generic easyblock derive from ``Bundle``
* new easyblocks for 2 software packages that require customized support:

  * GAMESS-US (`#470 <https://github.com/hpcugent/easybuild-easyblocks/pull/470>`__, `#544 <https://github.com/hpcugent/easybuild-easyblocks/pull/544>`__, `#558 <https://github.com/hpcugent/easybuild-easyblocks/pull/558>`__), Hadoop (`#563 <https://github.com/hpcugent/easybuild-easyblocks/pull/563>`__)
* various other enhancements, including:

  * move support for ``staged_install`` from CPLEX easyblock to generic ``Binary`` easyblock (`#502 <https://github.com/hpcugent/easybuild-easyblocks/pull/502>`__)
  * fix sanity check in picard easyblock for v1.119 that doesn't include ``sam.jar`` (`#522 <https://github.com/hpcugent/easybuild-easyblocks/pull/522>`__)
  * log warning message when unlinking jellyfish symlink fails in Trinity easyblock (`#534 <https://github.com/hpcugent/easybuild-easyblocks/pull/534>`__)
  * revamp ``EB_libint2`` easyblock into ``EB_Libint`` that works for both Libint v1x and v2.x (`#536 <https://github.com/hpcugent/easybuild-easyblocks/pull/536>`__)
  * update CP2K easyblock for recent versions (no more '``fes``') (`#537 <https://github.com/hpcugent/easybuild-easyblocks/pull/537>`__)
  * update SuiteSparse easyblock for recent versions (`#541 <https://github.com/hpcugent/easybuild-easyblocks/pull/541>`__)
  * fix easyblock unit tests after dropping support for deprecated behaviour in framework (`#543 <https://github.com/hpcugent/easybuild-easyblocks/pull/543>`__)
  * rework PSI easyblock to support future releases (`#545 <https://github.com/hpcugent/easybuild-easyblocks/pull/545>`__)
  * enable always generating a 'verbose' Makefile in the generic CMakeMake easyblock (`#546 <https://github.com/hpcugent/easybuild-easyblocks/pull/546>`__)
  * remove functionality in (generic) easyblocks that was deprecated for EasyBuild v2.0 (`#547 <https://github.com/hpcugent/easybuild-easyblocks/pull/547>`__)
  * enhance generic RPackage easyblock to support installing extensions in a separate prefix (`#551 <https://github.com/hpcugent/easybuild-easyblocks/pull/551>`__)
  * deprecate GenomeAnalysisTK easyblock, since it's basically equivalent to Tarball (`#557 <https://github.com/hpcugent/easybuild-easyblocks/pull/557>`__)
  * update SAMtools easyblock for v1.2 (`#562 <https://github.com/hpcugent/easybuild-easyblocks/pull/562>`__)
  * take ``preconfigopts`` easyconfig parameter into account in ROOT easyblock (`#566 <https://github.com/hpcugent/easybuild-easyblocks/pull/566>`__)
  * update easyblock for installing EasyBuild

    * to support bootstrapping with provided source tarballs (`#559 <https://github.com/hpcugent/easybuild-easyblocks/pull/559>`__)

    * to also cover vsc-base dependency, and verify ``easy-install.pth`` (`#567 <https://github.com/hpcugent/easybuild-easyblocks/pull/567>`__)
  * update disabling sanitizer tests for Clang 3.6 (`#570 <https://github.com/hpcugent/easybuild-easyblocks/pull/570>`__)
* various bug fixes, including:
  * fix handling of LTO in GCC easyblock (`#535 <https://github.com/hpcugent/easybuild-easyblocks/pull/535>`__)
  * relocate FDTD RPM to fix installation on SL6 (`#538 <https://github.com/hpcugent/easybuild-easyblocks/pull/538>`__)

**easyconfigs**

* added example easyconfig files for **29** new software packages:

  * bsoft (`#1353 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1353>`__), Coot (`#1400 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1400>`__), Cuby (`#1258 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1258>`__), DSRC (`#1242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1242>`__), Exonerate (`#568 <https://github.com/hpcugent/easybuild-easyconfigs/pull/568>`__), fastqz (`#1242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1242>`__), FSA (`#568 <https://github.com/hpcugent/easybuild-easyconfigs/pull/568>`__), fqzcomp (`#1242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1242>`__), GAMESS-US (`#1153 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1153>`__, `#1406 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1406>`__), Grep (`#1308 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1308>`__), Hadoop (`#1418 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1418>`__), Hoard (`#1415 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1415>`__), IMB (`#1284 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1284>`__), ISL (`#1389 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1389>`__), jemalloc (`#1416 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1416>`__), libdwarf (`#1283 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1283>`__), libelf (`#1283 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1283>`__), MPC (`#1310 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1310>`__), multitail (`#1327 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1327>`__), Pmw (`#1403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1403>`__), Quip (`#1242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1242>`__), rCUDA (`#720 <https://github.com/hpcugent/easybuild-easyconfigs/pull/720>`__), SCALCE (`#1242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1242>`__), SMALT (`#568 <https://github.com/hpcugent/easybuild-easyconfigs/pull/568>`__), STREAM (`#1332 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1332>`__), worker (`#1307 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1307>`__), Xerces-C++ (`#1370 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1370>`__), XQilla (`#1370 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1370>`__), ZPAQ (`#1242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1242>`__)
* added easyconfigs for new (common) toolchains

  * ``foss/2015a`` (`#1239 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1239>`__), ``gompi/1.5.16`` (`#1380 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1380>`__), ``gmvolf/1.7.20`` (`#1397 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1397>`__), ``goolf/1.7.20`` (`#1294 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1294>`__), intel/2015a (`#1238 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1238>`__), ``intel/2015.02`` (`#1393 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1393>`__), ``iomkl/2015.01`` (`#1325 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1325>`__), ``iomkl/2015.02`` (`#1401 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1401>`__)
* added new software bundle: ``Autotools`` (`#1385 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1385>`__)
* various other enhancements, including:

  * don't define ``$LDSHARED`` in zlib easyconfigs (`#1350 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1350>`__)

    * this fixes the long-standing "``no version information available``" issue with zlib
    * see also `framework#108 <https://github.com/hpcugent/easybuild-framework/issues/108>`__
  * add unit test to check that all ``extra_options`` keys are defined in ``EasyConfig`` instance (`#1378 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1378>`__)
  * add source MD5 checksums in all GCC easyconfigs (`#1391 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1391>`__)
  * speeding up the unit tests by avoiding rereading of same easyconfig file (`#1432 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1432>`__)
  * fix conflict detection in unit tests by considering build deps separately from runtime deps (`#1447 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1447>`__)
  * fix toolchain for Bison build dep in ``MVAPICH2-1.9-iccifort-2011.13.367.eb`` easyconfig (`#1448 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1448>`__)
  * use ``Bundle`` generic easyblock for HPCBIOS bundles and fix ``moduleclass`` (`#1451 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1451>`__)
* various bug fixes, including:

  * revert version of Libint dependency to 1.1.4 in CP2K v2.5.1 easyconfig (`#1144 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1144>`__)
  * added Java dependencies to EMBOSS easyconfigs (`#1167 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1167>`__)
  * don't list '``lto``' as a language in GCC easyconfigs (`#1286 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1286>`__)

    * related to the fixes in the GCC easyblock, see `easyblocks#535 <https://github.com/hpcugent/easybuild-easyblocks/pull/535>`__
  * rename libint2 easyconfigs as Libint v2 easyconfigs (`#1287 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1287>`__)
  * fix mpi4py ``source_urls`` in Python easyconfigs (`#1306 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1306>`__)
  * consistently use CLooG 0.18.0 for GCC 4.8 series (`#1392 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1392>`__)
  * rename GenomeAnalysisTk easyconfigs to GATK (`#1399 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1399>`__)
  * include ``openssl-devel`` SLES11 OS dependency in cURL/MySQL/Python easyconfigs (`#1422 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1422>`__)
  * add missing Perl dependency in parallel easyconfigs (`#1430 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1430>`__)
  * correct name in BLAST+ easyconfigs (`#1443 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1443>`__)
  * fix name for sparsehash easyconfigs (`#1452 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1452>`__)


v1.16.2 (March 6th 2015)
------------------------

bugfix release

**framework**

`(no changes compared to v1.16.1, simple version bump to stay in sync with easybuild-easyblocks)`

**easyblocks**

* make ``EB_EasyBuildMeta`` easyblock aware of vsc-base to make upgrading to EasyBuild v2.0.0 possible (`#573 <https://github.com/hpcugent/easybuild-easyblocks/pull/573>`__)

**easyconfigs**

`(no changes compared to v1.16.1, simple version bump to stay in sync with easybuild-easyblocks)`

v1.16.1 (December 19th 2014)
----------------------------

bugfix release

**framework**

* fix functionality that is broken with ``--deprecated=2.0`` or with ``$EASYBUILD_DEPRECATED=2.0``

  * don't include easyconfig parameters for ``ConfigureMake`` in ``eb -a``, since fallback is deprecated (`#1123 <https://github.com/hpcugent/easybuild-framework/pull/1123>`__)
  * correctly check software_license value type (`#1124 <https://github.com/hpcugent/easybuild-framework/pull/1124>`__)
  * fix ``generate_software_list.py`` script w.r.t. deprecated fallback to ``ConfigureMake`` (`#1127 <https://github.com/hpcugent/easybuild-framework/pull/1127>`__)

* other bug fixes

  * fix logging issues in tests, sync with vsc-base v2.0.0 (`#1120 <https://github.com/hpcugent/easybuild-framework/pull/1120>`__)

**easyblocks**

* fix EasyBuild versions for which ``$EASYBUILD_DEPRECATED=1.0`` is set in EasyBuild sanity check (`#531 <https://github.com/hpcugent/easybuild-easyblocks/pull/531>`__)

**easyconfigs**

* set default easyblock to ConfigureMake in TEMPLATE.eb (`#1277 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1277>`__)

v1.16.0 (December 18th 2014)
----------------------------

feature + bugfix release

**framework**

* deprecate automagic fallback to ``ConfigureMake`` easyblock (`#1113 <https://github.com/hpcugent/easybuild-framework/pull/1113>`__)

  * easyconfigs should specify ``easyblock = 'ConfigureMake'`` instead of relying on the fallback mechanism
  * **note: automagic fallback to** ``ConfigureMake`` **easyblock will be removed in EasyBuild v2.0**
  * see also `Automagic fallback to ConfigureMake <http://easybuild.readthedocs.org/en/latest/Deprecated-functionality.html#configuremake-fallback>`__

* stop triggering deprecated functionality, to enable use of ``--deprecated=2.0`` (`#1107 <https://github.com/hpcugent/easybuild-framework/pull/1107>`__, `#1115 <https://github.com/hpcugent/easybuild-framework/pull/1115>`__, `#1119 <https://github.com/hpcugent/easybuild-framework/pull/1119>`__)

  * see `Deprecated functionality <http://easybuild.readthedocs.org/en/latest/Deprecated-functionality.html#configuremake-fallback>`__ for more information

* various other enhancements, including:

  * add script to clean up gists created via ``--upload-test-report`` (`#958 <https://github.com/hpcugent/easybuild-framework/pull/958>`__)
  * also use ``-xHost`` when using Intel compilers on AMD systems (as opposed to ``-msse3``) (`#960 <https://github.com/hpcugent/easybuild-framework/pull/960>`__)
  * add Python version check in ``eb`` command (`#1046 <https://github.com/hpcugent/easybuild-framework/pull/1046>`__)
  * take ``versionprefix`` into account in ``HierarchicalMNS`` module naming scheme (`#1058 <https://github.com/hpcugent/easybuild-framework/pull/1058>`__)
  * clean up and refactor ``main.py``, move functionality to other modules (`#1059 <https://github.com/hpcugent/easybuild-framework/pull/1059>`__, `#1064 <https://github.com/hpcugent/easybuild-framework/pull/1064>`__, `#1075 <https://github.com/hpcugent/easybuild-framework/pull/1075>`__, `#1087 <https://github.com/hpcugent/easybuild-framework/pull/1087>`__)
  * add check in ``download_file`` function for HTTP return code + show download progress report (`#1066 <https://github.com/hpcugent/easybuild-framework/pull/1066>`__, `#1090 <https://github.com/hpcugent/easybuild-framework/pull/1090>`__)
  * include info log message with name and location of used easyblock (`#1069 <https://github.com/hpcugent/easybuild-framework/pull/1069>`__)
  * add toolchains definitions for ``gpsmpi``, ``gpsolf``, ``impich``, ``intel-para``, ``ipsmpi`` toolchains (`#1072 <https://github.com/hpcugent/easybuild-framework/pull/1072>`__, `#1073 <https://github.com/hpcugent/easybuild-framework/pull/1073>`__)

    * support for Parastation MPI based toolchains

  * enforce that ``hiddendependencies`` is a subset of ``dependencies`` (`#1078 <https://github.com/hpcugent/easybuild-framework/pull/1078>`__)

    * this is done to avoid that site-specific policies w.r.t. hidden modules slip into contributed easyconfigs

  * enable use of ``--show_hidden`` for ``avail`` subcommand with recent Lmod versions (`#1081 <https://github.com/hpcugent/easybuild-framework/pull/1081>`__)
  * add ``--robot-paths`` configure option (`#1080 <https://github.com/hpcugent/easybuild-framework/pull/1080>`__, `#1093 <https://github.com/hpcugent/easybuild-framework/pull/1093>`__, `#1095 <https://github.com/hpcugent/easybuild-framework/pull/1095>`__,  `#1114 <https://github.com/hpcugent/easybuild-framework/pull/1114>`__)
  * support use of ``%(DEFAULT_ROBOT_PATHS)s`` template in EasyBuild configuration files (`#1100 <https://github.com/hpcugent/easybuild-framework/pull/1100>`__)

    * see also `Controlling the robot search path <http://easybuild.readthedocs.org/en/latest/Using_the_EasyBuild_command_line.html#controlling-the-robot-search-path>`__

  * use ``-xHost`` rather than ``-xHOST``, to match Intel documentation (`#1084 <https://github.com/hpcugent/easybuild-framework/pull/1084>`__)
  * update and cleanup ``README`` file (`#1085 <https://github.com/hpcugent/easybuild-framework/pull/1085>`__)
  * deprecate ``self.moduleGenerator`` in favor of ``self.module_generator`` in ``EasyBlock`` (`#1088 <https://github.com/hpcugent/easybuild-framework/pull/1088>`__)
  * also support ``MPICH`` MPI family in ``mpi_cmd_for`` function (`#1098 <https://github.com/hpcugent/easybuild-framework/pull/1098>`__)
  * update documentation references to point to http://easybuild.readthedocs.org (`#1102 <https://github.com/hpcugent/easybuild-framework/pull/1102>`__)
  * check for OS dependencies with *both* ``rpm`` and ``dpkg`` (if available) (`#1111 <https://github.com/hpcugent/easybuild-framework/pull/1111>`__)


* various bug fixes, including:

  * fix picking required software version specified by ``--software-version`` and clean up ``tweak.py`` (`#1062 <https://github.com/hpcugent/easybuild-framework/pull/1062>`__, `#1063 <https://github.com/hpcugent/easybuild-framework/pull/1063>`__)
  * escape ``$`` characters in module load message specified via ``modloadmsg`` easyconfig parameter) (`#1068 <https://github.com/hpcugent/easybuild-framework/pull/1068>`__)
  * take available hidden modules into account in dependency resolution (`#1065 <https://github.com/hpcugent/easybuild-framework/pull/1065>`__)
  * fix hard crash when using patch files with an empty list of sources (`#1070 <https://github.com/hpcugent/easybuild-framework/pull/1070>`__)
  * fix Intel MKL BLACS library being used for MPICH/MPICH2-based toolchains (`#1072 <https://github.com/hpcugent/easybuild-framework/pull/1072>`__)
  * fix regular expression in ``fetch_parameter_from_easyconfig_file`` function (`#1096 <https://github.com/hpcugent/easybuild-framework/pull/1096>`__)
  * don't hardcode queue names when submitting a job (`#1106 <https://github.com/hpcugent/easybuild-framework/pull/1106>`__)
  * fix affiliation/mail address for Fotis in headers (`#1105 <https://github.com/hpcugent/easybuild-framework/pull/1105>`__)
  * filter out ``/dev/null`` entries in patch file in ``det_patched_files`` function (`#1108 <https://github.com/hpcugent/easybuild-framework/pull/1108>`__)
  * fix ``gmpolf`` toolchain definition, to have ``gmpich`` as MPI components (instead of ``gmpich2``) (`#1101 <https://github.com/hpcugent/easybuild-framework/pull/1101>`__)

    * 'MPICH' refers to MPICH v3.x, while MPICH2 refers to MPICH(2) v2.x (MPICH v1.x is ancient/obsolete)
    * **note**: this requires to reinstall the ``gmpolf`` module, using the updated easyconfig from `easybuild-easyconfigs#1217 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1217>`__

**easyblocks**

* new easyblocks for **2** software packages that requires customized support:

  * Chimera (`#524 <https://github.com/hpcugent/easybuild-easyblocks/pull/524>`__), GATE (`#518 <https://github.com/hpcugent/easybuild-easyblocks/pull/518>`__)

* fix use of deprecated functionality, enhance unit tests to check for it (`#523 <https://github.com/hpcugent/easybuild-easyblocks/pull/523>`__)

* various other enhancements, including:

  * update PETSc easyblock for recent versions (v3.5) (`#446 <https://github.com/hpcugent/easybuild-easyblocks/pull/446>`__)
  * only include major/minor version numbers for FLUENT subdir (`#480 <https://github.com/hpcugent/easybuild-easyblocks/pull/480>`__)
  * factor out 'move after install' code from impi easyblock to ``IntelBase``, use it for itac (`#487 <https://github.com/hpcugent/easybuild-easyblocks/pull/487>`__)
  * support custom easyconfig parameters in ``EB_impi`` easyblock to correct behavior of MPI wrapper commands (`#493 <https://github.com/hpcugent/easybuild-easyblocks/pull/493>`__)
  * consider both ``lib`` and ``lib64`` in sanity check for GROMACS (`#501 <https://github.com/hpcugent/easybuild-easyblocks/pull/501>`__)
  * take ``preinstallopts`` and ``installopts`` into account in ``Binary`` easyblock (`#503 <https://github.com/hpcugent/easybuild-easyblocks/pull/503>`__)
  * add sanity check command ``abaqus information=all`` for ABAQUS (`#504 <https://github.com/hpcugent/easybuild-easyblocks/pull/504>`__)
  * update and clean up ``README``, refer to http://easybuild.readthedocs.org documentation (`#505 <https://github.com/hpcugent/easybuild-easyblocks/pull/505>`__, `#516 <https://github.com/hpcugent/easybuild-easyblocks/pull/516>`__)
  * rename deprecated ``self.moduleGenerator`` to ``self.module_generator`` (`#506 <https://github.com/hpcugent/easybuild-easyblocks/pull/506>`__)

    * see also `easybuild-framework#1088 <https://github.com/hpcugent/easybuild-easyblocks/pull/1088>`__

  * check whether specified ``type`` value is a known value (``psmp`` or ``popt``) in CP2K easyblock (`#509 <https://github.com/hpcugent/easybuild-easyblocks/pull/509>`__)
  * add support to ``SAMtools`` easyblock for installing recent versions (v1.x) (`#512 <https://github.com/hpcugent/easybuild-easyblocks/pull/512>`__)
  * fix version check + sanity check in Geant4 easyblock + style fixes (`#517 <https://github.com/hpcugent/easybuild-easyblocks/pull/517>`__)
  * added ``$root/modlib`` to ``$PYTHONPATH`` guesses in Modeller easyblock (`#525 <https://github.com/hpcugent/easybuild-easyblocks/pull/525>`__)
  * mark ``license`` custom easyconfig parameter as deprecated in ``IntelBase`` (`#527 <https://github.com/hpcugent/easybuild-easyblocks/pull/527>`__)

* various bug fixes, including:

  * fix Libxc version check in CP2K easyblock (`#478 <https://github.com/hpcugent/easybuild-easyblocks/pull/478>`__)
  * correctly specify ``mkl_libs`` when building *numpy* with GCC and imkl (`#485 <https://github.com/hpcugent/easybuild-easyblocks/pull/485>`__)
  * extend noqa for OpenFOAM-Extend in build_step (`#488 <https://github.com/hpcugent/easybuild-easyblocks/pull/488>`__, `#520 <https://github.com/hpcugent/easybuild-easyblocks/pull/520>`__)
  * correctly set ``$LD_LIBRARY_PATH``, ``$LIBRARY_PATH`` and ``$PKG_CONFIG_PATH`` for ``R`` (`#495 <https://github.com/hpcugent/easybuild-easyblocks/pull/495>`__)
  * fix default value for ``files_to_copy`` in ``MakeCp`` easyblock (`#500 <https://github.com/hpcugent/easybuild-easyblocks/pull/500>`__)
  * treat ``MPICH`` MPI family as MPICH v3.x instead of MPICH v1.x (`#519 <https://github.com/hpcugent/easybuild-easyblocks/pull/519>`__)

    * see also `easybuild-framework#1112 <https://github.com/hpcugent/easybuild-easyblocks/pull/1112>`__

  * fix affiliation/mail address for Fotis in headers (`#521 <https://github.com/hpcugent/easybuild-easyblocks/pull/521>`__)
  * clean up in ``extra_options`` methods, avoid casting return value to ``dict`` or returning via parent (`#528 <https://github.com/hpcugent/easybuild-easyblocks/pull/528>`__)

**easyconfigs**

* added example easyconfig files for **39** new software packages:

  * ANTs (`#1232 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1232>`__), BEOPS (`#1264 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1264>`__), Chhimera (`#1255 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1255>`__), ctffind (`#1249 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1249>`__), DBD-SQLite (`#1064 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1064>`__), DBD-mysql (`#1063 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1063>`__), DIALIGN-TX (`#668 <https://github.com/hpcugent/easybuild-easyconfigs/pull/668>`__), ffmpeg (`#1088 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1088>`__), GObject-Introspection (`#1079 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1079>`__), GTS (`#1079 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1079>`__), Graphviz (`#1079 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1079>`__), GraphViz2 (`#1079 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1079>`__), grace (`#1131 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1131>`__), HarfBuzz (`#1079 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1079>`__), HTSlib (`#1161 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1161>`__), GSSAPI (`#1048 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1048>`__), Kerberos_V5 (`#1048 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1048>`__), libevent (`#1063 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1063>`__), libXdmcp (`#1129 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1129>`__), libXft (`#1017 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1017>`__), libXinerama (`#1017 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1017>`__), libXrender (`#1017 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1017>`__), Maven (`#1094 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1094>`__), MySQL (`#1063 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1063>`__), Net-LibIDN (`#1060 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1060>`__), OpenCV (`#1088 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1088>`__), OpenMD (`#1105 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1105>`__), Qhull (`#1105 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1105>`__), Pango (`#1079 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1079>`__), psmpi (`#1245 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1245>`__, `#1246 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1246>`__), RELION (`#1017 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1017>`__), renderproto (`#1017 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1017>`__), rjags (`#1125 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1125>`__), runjags (`#1125 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1125>`__), SPRNG (`#1138 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1138>`__, `#1141 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1141>`__), xineramaproto (`#1017 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1017>`__), XML-Dumper (`#1061 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1061>`__), XML-Parser (`#1061 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1061>`__), XML-Twig (`#1061 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1061>`__)

* added easyconfigs for new toolchains

  * ``intel/2014.10`` & ``intel/2014.11`` (`#1219 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1219>`__), ``intel-para/2014.12`` (`#1246 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1246>`__), ``gpsolf/2014.12`` (`#1245 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1245>`__), ``iompi/6.6.4`` (`#1215 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1215>`__)

* include ``easyblock = 'ConfigureMake'`` in relevant easyconfigs to deal with deprecation of automagic fallback to ``ConfigureMake`` (`#1248 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1248>`__)

  * see also `easybuild-framework#1113 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1113>`__ and `Automagic fallback to ConfigureMake <http://easybuild.readthedocs.org/en/latest/Deprecated-functionality.html#configuremake-fallback>`__

* clean up use of deprecated functionality in existing easyconfigs (`#1252 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1252>`__, `#1259 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1259>`__)

  * stop using deprecated ``makeopts``, ``premakeopts`` and ``shared_lib_ext``
  * check for use of deprecated functionality in easyconfigs unit tests
  * see also http://easybuild.readthedocs.org/en/latest/Deprecated-functionality.html#easyconfig-parameters

* various other enhancements, including:

  * also build ``fftw3_threads`` libraries, and enhance sanity checks (`#1013 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1013>`__)
  * add unit test to verify specified ``sanity_check_paths`` (`#1119 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1119>`__)
  * update and clean up ``README``, refer to http://easybuild.readthedocs.org documentation (`#1184 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1184>`__, `#1224 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1224>`__)

* various bug fixes, including:

  * fix unit tests w.r.t. changes in framework (`#1146 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1146>`__)
  * remove unnecessary build dependencies for OpenMPI (`#1168 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1168>`__)
  * remove duplicate line in OpenMPI easyconfigs (`#1207 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1207>`__)
  * fix affiliation/mail address for Fotis in headers (`#1237 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1237>`__)
  * fix permissions of easyconfig files for consistency (`#1210 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1210>`__)
  * disable symbol lookup feature in cairo to fix build on SL6 (`#1241 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1241>`__)
  * fix easyconfig ``gmpolf`` toolchain w.r.t. MPICH software name (`#1217 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1217>`__)

    * see also `easybuild-framework#1112 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1112>`__

  * fix ``source_urls`` for WRF and WPS (`#1225 <h`ttps://github.com/hpcugent/easybuild-easyconfigs/pull/1225>`__)
  * fix and clean up GATE easyconfigs (`#1228 <h`ttps://github.com/hpcugent/easybuild-easyconfigs/pull/1228>`__)
  * fix broken CLHEP builds by including ``-gcc`` in ``$CXXFLAGS`` (`#1254 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1254>`__)
  * add patch to fix broken test in Go (`#1257 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1257>`__)
  * fix name of GMAP easyconfigs, should be GMAP-GSNAP (`#1268 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1268>`__)
  * fix easyconfig filenames, enhance unit test to check easyconfig filenames (`#1271 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1271>`__)


v1.15.2 (October 7th 2014)
--------------------------

bugfix release

**framework**

* fix ``$MODULEPATH`` extensions for Clang/CUDA, to make ``goolfc``/``cgoolf`` compatible with ``HierarchicalMNS`` (`#1050 <https://github.com/hpcugent/easybuild-framework/pull/1050>`__)
* include ``versionsuffix`` in module subdirectory with ``HierarchicalMNS`` (`#1050 <https://github.com/hpcugent/easybuild-framework/pull/1050>`__, `#1055 <https://github.com/hpcugent/easybuild-framework/pull/1055>`__)
* fix unit tests which were broken with bash patched for ShellShock bug (`#1051 <https://github.com/hpcugent/easybuild-framework/pull/1051>`__)
* add definition of gimpi toolchain, required to make gimkl toolchain compatible with ``HierarchicalMNS`` (`#1052 <https://github.com/hpcugent/easybuild-framework/pull/1052>`__)
* don't override ``COMPILER_MODULE_NAME`` obtained from ``ClangGCC`` in Clang-based toolchains (`#1053 <https://github.com/hpcugent/easybuild-framework/pull/1053>`__)
* fix wrong code in ``path_to_top_of_module_tree`` function (`#1054 <https://github.com/hpcugent/easybuild-framework/pull/1054>`__)

  * because of this, load statements for compilers were potentially included in higher-level modules under ``HierarchicalMNS``

**easyblocks**

* only disable sanitizer tests for recent Clang versions (`#481 <https://github.com/hpcugent/easybuild-easyblocks/pull/481>`__, `#482 <https://github.com/hpcugent/easybuild-easyblocks/pull/482>`__)
* pass down installopts to CUDA install command (`#483 <https://github.com/hpcugent/easybuild-easyblocks/pull/483>`__)

**easyconfigs**

* disable parallel build for slalib (`#968 <https://github.com/hpcugent/easybuild-easyconfigs/pull/968>`__)
* fix compatibility of goolfc with HierarchicalMNS by using GCC toolchain for installing CUDA (`#1106 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1106>`__, `#1115 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1115>`__)
* fix zlib OS dependency spec for Debian in Boost easyconfigs (`#1109 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1109>`__)
* fix compatibility of gimkl with HierarchicalMNS by using gimpi subtoolchain (`#1110 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1110>`__)
* make both GCC and Clang first-class members in Clang-based toolchains to fix compatibility with HierarchicalMNS (`#1113 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1113>`__)

v1.15.1 (September 23rd 2014)
-----------------------------

bugfix release

**framework**

* take into account that multiple modules may be extending ``$MODULEPATH`` with the same path, when determining path to top of module tree (see `#1047 <https://github.com/hpcugent/easybuild-framework/pull/1047>`__)

  * this bug caused a load statement for either ``icc`` or ``ifort`` to be included in higher-level modules installed with an Intel-based compiler toolchain, under the ``HierarchicalMNS`` module naming scheme

* make ``HierarchicalMNS`` module naming scheme compatible with ``cgoolf`` and ``goolfc`` toolchain (`#1049 <https://github.com/hpcugent/easybuild-framework/pull/1049>`__)
* add definition of ``iompi`` (sub)toolchain to make ``iomkl`` toolchain compatible with ``HierarchicalMNS`` (`#1049 <https://github.com/hpcugent/easybuild-framework/pull/1049>`__)

**easyblocks**

`(no changes compared to v1.15.0, simple version bump to stay in sync with easybuild-framework)`

**easyconfigs**

* minor bug fixes, including:

  * use SHLIB_EXT in GMP/MPFR easyconfigs (`#1090 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1090>`__)
  * fix TopHat homepage and source_urls since page moved (`#1092 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1092>`__)
  * make iomkl toolchain compatible with HierarchicalMNS (`#1099 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1099>`__)

v1.15.0 (September 12th 2014)
-----------------------------

feature + bugfix release

**framework**

* various other enhancements, including:

  * fetch extension sources in fetch_step to enhance ``--stop=fetch`` (`#978 <https://github.com/hpcugent/easybuild-framework/pull/978>`__)
  * add ``iimpi`` toolchain definition (`#993 <https://github.com/hpcugent/easybuild-framework/pull/993>`__)
  * prepend robot path with download location of files when ``--from-pr`` is used (`#995 <https://github.com/hpcugent/easybuild-framework/pull/995>`__)
  * add support for excluding module path extensions from generated modules (`#1003 <https://github.com/hpcugent/easybuild-framework/pull/1003>`__)

    * see ``include_modpath_extensions`` easyconfig parameter

  * add support for installing hidden modules and using them as dependencies (`#1009 <https://github.com/hpcugent/easybuild-framework/pull/1009>`__, `#1021 <https://github.com/hpcugent/easybuild-framework/pull/1021>`__, `#1023 <https://github.com/hpcugent/easybuild-framework/pull/1023>`__)

    * see ``--hidden`` and ``hiddendependencies`` easyconfig parameter

  * stop relying on ``conflict`` statement in module files to determine software name of toolchain components (`#1017 <https://github.com/hpcugent/easybuild-framework/pull/1017>`__, `#1037 <https://github.com/hpcugent/easybuild-framework/pull/1037>`__)

    * instead, the ``is_short_modname_for`` method defined by the module naming scheme implementation is queried

  * improve error message generated for a missing easyconfig file (`#1019 <https://github.com/hpcugent/easybuild-framework/pull/1019>`__)
  * include path where tweaked easyconfigs are placed in robot path (`#1032 <https://github.com/hpcugent/easybuild-framework/pull/1032>`__)
  * indicate forced builds in ``--dry-run`` output (`#1034 <https://github.com/hpcugent/easybuild-framework/pull/1034>`__)
  * fix interaction between ``--force`` and ``--try-toolchain --robot`` (`#1035 <https://github.com/hpcugent/easybuild-framework/pull/1035>`__)
  * add ``--software`` option, disable recursion for ``--try-software(-X)`` (`#1036 <https://github.com/hpcugent/easybuild-framework/pull/1036>`__)
* various bug fixes, including:
  * fix ``HierarchicalMNS`` crashing when MPI library is installed with a dummy toolchain (`#986 <https://github.com/hpcugent/easybuild-framework/pull/986>`__)
  * fix list of FFTW wrapper libraries for Intel MKL (`#987 <https://github.com/hpcugent/easybuild-framework/pull/987>`__)
  * fix stability of unit tests (`#988 <https://github.com/hpcugent/easybuild-framework/pull/988>`__, `#1027 <https://github.com/hpcugent/easybuild-framework/pull/1027>`__, `#1033 <https://github.com/hpcugent/easybuild-framework/pull/1033>`__)
  * make sure ``$SCALAPACK_INC_DIR`` (and ``$SCALAPACK_LIB_DIR``) are defined when using ``imkl`` (`#990 <https://github.com/hpcugent/easybuild-framework/pull/990>`__)
  * fix error message on missing FFTW wrapper libs (`#992 <https://github.com/hpcugent/easybuild-framework/pull/992>`__)
  * fix duplicate toolchain elements in ``--list-toolchains`` output (`#993 <https://github.com/hpcugent/easybuild-framework/pull/993>`__)
  * filter out load statements that extend the ``$MODULEPATH`` to make the module being installed available (`#1016 <https://github.com/hpcugent/easybuild-framework/pull/1016>`__)
  * fix conflict specification included in module files (`#1017 <https://github.com/hpcugent/easybuild-framework/pull/1017>`__)
  * avoid ``--from-pr`` crashing hard unless ``--robot`` is used (`#1022 <https://github.com/hpcugent/easybuild-framework/pull/1022>`__)
  * properly quote GCC version string in archived easyconfig (`#1028 <https://github.com/hpcugent/easybuild-framework/pull/1028>`__)
  * fix issue with ``--repositorypath`` not honoring ``--prefix`` (`#1031 <https://github.com/hpcugent/easybuild-framework/pull/1031>`__)
  * sync with latest vsc-base version to fix log order (`#1039 <https://github.com/hpcugent/easybuild-framework/pull/1039>`__)
  * increase # commits per page for ``--from-pr`` (`#1040 <https://github.com/hpcugent/easybuild-framework/pull/1040>`__)

**easyblocks**

* added support for **2** new software packages that requires customized support:

  * Modeller (`#392 <https://github.com/hpcugent/easybuild-easyblocks/pull/392>`__), NAMD (`#397 <https://github.com/hpcugent/easybuild-easyblocks/pull/397>`__)

* various enhancements, including:

  * fix locale used for running Perl unit tests (`#425 <https://github.com/hpcugent/easybuild-easyblocks/pull/425>`__)
  * fix Rmpi easyblock to correctly configure for Intel MPI (`#435 <https://github.com/hpcugent/easybuild-easyblocks/pull/435>`__)
  * add support in generic Rpackage easyblock for handling patches (`#435 <https://github.com/hpcugent/easybuild-easyblocks/pull/435>`__)
  * enhance OpenFOAM easyblock: fix building MPI build of Pstream and (pt)scotchDecomp + overall cleanup (`#436 <https://github.com/hpcugent/easybuild-easyblocks/pull/436>`__)
  * enhance NWChem easyblock for version 6.3, clean up running of test cases (`#441 <https://github.com/hpcugent/easybuild-easyblocks/pull/441>`__)
  * enhance noqa for interactive configuration of Qt build procedure (`#447 <https://github.com/hpcugent/easybuild-easyblocks/pull/447>`__)
  * add custom sanity check for R in easyblock (`#449 <https://github.com/hpcugent/easybuild-easyblocks/pull/449>`__)
  * make perlmodule take into account ``(pre){config,build,install}opts`` (`#450 <https://github.com/hpcugent/easybuild-easyblocks/pull/450>`__)
  * add support for specifying an activation key after installing Mathematica (`#452 <https://github.com/hpcugent/easybuild-easyblocks/pull/452>`__)
  * consider both ``lib`` and ``lib64`` directories in netCDF sanity check (`#453 <https://github.com/hpcugent/easybuild-easyblocks/pull/453>`__)
  * fix sanity check for ANSYS for v15.0.x (`#458 <https://github.com/hpcugent/easybuild-easyblocks/pull/458>`__)
  * fix Trilinos easyblock for recent version (`#462 <https://github.com/hpcugent/easybuild-easyblocks/pull/462>`__)
  * enhance impi easyblock to handle install subdir for impi v5.0.1 and future version (`#465 <https://github.com/hpcugent/easybuild-easyblocks/pull/465>`__, `#472 <https://github.com/hpcugent/easybuild-easyblocks/pull/472>`__)
  * include $CFLAGS in linker flags for HPL (`#466 <https://github.com/hpcugent/easybuild-easyblocks/pull/466>`__)
  * update sanity test checks for GROMACS 5.x (`#471 <https://github.com/hpcugent/easybuild-easyblocks/pull/471>`__)

* various bug fixes:

  * fix building of FFTW wrappers for Intel MKL v11.1.x + cleanup of imkl easyblock (`#445 <https://github.com/hpcugent/easybuild-easyblocks/pull/445>`__)

**easyconfigs**

* added example easyconfig files for **13** new software packages:

  * Circos (`#780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/780>`__), DB_File (`#913 <https://github.com/hpcugent/easybuild-easyconfigs/pull/913>`__), Emacs (`#970 <https://github.com/hpcugent/easybuild-easyconfigs/pull/970>`__), evmix (`#1077 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1077>`__), GD (`#780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/780>`__), gsl (`#1077 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1077>`__), IOR (`#949 <https://github.com/hpcugent/easybuild-easyconfigs/pull/949>`__), JAGS (`#1076 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1076>`__),
    libgd (`#780 <https://github.com/hpcugent/easybuild-easyconfigs/pull/780>`__), MethPipe (`#1070 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1070>`__), Modeller (`#825 <https://github.com/hpcugent/easybuild-easyconfigs/pull/825>`__), NAMD (`#835 <https://github.com/hpcugent/easybuild-easyconfigs/pull/835>`__), netCDF-C++4 (`#1015 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1015>`__)

* added easyconfigs for new toolchains (`#986 <https://github.com/hpcugent/easybuild-easyconfigs/pull/986>`__, `#1051 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1051>`__):

  * gimkl/1.5.9, ictce/7.1.2

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * including Python 2.7.8/3.4.1, Perl 5.20.0, R 3.1.1, NWChem 6.3, OpenFOAM-Extend 3.1, GCC 4.9.1, Clang 3.4.2, ...

* various enhancements, including:

  * make existing ictce/intel toolchains compatible with HierarchicalMNS (`#1069 <https://github.com/hpcugent/easybuild-easyconfigs/pull/1069>`__)

    * this involves installing impi with an iccifort toolchain, and imkl with an iimpi toolchain

* various bug fixes, including:

  * download link for Perl modules changed to use cpan.metapan.org
  * fix missing MPI-based OpenFOAM libraries (``Pstream``, ``(pt)scotchDecomp``), make sure provided SCOTCH is used (`#957 <https://github.com/hpcugent/easybuild-easyconfigs/pull/957>`__)

v1.14.0 (July 9th 2014)
-----------------------

feature + bugfix release

**framework**

* important changes

  * required Lmod version bumped to v5.6.3 (`#944 <https://github.com/hpcugent/easybuild-framework/pull/944>`__)

    * required due to enhancements and bug fixes in Lmod, e.g. making ``--terse avail`` significantly faster, and
      correctly handling a ``prepend-path`` statement that includes multiple directories at once

  * required Tcl/C environment modules version set to 3.2.10 (

    * hard requirement due to fixed ``modulecmd`` segmentation fault bug, that only tends manifests itself
      when making a large amount of changes in the environment (e.g. ``module load <toolchain>``)

  * renamed ``EasyBuildModuleNamingScheme`` to ``EasyBuildMNS``

* enhanced custom module naming schemes functionality to support hierarchical module naming schemes (`#953 <https://github.com/hpcugent/easybuild-framework/pull/953>`__, `#971 <https://github.com/hpcugent/easybuild-framework/pull/971>`__, `#975 <https://github.com/hpcugent/easybuild-framework/pull/975>`__)

  * extended API for custom module naming schemes to allow tweaking different aspects of module naming

    * see ``easybuild/tools/module_naming_scheme/mns.py`` for abstract ``ModuleNamingScheme`` class
    * an example hierarchical module naming scheme is included, see ``HierarchicalMNS``

  * split up full module names into a module subdirectory part, which becomes part of ``$MODULEPATH``),
    and a 'short' module name (is exposed to end-users)

    * example: ``GCC/4.7.2`` in ``Core`` subdir, ``OpenMPI/1.6.5`` in ``Compiler/GCC/4.7.2`` subdir

  * make ``ModuleNamingScheme`` class a singleton, move it into ``easybuild.tools.module_naming_scheme.mns`` module
  * implement ``ActiveMNS`` wrapper class for quering active module naming scheme
  * implement toolchain inspection functions that can be used in a custom module naming scheme

    * ``det_toolchain_compilers``, ``det_toolchain_mpi`` in ``easybuild.tools.module_naming_scheme.toolchain``

  * significant code cleanup & enhanced unit tests

* enhance & clean up ``tools/modules.py`` (`#944 <https://github.com/hpcugent/easybuild-framework/pull/944>`__, `#953 <https://github.com/hpcugent/easybuild-framework/pull/953>`__, `#963 <https://github.com/hpcugent/easybuild-framework/pull/963>`__, `#964 <https://github.com/hpcugent/easybuild-framework/pull/964>`__, `#969 <https://github.com/hpcugent/easybuild-framework/pull/969>`__)

  * make ``ModulesTool`` a singleton to avoid repeating module commands over & over again needlessly
  * use ``module use``, ``module unuse`` rather than fiddling with ``$MODULEPATH`` directly
  * improve debug logging (include full stdout/stderr output of module commands)
  * remove deprecated functionality (``add_module``, ``remove_module``, indirect module load)

* various other enhancements, including:

  * added toolchain definitions for 'common' toolchains: ``intel`` and ``foss`` (`#956 <https://github.com/hpcugent/easybuild-framework/pull/956>`__)
  * implement caching for easyconfig files, parsed easyconfigs and toolchains (`#953 <https://github.com/hpcugent/easybuild-framework/pull/953>`__)
  * enable ``--ignore-osdeps`` implicitely when ``-D``, ``--dry-run`` or ``--dep-graph`` are used (`#953 <https://github.com/hpcugent/easybuild-framework/pull/953>`__)
  * flesh out ``use_group`` and ``det_parallelism`` function, include them in ``easybuild.tools.systemtools`` (`#953 <https://github.com/hpcugent/easybuild-framework/pull/953>`__)
  * make symlinking of module files part of module naming scheme API (`#973 <https://github.com/hpcugent/easybuild-framework/pull/973>`__)

    * list of symlinks paths can be controlled using ``det_module_symlink_paths()`` method

  * added support for new configuration options:

    * tweaking compiler flags triggered by ``optarch`` toolchain options using ``--optarch`` (`#949 <https://github.com/hpcugent/easybuild-framework/pull/949>`__)
    * filtering out dependencies from easyconfig files using ``--filter-deps`` (`#957 <https://github.com/hpcugent/easybuild-framework/pull/957>`__)
    * filtering environment included in test reports with ``--test-report-env-filter`` (`#959 <https://github.com/hpcugent/easybuild-framework/pull/959>`__)
      e.g. ``--test-report-env-filter='^SSH|USER|HOSTNAME|UID|.*COOKIE.*'``
    * made suffix used for module files install path configurable, using ``--suffix-modules-path`` (`#973 <https://github.com/hpcugent/easybuild-framework/pull/973>`__)

  * added support for additional easyconfig parameters:
    * define aliases in module files (``modaliases``) (`#952 <https://github.com/hpcugent/easybuild-framework/pull/952>`__)
    * add print message on module load (``modloadmsg``) and Tcl footer (``modtclfooter``) in module files (`#954 <https://github.com/hpcugent/easybuild-framework/pull/954>`__, `#974 <https://github.com/hpcugent/easybuild-framework/pull/974>`__)

* various bug fixes, including:

  * don't try to tweak generated easyconfigs when using ``--try-X`` (`#942 <https://github.com/hpcugent/easybuild-framework/pull/942>`__)
  * currently create symlinks to module files modules/all under a custom module naming scheme (`#953 <https://github.com/hpcugent/easybuild-framework/pull/953>`__)
  * restore traceback error reporting on hard crashes (`#965 <https://github.com/hpcugent/easybuild-framework/pull/965>`__)

**easyblocks**

* added **one** new `generic` easyblock: CmdCp (`#395 <https://github.com/hpcugent/easybuild-easyblocks/pull/395>`__)
* added support for **2** new software packages that requires customized support:

  * ANSYS (`#398 <https://github.com/hpcugent/easybuild-easyblocks/pull/398>`__), HPCG (`#408 <https://github.com/hpcugent/easybuild-easyblocks/pull/408>`__)

* various enhancements, including:

  * updated ABAQUS easyblock so that it works for version 13.2 (`#406 <https://github.com/hpcugent/easybuild-easyblocks/pull/406>`__)
  * enhance BLAT easyblock by using ``super``'s ``build_step`` and ``prebuildopts``/``buildopts`` (`#423 <https://github.com/hpcugent/easybuild-easyblocks/pull/423>`__)
  * enhance Mothur easyblock to guess correct start dir for recent versions (`#424 <https://github.com/hpcugent/easybuild-easyblocks/pull/424>`__)
  * replace use of deprecated (pre)makeopts with (``pre``)``buildopts`` in all easyblocks (`#427 <https://github.com/hpcugent/easybuild-easyblocks/pull/427>`__)
  * fix poor mans version of toolchain compiler detection in imkl easyblock (`#429 <https://github.com/hpcugent/easybuild-easyblocks/pull/429>`__)

* various bug fixes:

  * only check for ``idb`` for older versions of icc (`#426 <https://github.com/hpcugent/easybuild-easyblocks/pull/426>`__)
  * fix issues with installing RPMS when ``rpmrebuild`` is required (`#433 <https://github.com/hpcugent/easybuild-easyblocks/pull/433>`__)
  * correctly disable parallel build for ATLAS (`#434 <https://github.com/hpcugent/easybuild-easyblocks/pull/434>`__)
  * fix sanity check for Intel MPI v5.x (only provides bin64) (`#432 <https://github.com/hpcugent/easybuild-easyblocks/pull/432>`__)
  * add ``$MIC_LD_LIBRARY_PATH`` for MKL v11.x (`#437 <https://github.com/hpcugent/easybuild-easyblocks/pull/437>`__)

**easyconfigs**

* added example easyconfig files for **17** new software packages:

  * ANSYS (`#836 <https://github.com/hpcugent/easybuild-easyconfigs/pull/836>`__), Beast (`#912 <https://github.com/hpcugent/easybuild-easyconfigs/pull/912>`__), ELPH (`#910 <https://github.com/hpcugent/easybuild-easyconfigs/pull/910>`__, `#911 <https://github.com/hpcugent/easybuild-easyconfigs/pull/911>`__), FastTree (`#900 <https://github.com/hpcugent/easybuild-easyconfigs/pull/900>`__, `#947 <https://github.com/hpcugent/easybuild-easyconfigs/pull/947>`__), GEM-library (`#858 <https://github.com/hpcugent/easybuild-easyconfigs/pull/858>`__), HPCG (`#853 <https://github.com/hpcugent/easybuild-easyconfigs/pull/853>`__),
    mdtest (`#925 <https://github.com/hpcugent/easybuild-easyconfigs/pull/925>`__), ncview (`#648 <https://github.com/hpcugent/easybuild-easyconfigs/pull/648>`__), PRANK (`#917 <https://github.com/hpcugent/easybuild-easyconfigs/pull/917>`__), RDP-Classifier (`#903 <https://github.com/hpcugent/easybuild-easyconfigs/pull/903>`__), SDPA (`#955 <https://github.com/hpcugent/easybuild-easyconfigs/pull/955>`__), SIBELia (`#886 <https://github.com/hpcugent/easybuild-easyconfigs/pull/886>`__),
    SOAPaligner (`#857 <https://github.com/hpcugent/easybuild-easyconfigs/pull/857>`__), SPAdes (`#884 <https://github.com/hpcugent/easybuild-easyconfigs/pull/884>`__), stemming (`#891 <https://github.com/hpcugent/easybuild-easyconfigs/pull/891>`__), WHAM (`#872 <https://github.com/hpcugent/easybuild-easyconfigs/pull/872>`__), YAXT (`#656 <https://github.com/hpcugent/easybuild-easyconfigs/pull/656>`__)

* added easyconfigs for new toolchains (`#935 <https://github.com/hpcugent/easybuild-easyconfigs/pull/935>`__, `#944 <https://github.com/hpcugent/easybuild-easyconfigs/pull/944>`__, `#948 <https://github.com/hpcugent/easybuild-easyconfigs/pull/948>`__):

  * foss/2014b, ictce/6.3.5, intel/2014b

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...
* various enhancements, including:

  * replace use of deprecated ``(pre)makeopts`` with ``(pre)buildopts`` in all easyblocks (`#954 <https://github.com/hpcugent/easybuild-easyconfigs/pull/954>`__)
  * disable running embossupdate on installation of EMBOSS (`#963 <https://github.com/hpcugent/easybuild-easyconfigs/pull/963>`__)
* various bug fixes, including:
  * really enable OpenMP support in FastTree easyconfigs (`#947 <https://github.com/hpcugent/easybuild-easyconfigs/pull/947>`__)
  * fix easyconfigs unit tests after changes in framework (`#958 <https://github.com/hpcugent/easybuild-easyconfigs/pull/958>`__)

v1.13.0 (May 29th 2014)
-----------------------

feature + bugfix release

**framework**

* make ``--try-X`` command line options work recursively (i.e. collaborate with ``--robot``) (`#922 <https://github.com/hpcugent/easybuild-framework/pull/922>`__)

  * EasyBuild will first build a full dependency graph of the specified easyconfigs, and then apply the ``--try`` specifications

    * the elements of the dependency graph for the used toolchain and its dependencies are left untouched

  * this makes ``eb foo-1.0-goolf-1.4.10.eb --try-toolchain=ictce,5.5.0 --robot`` also work when ``foo`` has dependencies
  * caveat: the specified easyconfig files must all use the same toolchain (version)

* add support for testing easyconfig pull requests from EasyBuild command line (`#920 <https://github.com/hpcugent/easybuild-framework/pull/920>`__, `#924 <https://github.com/hpcugent/easybuild-framework/pull/924>`__, `#925 <https://github.com/hpcugent/easybuild-framework/pull/925>`__, `#932 <https://github.com/hpcugent/easybuild-framework/pull/932>`__, `#933 <https://github.com/hpcugent/easybuild-framework/pull/933>`__, `#938 <https://github.com/hpcugent/easybuild-framework/pull/938>`__)

  * add ``--from-pr`` command line option for downloading easyconfig files from pull requests
  * add ``--upload-test-report`` command line option for uploading a detailed test report to GitHub as a gist

    * this requires specifying a GitHub username for which a GitHub token is available, using ``--github-user``
    * with ``--dump-test-report``, the test report can simply be dumped to file rather than being uploaded to GitHub
    * see also https://github.com/hpcugent/easybuild/wiki/Review-process-for-contributions#testing-result

* the ``makeopts`` and ``premakeopts`` easyconfig parameter are deprecated, and replaced by ``buildopts`` and ``prebuildopts`` (`#918 <https://github.com/hpcugent/easybuild-framework/pull/918>`__)

  * both ``makeopts`` and ``premakeopts`` will still be honored in future EasyBuild v1.x versions, but should no longer be used

* various other enhancements, including:

  * add ``--disable-cleanup-builddir`` command line option, to keep the build dir after a (successful) build (`#853 <https://github.com/hpcugent/easybuild-framework/pull/853>`__)

    * the build dir is still cleaned up by default for successful builds, i.e. ``--cleanup-builddir`` is the default

  * also consider lib32 in paths checked for ``$LD_LIBRARY_PATH`` and ``$LIBRARY_PATH`` (`#912 <https://github.com/hpcugent/easybuild-framework/pull/912>`__)
  * reorganize support for file/git/svn repositories into ``repository`` package, making it extensible (`#913 <https://github.com/hpcugent/easybuild-framework/pull/913>`__)
  * add support for ``postinstallcmds`` easyconfig parameter, to specify commands that need to be run after the install step (`#918 <https://github.com/hpcugent/easybuild-framework/pull/918>`__)
  * make ``VERSION=`` part in version of C environment modules tool optional, which is required for older versions (`#930 <https://github.com/hpcugent/easybuild-framework/pull/930>`__)
* various bug fixes, including:

  * fix small issues in bootstrap script: correctly determine EasyBuild version and make sure modules path exists (`#915 <https://github.com/hpcugent/easybuild-framework/pull/915>`__)
  * fix github unit tests (`#916 <https://github.com/hpcugent/easybuild-framework/pull/916>`__)
  * disable useless debug logging for unit tests (`#919 <https://github.com/hpcugent/easybuild-framework/pull/919>`__)
  * fix unit test for ``--skip`` (`#929 <https://github.com/hpcugent/easybuild-framework/pull/929>`__)
  * make sure ``start_dir`` can be set based on location of unpacked first source file (`#931 <https://github.com/hpcugent/easybuild-framework/pull/931>`__)
  * the ``vsc`` package shipped with easybuild-framework is synced with vsc-base v1.9.1 (`#935 <https://github.com/hpcugent/easybuild-framework/pull/935>`__)

    * fancylogger (used for logging in EasyBuild) is now robust against strings containing UTF8 characters
    * the ``deprecated`` logging function now does a non-strict version check (rather than an erroneous strict check)
    * the ``easybuild.tools.agithub`` module is removed, ``vsc.utils.rest`` now provides the required functionality

  * fix support for unpacking gzipped source files, don't unpack ``.gz`` files in-place in the source directory (`#936 <https://github.com/hpcugent/easybuild-framework/pull/936>`__)

**easyblocks**

* added support for **1** new software package that requires customized support:

  * Go (`#417 <https://github.com/hpcugent/easybuild-easyblocks/pull/417>`__)

* various enhancements, including:

  * enhance OpenFOAM easyblock so OpenFOAM-Extend fork can be built too + style fixes (`#253 <https://github.com/hpcugent/easybuild-easyblocks/pull/253>`__, `#416 <https://github.com/hpcugent/easybuild-easyblocks/pull/416>`__)
  * enhance CPLEX easyblock by adding support for staged installation (`#372 <https://github.com/hpcugent/easybuild-easyblocks/pull/372>`__)
  * include support for ``configure_cmd_prefix`` easyconfig parameter in ConfigureMake generic easyblock (`#393 <https://github.com/hpcugent/easybuild-easyblocks/pull/393>`__)
  * enhance GCC easyblock for building v4.9.0 and versions prior to v4.5 (`#396 <https://github.com/hpcugent/easybuild-easyblocks/pull/396>`__, `#400 <https://github.com/hpcugent/easybuild-easyblocks/pull/400>`__)
  * enhance easyblocks for Intel ipp and itac to support recent versions (`#399 <https://github.com/hpcugent/easybuild-easyblocks/pull/399>`__)
  * enhance Clang easyblock: install static analyzer (`#402 <https://github.com/hpcugent/easybuild-easyblocks/pull/402>`__), be more robust against changing source dir names (`#413 <https://github.com/hpcugent/easybuild-easyblocks/pull/413>`__)
  * enhance FoldX easyblock, update list of potential FoldX binaries to support recent versions (`#407 <https://github.com/hpcugent/easybuild-easyblocks/pull/407>`__)
  * add runtime patching in Boost easyblock to fix build issue with old Boost versions and recent glibc (> 2.15) (`#412 <https://github.com/hpcugent/easybuild-easyblocks/pull/412>`__)
  * enhance ``MakeCp`` generic easyblock: use location of 1st unpacked source as fallback base dir for ``files_to_copy`` (`#415 <https://github.com/hpcugent/easybuild-easyblocks/pull/415>`__)

* various bug fixes:

  * fix installing Mathematica when X forwarding is enabled (make sure ``$DISPLAY`` is unset) (`#391 <https://github.com/hpcugent/easybuild-easyblocks/pull/391>`__)
  * fix permissions of installed files in SAMtools easyblock, ensure read/execute for group/other (`#409 <https://github.com/hpcugent/easybuild-easyblocks/pull/409>`__)
  * fix implementation of ``det_pylibdir`` function in PythonPackage generic easyblock (`#419 <https://github.com/hpcugent/easybuild-easyblocks/pull/419>`__, `#420 <https://github.com/hpcugent/easybuild-easyblocks/pull/420>`__)

    * determine Python lib dir via ``distutils`` Python, which works cross-OS (as opposed to hardcoding ``lib``)

**easyconfigs**

* added example easyconfig files for **32** new software packages:

  * APBS (`#742 <https://github.com/hpcugent/easybuild-easyconfigs/pull/742>`__), BayesTraits (`#770 <https://github.com/hpcugent/easybuild-easyconfigs/pull/770>`__), bc (`#888 <https://github.com/hpcugent/easybuild-easyconfigs/pull/888>`__), BitSeq (`#791 <https://github.com/hpcugent/easybuild-easyconfigs/pull/791>`__), CEM (`#789 <https://github.com/hpcugent/easybuild-easyconfigs/pull/789>`__), CVS (`#888 <https://github.com/hpcugent/easybuild-easyconfigs/pull/888>`__), eXpress (`#786 <https://github.com/hpcugent/easybuild-easyconfigs/pull/786>`__), file (`#888 <https://github.com/hpcugent/easybuild-easyconfigs/pull/888>`__),
    GEMSTAT (`#861 <https://github.com/hpcugent/easybuild-easyconfigs/pull/861>`__), GMAP (`#594 <https://github.com/hpcugent/easybuild-easyconfigs/pull/594>`__), Go (`#887 <https://github.com/hpcugent/easybuild-easyconfigs/pull/887>`__), iscp (`#602 <https://github.com/hpcugent/easybuild-easyconfigs/pull/602>`__), IsoInfer (`#773 <https://github.com/hpcugent/easybuild-easyconfigs/pull/773>`__), Jellyfish (`#868 <https://github.com/hpcugent/easybuild-easyconfigs/pull/868>`__), less (`#888 <https://github.com/hpcugent/easybuild-easyconfigs/pull/888>`__),
    libcircle (`#883 <https://github.com/hpcugent/easybuild-easyconfigs/pull/883>`__), mcpp (`#602 <https://github.com/hpcugent/easybuild-easyconfigs/pull/602>`__), MMSEQ (`#795 <https://github.com/hpcugent/easybuild-easyconfigs/pull/795>`__), MUSTANG (`#800 <https://github.com/hpcugent/easybuild-easyconfigs/pull/800>`__), OpenFOAM-Extend (`#437 <https://github.com/hpcugent/easybuild-easyconfigs/pull/437>`__), popt (`#759 <https://github.com/hpcugent/easybuild-easyconfigs/pull/759>`__), pscom (`#759 <https://github.com/hpcugent/easybuild-easyconfigs/pull/759>`__),
    psmpi2 (`#759 <https://github.com/hpcugent/easybuild-easyconfigs/pull/759>`__), QuadProg++ (`#773 <https://github.com/hpcugent/easybuild-easyconfigs/pull/773>`__), rSeq (`#771 <https://github.com/hpcugent/easybuild-easyconfigs/pull/771>`__), RSEQtools (`#870 <https://github.com/hpcugent/easybuild-easyconfigs/pull/870>`__), Ruby (`#873 <https://github.com/hpcugent/easybuild-easyconfigs/pull/873>`__), segemehl (`#792 <https://github.com/hpcugent/easybuild-easyconfigs/pull/792>`__), SOAPec (`#879 <https://github.com/hpcugent/easybuild-easyconfigs/pull/879>`__),
    SOAPdenovo2 (`#874 <https://github.com/hpcugent/easybuild-easyconfigs/pull/874>`__), SRA-Toolkit (`#793 <https://github.com/hpcugent/easybuild-easyconfigs/pull/793>`__), texinfo (`#888 <https://github.com/hpcugent/easybuild-easyconfigs/pull/888>`__)

* added easyconfig for new toolchain goolfc/1.4.10
* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * e.g., older versions of Boost (1.47.0), GCC (4.1-4.4), & recent versions of Clang, GCC, Lmod, etc.

* various enhancements, including:

  * add OpenSSL dependency for cURL, to enable HTTPS support (`#881 <https://github.com/hpcugent/easybuild-easyconfigs/pull/881>`__)
  * also install esl-X binaries for HMMER (`#889 <https://github.com/hpcugent/easybuild-easyconfigs/pull/889>`__)

* various bug fixes, including:

  * properly pass down compiler flags for ParMGridGen (`#437 <https://github.com/hpcugent/easybuild-easyconfigs/pull/437>`__)
  * specify proper make options for PLINK, fixing the build on SL6 (`#594 <https://github.com/hpcugent/easybuild-easyconfigs/pull/594>`__, `#772 <https://github.com/hpcugent/easybuild-easyconfigs/pull/772>`__)
  * fix netloc version (0.5 rather than 0.5beta) (`#707 <https://github.com/hpcugent/easybuild-easyconfigs/pull/707>`__)
  * remove Windows-style line ending in netCDF patch file (`#796 <https://github.com/hpcugent/easybuild-easyconfigs/pull/796>`__)
  * bump version of OpenSSL dep for BOINC (`#882 <https://github.com/hpcugent/easybuild-easyconfigs/pull/882>`__)

v1.12.1 (April 25th 2014)
-------------------------

bugfix release

**framework**

* return to original directory after executing a command in a subdir (`#908 <https://github.com/hpcugent/easybuild-framework/pull/908>`__)
* fix bootstrap with Lmod, fix issue with module function check and Lmod (`#911 <https://github.com/hpcugent/easybuild-framework/pull/911>`__)

**easyblocks**

`(no changes compared to v1.12.0, simple version bump to stay in sync with easybuild-framework)`

**easyconfigs**

`(no changes compared to v1.12.0, simple version bump to stay in sync with easybuild-framework)`

v1.12.0 (April 4th 2014)
------------------------

feature + bugfix release

**framework**

* various enhancements, including:

  * completed support for custom module naming schemes (`#879 <https://github.com/hpcugent/easybuild-framework/pull/879>`__, `#904 <https://github.com/hpcugent/easybuild-framework/pull/904>`__)

    * a fully parsed easyconfig file is now passed to the ``det_full_module_name`` function
    * this does require that an easyconfig file matching the dependency specification is available

  * added more features to better support using a shared install target with multiple users (`#902 <https://github.com/hpcugent/easybuild-framework/pull/902>`__, `#903 <https://github.com/hpcugent/easybuild-framework/pull/903>`__, `#904 <https://github.com/hpcugent/easybuild-framework/pull/904>`__)
  * further development on support for new easyconfig format (v2.0) (`#844 <https://github.com/hpcugent/easybuild-framework/pull/844>`__, `#848 <https://github.com/hpcugent/easybuild-framework/pull/848>`__)

    * not considered stable yet, so still requires using ``--experimental``

  * enhanced bootstrap script to also support Lmod and ``modulecmd.tcl`` module tools (`#869 <https://github.com/hpcugent/easybuild-framework/pull/869>`__)
  * added support to ``run_cmd_qa`` function to supply a list of answers  (`#887 <https://github.com/hpcugent/easybuild-framework/pull/887>`__)
  * detect mismatch between definition of ``module`` function and selected modules tool (`#871 <https://github.com/hpcugent/easybuild-framework/pull/871>`__)

    * allowing mismatch now requires ``--allow-modules-tool-mismatch``; an empty ``module`` function is simply ignored

  * provide lib64 fallback option for directories in default sanity check paths (`#896 <https://github.com/hpcugent/easybuild-framework/pull/896>`__)
  * add support for adding JAR files to ``$CLASSPATH`` (`#898 <https://github.com/hpcugent/easybuild-framework/pull/898>`__)
  * enhanced and cleaned up unit tests (`#877 <https://github.com/hpcugent/easybuild-framework/pull/877>`__, `#880 <https://github.com/hpcugent/easybuild-framework/pull/880>`__, `#884 <https://github.com/hpcugent/easybuild-framework/pull/884>`__, `#899 <https://github.com/hpcugent/easybuild-framework/pull/899>`__, `#901 <https://github.com/hpcugent/easybuild-framework/pull/901>`__)
  * code cleanup and refactoring

    * get rid of global variable for configuration settings in ``config.py``, use singleton instead (`#874 <https://github.com/hpcugent/easybuild-framework/pull/874>`__, `#888 <https://github.com/hpcugent/easybuild-framework/pull/888>`__, `#890 <https://github.com/hpcugent/easybuild-framework/pull/890>`__, `#892 <https://github.com/hpcugent/easybuild-framework/pull/892>`__)
    * track build options via singleton in ``config.py`` rather than passing them around all over (`#886 <https://github.com/hpcugent/easybuild-framework/pull/886>`__, `#889 <https://github.com/hpcugent/easybuild-framework/pull/889>`__)
    * avoid parsing easyconfig files multiple times by passing a parsed easyconfig to the easyblock (`#891 <https://github.com/hpcugent/easybuild-framework/pull/891>`__)
    * deprecate list of tuples return type of ``extra_options`` static method (`#893 <https://github.com/hpcugent/easybuild-framework/pull/893>`__, `#894 <https://github.com/hpcugent/easybuild-framework/pull/894>`__)
    * move OS dependency check to ``systemtools.py`` module (`#895 <https://github.com/hpcugent/easybuild-framework/pull/895>`__)

* bug fixes, including:

  * fix linking with ``-lcudart`` if CUDA is part of the toolchain, should also include ``-lrt`` (`#882 <https://github.com/hpcugent/easybuild-framework/pull/882>`__)

**easyblocks**

* various enhancements, including:

  * also run ``Perl Build build`` for Perl modules (usually not required, but sometimes it is) (`#380 <https://github.com/hpcugent/easybuild-easyblocks/pull/380>`__)
  * added glob support in generic makecp block (`#367 <https://github.com/hpcugent/easybuild-easyblocks/pull/367>`__, `#384 <https://github.com/hpcugent/easybuild-easyblocks/pull/384>`__)
  * enhance sanity check in GCC easyblock such that it also passes/works on OpenSuSE (`#365 <https://github.com/hpcugent/easybuild-easyblocks/pull/365>`__)
  * add multilib support in GCC easyblock (`#379 <https://github.com/hpcugent/easybuild-easyblocks/pull/379>`__)
* various bug fixes:
  * Clang: disable sanitizer tests when vmem limit is set (`#366 <https://github.com/hpcugent/easybuild-easyblocks/pull/366>`__)
  * make sure all libraries are installed for recent Intel MKL versions (`#375 <https://github.com/hpcugent/easybuild-easyblocks/pull/375>`__)
  * fix appending Intel MPI include directories to ``$CPATH`` (`#371 <https://github.com/hpcugent/easybuild-easyblocks/pull/371>`__)
  * statically link readline/ncurses libraries in Python and NWChem easyblocks (`#370 <https://github.com/hpcugent/easybuild-easyblocks/pull/370>`__, `#383 <https://github.com/hpcugent/easybuild-easyblocks/pull/383>`__, `#385 <https://github.com/hpcugent/easybuild-easyblocks/pull/385>`__)
  * fix easyblock unit tests after changes in framework (`#376 <https://github.com/hpcugent/easybuild-easyblocks/pull/376>`__, `#377 <https://github.com/hpcugent/easybuild-easyblocks/pull/377>`__, `#378 <https://github.com/hpcugent/easybuild-easyblocks/pull/378>`__)

**easyconfigs**

* added example easyconfig files for **6** new software packages:

  * CLooG (`#653 <https://github.com/hpcugent/easybuild-easyconfigs/pull/653>`__), ELPA (`#738 <https://github.com/hpcugent/easybuild-easyconfigs/pull/738>`__), LIBSVM (`#788 <https://github.com/hpcugent/easybuild-easyconfigs/pull/788>`__), netaddr (`#753 <https://github.com/hpcugent/easybuild-easyconfigs/pull/753>`__), netifcas (`#753 <https://github.com/hpcugent/easybuild-easyconfigs/pull/753>`__), slalib-c (`#750 <https://github.com/hpcugent/easybuild-easyconfigs/pull/750>`__)

* added easyconfigs for new toolchains:

  * ClangGCC/1.3.0 (`#653 <https://github.com/hpcugent/easybuild-easyconfigs/pull/653>`__), goolf/1.4.10-no-OFED (`#749 <https://github.com/hpcugent/easybuild-easyconfigs/pull/749>`__), goolf/1.5.14(-no-OFED) (`#764 <https://github.com/hpcugent/easybuild-easyconfigs/pull/764>`__, `#767 <https://github.com/hpcugent/easybuild-easyconfigs/pull/767>`__), ictce/6.2.5 (`#726 <https://github.com/hpcugent/easybuild-easyconfigs/pull/726>`__), iomkl (`#747 <https://github.com/hpcugent/easybuild-easyconfigs/pull/747>`__)

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...
* various enhancements, including:

  * tweak BOINC easyconfig to make use of ``glob`` support available for ``files_to_copy`` (`#781 <https://github.com/hpcugent/easybuild-easyconfigs/pull/781>`__)
  * enable ``-fPIC`` for libreadline, so it can be linked into shared libs (e.g. ``libpython2.x.so``) (`#798 <https://github.com/hpcugent/easybuild-easyconfigs/pull/798>`__)
* various bug fixes, including:
  * fix Qt source_urls (`#756 <https://github.com/hpcugent/easybuild-easyconfigs/pull/756>`__)
  * enable ``-fPIC`` in ncurses 5.9 ictce/5.2.0 easyconfig, just like in the others (`#801 <https://github.com/hpcugent/easybuild-easyconfigs/pull/801>`__)
  * fix unit tests after changes to framework (`#763 <https://github.com/hpcugent/easybuild-easyconfigs/pull/763>`__, `#766 <https://github.com/hpcugent/easybuild-easyconfigs/pull/766>`__, `#769 <https://github.com/hpcugent/easybuild-easyconfigs/pull/769>`__)

v1.11.1 (February 28th 2014)
----------------------------

bugfix release

**framework**

* various bug fixes, including:

  * fix hard crash when ``$LMOD_CMD`` specified full path to lmod binary, but ``spider`` binary is not in ``$PATH`` (`#861 <https://github.com/hpcugent/easybuild-framework/pull/861>`__, `#873 <https://github.com/hpcugent/easybuild-framework/pull/873>`__)
  * fix bug in initialisation of repositories, causing problems when a repository subdirectory is specified (`#852 <https://github.com/hpcugent/easybuild-framework/pull/852>`__)
  * avoid long wait when dependency resolution fails if ``--robot`` is not specified (`#875 <https://github.com/hpcugent/easybuild-framework/pull/875>`__)

**easyblocks**

`(no changes compared to v1.11.0, simple version bump to stay in sync with easybuild-framework)`

**easyconfigs**

`(no changes compared to v1.11.0, simple version bump to stay in sync with easybuild-framework)`

v1.11.0 (February 16th 2014)
----------------------------

feature + bugfix release

**framework**

* various enhancements, including:

  * add checksum support for extensions (`#807 <https://github.com/hpcugent/easybuild-framework/pull/807>`__)
  * make checksum functionality more memory efficient by reading in blocks (`#836 <https://github.com/hpcugent/easybuild-framework/pull/836>`__)
  * rewrite of dependency solving for speed and better reporting of missing dependencies (`#806 <https://github.com/hpcugent/easybuild-framework/pull/806>`__, `#818 <https://github.com/hpcugent/easybuild-framework/pull/818>`__)
  * refactoring of ``main.py`` (`#815 <https://github.com/hpcugent/easybuild-framework/pull/815>`__, `#828 <https://github.com/hpcugent/easybuild-framework/pull/828>`__)

    * function/method signatures to pass down build options
    * move functions from main.py into easybuild.framework.X or easybuild.tools

  * provide better build statistics (`#824 <https://github.com/hpcugent/easybuild-framework/pull/824>`__)
  * add --experimental, ``--deprecated`` and ``--oldstyleconfig`` command line options (`#838 <https://github.com/hpcugent/easybuild-framework/pull/838>`__)

    * with ``--experimental``, new but incomplete (or partially broken) features are enabled
    * with ``--deprecated``, removed of deprecated functionality can be tested (anything deprecated will fail hard)
    * with ``--disable-oldstyleconfig``, support for the old style configuration is disabled

  * define ``$LIBRARY_PATH`` in generated module files (`#832 <https://github.com/hpcugent/easybuild-framework/pull/832>`__)
  * more constants for source URLs (e.g. for downloads from bitbucket) (`#831 <https://github.com/hpcugent/easybuild-framework/pull/831>`__)
  * prefer ``$XDG_CONFIG_HOME`` and ``~/.config/easybuild`` over ``~/.easybuild`` for configuration files (`#820 <https://github.com/hpcugent/easybuild-framework/pull/820>`__)
  * add support for specifying footers to be appended to generated module files (`#808 <https://github.com/hpcugent/easybuild-framework/pull/808>`__)

    * see ``--modules-footer`` command line option

  * track version of modules tool + cleanup of ``modules.py`` (`#839 <https://github.com/hpcugent/easybuild-framework/pull/839>`__)
  * move actual ``run_cmd`` and ``run_cmd_qa`` implementations from ``tools.filetools`` into ``tools.run`` (`#842 <https://github.com/hpcugent/easybuild-framework/pull/842>`__, `#843 <https://github.com/hpcugent/easybuild-framework/pull/843>`__)
  * add support for generating modules that support recursive unloading (`#830 <https://github.com/hpcugent/easybuild-framework/pull/830>`__)

    * see ``--recursive-module-unload`` command line option

  * add flexibility support for specifying OS dependencies (`#846 <https://github.com/hpcugent/easybuild-framework/pull/846>`__)

    * alternatives can be specified, e.g. (``openssl-devel``, ``libssl-dev``)

  * initial (incomplete) support for easyconfig files in new format (v2.0) (`#810 <https://github.com/hpcugent/easybuild-framework/pull/810>`__, `#826 <https://github.com/hpcugent/easybuild-framework/pull/826>`__, `#827 <https://github.com/hpcugent/easybuild-framework/pull/827>`__, `#841 <https://github.com/hpcugent/easybuild-framework/pull/841>`__)

    * requires ``--experimental`` to be able to experiment with format v2 easyconfig files

* various bug fixes, including:

  * fix problems with use of new-style configuration file (`#821 <https://github.com/hpcugent/easybuild-framework/pull/821>`__)
  * fix removal of old build directories, unless ``cleanupoldbuild`` easyconfig parameter is set (`#809 <https://github.com/hpcugent/easybuild-framework/pull/809>`__)
  * fix support for different types of repository path specifications (`#814 <https://github.com/hpcugent/easybuild-framework/pull/814>`__)
  * fix unit tests sensitive to ``$MODULEPATH`` and available easyblocks (`#845 <https://github.com/hpcugent/easybuild-framework/pull/845>`__)

**easyblocks**

* added **one** new `generic` easyblock: ``VSCPythonPackage`` (`#348 <https://github.com/hpcugent/easybuild-easyblocks/pull/348>`__)
* added support for **1** new software package that requires customized support:

  * netcdf4-python (`#347 <https://github.com/hpcugent/easybuild-easyblocks/pull/347>`__)

* various enhancements, including:

  * add support for installing recent tbb versions (`#341 <https://github.com/hpcugent/easybuild-easyblocks/pull/341>`__)
  * use ``makeopts`` in the build step of the generic ``PythonPackage`` easyblock (`#352 <https://github.com/hpcugent/easybuild-easyblocks/pull/352>`__)
  * define the ``$CMAKE_INCLUDE_PATH`` and ``$CMAKE_LIBRARY_PATH`` in the generic ``CMakeMake`` easyblock (`#351 <https://github.com/hpcugent/easybuild-easyblocks/pull/351>`__, `#360 <https://github.com/hpcugent/easybuild-easyblocks/pull/360>`__)
  * update Clang easyblock to support v3.4 (`#346 <https://github.com/hpcugent/easybuild-easyblocks/pull/346>`__)
  * make sure Python is built with SSL support, adjust Python easyblock to pick up OpenSSL dep (`#359 <https://github.com/hpcugent/easybuild-easyblocks/pull/359>`__)

    * note: providing OpenSSL via an OS package is still recommended, such that security updates are picked up

  * add support for recent netCDF versions (`#347 <https://github.com/hpcugent/easybuild-easyblocks/pull/347>`__)
  * update SuiteSparse easyblock for new versions, and clean it up a bit (`#350 <https://github.com/hpcugent/easybuild-easyblocks/pull/350>`__)

* various bug fixes:

  * fix name of ``VersionIndependentPythonPackage`` easyblock, deprecate ``VersionIndependendPythonPackage`` easyblock (`#348 <https://github.com/hpcugent/easybuild-easyblocks/pull/348>`__)
  * fix detection of machine architecture in FSL easyblock (`#353 <https://github.com/hpcugent/easybuild-easyblocks/pull/353>`__)
  * fix bug in NWChem easyblock w.r.t. creating local dummy ``.nwchem`` file (`#360 <https://github.com/hpcugent/easybuild-easyblocks/pull/360>`__)
  * make sure ``$LIBRARY_PATH`` is set for Intel compilers and Intel MPI, fix 64-bit specific paths (`#360 <https://github.com/hpcugent/easybuild-easyblocks/pull/360>`__)

**easyconfigs**

* added example easyconfig files for **30** new software packages:

  * argtable (`#669 <https://github.com/hpcugent/easybuild-easyconfigs/pull/669>`__), Clustal-Omega (`#669 <https://github.com/hpcugent/easybuild-easyconfigs/pull/669>`__), Coreutils (`#582 <https://github.com/hpcugent/easybuild-easyconfigs/pull/582>`__), GMT (`#560 <https://github.com/hpcugent/easybuild-easyconfigs/pull/560>`__), gperftools (`#596 <https://github.com/hpcugent/easybuild-easyconfigs/pull/596>`__), grep (`#582 <https://github.com/hpcugent/easybuild-easyconfigs/pull/582>`__), h4toh5 (`#597 <https://github.com/hpcugent/easybuild-easyconfigs/pull/597>`__),
    libunwind (`#596 <https://github.com/hpcugent/easybuild-easyconfigs/pull/596>`__), Lmod (`#600 <https://github.com/hpcugent/easybuild-easyconfigs/pull/600>`__, `#692 <https://github.com/hpcugent/easybuild-easyconfigs/pull/692>`__), Lua (`#600 <https://github.com/hpcugent/easybuild-easyconfigs/pull/600>`__, `#692 <https://github.com/hpcugent/easybuild-easyconfigs/pull/692>`__), MAFFT (`#654 <https://github.com/hpcugent/easybuild-easyconfigs/pull/654>`__), Molekel (`#597 <https://github.com/hpcugent/easybuild-easyconfigs/pull/597>`__), NEdit (`#597 <https://github.com/hpcugent/easybuild-easyconfigs/pull/597>`__),
    netcdf4-python (`#660 <https://github.com/hpcugent/easybuild-easyconfigs/pull/660>`__), nodejs (`#678 <https://github.com/hpcugent/easybuild-easyconfigs/pull/678>`__), OCaml (`#704 <https://github.com/hpcugent/easybuild-easyconfigs/pull/704>`__), patch (`#582 <https://github.com/hpcugent/easybuild-easyconfigs/pull/582>`__), PhyML (`#664 <https://github.com/hpcugent/easybuild-easyconfigs/pull/664>`__),
    PRACE Common Production Environment (`#599 <https://github.com/hpcugent/easybuild-easyconfigs/pull/599>`__), protobuf (`#680 <https://github.com/hpcugent/easybuild-easyconfigs/pull/680>`__), python-dateutil (`#438 <https://github.com/hpcugent/easybuild-easyconfigs/pull/438>`__), sed (`#582 <https://github.com/hpcugent/easybuild-easyconfigs/pull/582>`__), sickle (`#651 <https://github.com/hpcugent/easybuild-easyconfigs/pull/651>`__),
    Tesla-Deployment-Kit (`#489 <https://github.com/hpcugent/easybuild-easyconfigs/pull/489>`__), TREE-PUZZLE (`#662 <https://github.com/hpcugent/easybuild-easyconfigs/pull/662>`__), VCFtools (`#626 <https://github.com/hpcugent/easybuild-easyconfigs/pull/626>`__), Vim (`#665 <https://github.com/hpcugent/easybuild-easyconfigs/pull/665>`__), vsc-mympirun-scoop (`#661 <https://github.com/hpcugent/easybuild-easyconfigs/pull/661>`__),
    vsc-processcontrol (`#661 <https://github.com/hpcugent/easybuild-easyconfigs/pull/661>`__), XZ (`#582 <https://github.com/hpcugent/easybuild-easyconfigs/pull/582>`__)

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * OpenSSL with ictce toolchain (`#703 <https://github.com/hpcugent/easybuild-easyconfigs/pull/703>`__)

* various enhancements, including:

  * using more constants and templates (`#613 <https://github.com/hpcugent/easybuild-easyconfigs/pull/613>`__, `#615 <https://github.com/hpcugent/easybuild-easyconfigs/pull/615>`__)
  * specify OS dependency for SSL support, with OpenSSL dependency as fallback (`#703 <https://github.com/hpcugent/easybuild-easyconfigs/pull/703>`__)

* various bug fixes, including:

  * fix unit tests after (internal) framework API changes (`#667 <https://github.com/hpcugent/easybuild-easyconfigs/pull/667>`__, `#672 <https://github.com/hpcugent/easybuild-easyconfigs/pull/672>`__)
  * fix homepage in vsc-mympirun easyconfig file (`#681 <https://github.com/hpcugent/easybuild-easyconfigs/pull/681>`__)
  * align OpenMPI easyconfigs (`#650 <https://github.com/hpcugent/easybuild-easyconfigs/pull/650>`__)
  * add additional source URL in Qt easyconfigs (`#676 <https://github.com/hpcugent/easybuild-easyconfigs/pull/676>`__)
  * specify correct $PATH specification and define ``$CHPL_HOME`` for Chapel (`#683 <https://github.com/hpcugent/easybuild-easyconfigs/pull/683>`__)

v1.10.0 (December 24th 2013)
----------------------------

feature + bugfix release

**framework**

* various enhancements, including:

  * set unique default temporary directory, add ``--tmpdir`` command line option (`#695 <https://github.com/hpcugent/easybuild-framework/pull/695>`__)
  * add support for computing and verifying source/patch file checksums (`#774 <https://github.com/hpcugent/easybuild-framework/pull/774>`__, `#777 <https://github.com/hpcugent/easybuild-framework/pull/777>`__, `#779 <https://github.com/hpcugent/easybuild-framework/pull/779>`__, `#801 <https://github.com/hpcugent/easybuild-framework/pull/801>`__, `#802 <https://github.com/hpcugent/easybuild-framework/pull/802>`__)

    * cfr. ``checksums`` easyconfig parameter

  * add support for `eb --confighelp`, which prints out an example configuration file (`#775 <https://github.com/hpcugent/easybuild-framework/pull/775>`__)
  * add initial support for ``eb`` tab completion in bash shells (`#775 <https://github.com/hpcugent/easybuild-framework/pull/775>`__, `#797 <https://github.com/hpcugent/easybuild-framework/pull/797>`__, `#798 <https://github.com/hpcugent/easybuild-framework/pull/798>`__)

    * see also https://github.com/hpcugent/easybuild/wiki/Setting-up-tab-completion-for-bash
    * note: may be quite slow for now

  * enhancements for using Lmod as modules tool (`#780 <https://github.com/hpcugent/easybuild-framework/pull/780>`__, `#795 <https://github.com/hpcugent/easybuild-framework/pull/795>`__, `#796 <https://github.com/hpcugent/easybuild-framework/pull/796>`__):

    * ignore Lmod spider cache by setting ``$LMOD_IGNORE_CACHE`` (requires Lmod 5.2)
    * bump required Lmod version to v5.2
    * get rid of slow workaround for detecting module directories (only required for older Lmod versions)
    * fix version parsing for Lmod release candidates (rc)
    * improve integration with `lmod spider` by adding ``Description: `` prefix to ``module-whatis`` field of module

  * add ``--dry-short-short``/``-D`` and ``--search-short``/``-S`` command line options (`#781 <https://github.com/hpcugent/easybuild-framework/pull/781>`__)
  * add toolchain definition for 'gompic', intended for using with CUDA-aware OpenMPI (`#783 <https://github.com/hpcugent/easybuild-framework/pull/783>`__)
  * add support for specifying multiple robot paths (`#786 <https://github.com/hpcugent/easybuild-framework/pull/786>`__)
  * add various source URL constants, add support for ``%(nameletter)s`` and ``%(nameletterlower)s`` templates (`#793 <https://github.com/hpcugent/easybuild-framework/pull/793>`__)
  * add ``buildininstalldir`` easyconfig parameter (`#794 <https://github.com/hpcugent/easybuild-framework/pull/794>`__)
  * add ``--ignore-osdeps`` command line option (`#799 <https://github.com/hpcugent/easybuild-framework/pull/799>`__, `#802 <https://github.com/hpcugent/easybuild-framework/pull/802>`__)

* various bug fixes, including:

  * enable ``-mt_mpi`` compiler flag if both ``usempi`` and ``openmp`` toolchain options are enabled (`#771 <https://github.com/hpcugent/easybuild-framework/pull/771>`__)
  * only use ``libmkl_solver*`` libraries for Intel MKL versions prior to 10.3 (`#776 <https://github.com/hpcugent/easybuild-framework/pull/776>`__)
  * fix toolchain support for recent Intel tools (`#785 <https://github.com/hpcugent/easybuild-framework/pull/785>`__)
  * code style fixes in ``main.py`` to adhere more to PEP8 (`#789 <https://github.com/hpcugent/easybuild-framework/pull/789>`__)
  * make sure ``easyblock`` easyconfig parameter is listed in ``eb -a`` (`#791 <https://github.com/hpcugent/easybuild-framework/pull/791>`__)
  * fix error that may pop up when using ``skipsteps=source`` (`#792 <https://github.com/hpcugent/easybuild-framework/pull/792>`__)

**easyblocks**

* added **one** new `generic` easyblock: ``VersionIndependendPythonPackage`` (`#329 <https://github.com/hpcugent/easybuild-easyblocks/pull/329>`__, `#334 <https://github.com/hpcugent/easybuild-easyblocks/pull/334>`__)
* added support for **2** new software packages that require customized support:

  * Charmm (`#318 <https://github.com/hpcugent/easybuild-easyblocks/pull/318>`__), GROMACS (`#335 <https://github.com/hpcugent/easybuild-easyblocks/pull/335>`__, `#339 <https://github.com/hpcugent/easybuild-easyblocks/pull/339>`__)

* various enhancements, including:

  * fix support for recent SAMtools version (>= 0.1.19) (`#320 <https://github.com/hpcugent/easybuild-easyblocks/pull/320>`__)
  * fix support for recent Intel tools (icc, ifort, imkl, impi) (`#325 <https://github.com/hpcugent/easybuild-easyblocks/pull/325>`__, `#327 <https://github.com/hpcugent/easybuild-easyblocks/pull/327>`__, `#338 <https://github.com/hpcugent/easybuild-easyblocks/pull/338>`__)
  * enhance generic easyblock for installing RPMs (`#332 <https://github.com/hpcugent/easybuild-easyblocks/pull/332>`__)
  * pick up ``preinstallopts`` in generic ``PythonPackage`` easyblock (`#334 <https://github.com/hpcugent/easybuild-easyblocks/pull/334>`__)
  * enhance CP2K easyblock (libxc support, new versions) + style cleanup (`#336 <https://github.com/hpcugent/easybuild-easyblocks/pull/336>`__)

* various bug fixes:

  * use unwanted env var functionality to unset ``$MKLROOT`` rather than failing with an error (`#273 <https://github.com/hpcugent/easybuild-easyblocks/pull/273>`__)
  * always include ``-w`` flag for preprocessor to supress warnings that may break QuantumESPRESSO configure (`#317 <https://github.com/hpcugent/easybuild-easyblocks/pull/317>`__)
  * link with multithreaded LAPACK libs for ESMF (`#319 <https://github.com/hpcugent/easybuild-easyblocks/pull/319>`__)
  * extend ``noqanda`` list of patterns in CUDA easyblock (`#328 <https://github.com/hpcugent/easybuild-easyblocks/pull/328>`__, `#337 <https://github.com/hpcugent/easybuild-easyblocks/pull/337>`__)
  * add ``import _ctypes`` to Python sanity check commands to capture a common build issue (`#329 <https://github.com/hpcugent/easybuild-easyblocks/pull/329>`__)
  * bug fixes in generic ``IntelBase`` easyblock (`#331 <https://github.com/hpcugent/easybuild-easyblocks/pull/331>`__, `#333 <https://github.com/hpcugent/easybuild-easyblocks/pull/333>`__, `#335 <https://github.com/hpcugent/easybuild-easyblocks/pull/335>`__)

    * remove broken symlink ``$HOME/intel`` if present
    * fix use of gettempdir to obtain a common (user-specific) tmp dir to symlink ``$HOME/intel`` to

  * fix build of recent scipy versions with GCC-based toolchain (`#334 <https://github.com/hpcugent/easybuild-easyblocks/pull/334>`__)
  * fix use of gettempdir to obtain common (user-specific) tmp dir for ``$HOME/.nwchemrc`` symlink (`#340 <https://github.com/hpcugent/easybuild-easyblocks/pull/340>`__, `#342 <https://github.com/hpcugent/easybuild-easyblocks/pull/342>`__)
  * extend ``noqanda`` list in Qt easyblock (`#342 <https://github.com/hpcugent/easybuild-easyblocks/pull/342>`__)

**easyconfigs**

* added example easyconfig files for **18** new software packages:

  * BEDTools (`#579 <https://github.com/hpcugent/easybuild-easyconfigs/pull/579>`__, `#632 <https://github.com/hpcugent/easybuild-easyconfigs/pull/632>`__, `#635 <https://github.com/hpcugent/easybuild-easyconfigs/pull/635>`__), CAP3 (`#548 <https://github.com/hpcugent/easybuild-easyconfigs/pull/548>`__), CHARMM (`#584 <https://github.com/hpcugent/easybuild-easyconfigs/pull/584>`__), cutadapt (`#620 <https://github.com/hpcugent/easybuild-easyconfigs/pull/620>`__), ErlangOTP (`#556 <https://github.com/hpcugent/easybuild-easyconfigs/pull/556>`__, `#630 <https://github.com/hpcugent/easybuild-easyconfigs/pull/630>`__),
    Ghostscript (`#547 <https://github.com/hpcugent/easybuild-easyconfigs/pull/547>`__, `#632 <https://github.com/hpcugent/easybuild-easyconfigs/pull/632>`__), HTSeq (`#554 <https://github.com/hpcugent/easybuild-easyconfigs/pull/554>`__, `#632 <https://github.com/hpcugent/easybuild-easyconfigs/pull/632>`__), Jansson (`#545 <https://github.com/hpcugent/easybuild-easyconfigs/pull/545>`__), libjpeg-turbo (`#574 <https://github.com/hpcugent/easybuild-easyconfigs/pull/574>`__), Molden (`#566 <https://github.com/hpcugent/easybuild-easyconfigs/pull/566>`__),
    netloc (`#545 <https://github.com/hpcugent/easybuild-easyconfigs/pull/545>`__), o2scl (`#633 <https://github.com/hpcugent/easybuild-easyconfigs/pull/633>`__), packmol (`#566 <https://github.com/hpcugent/easybuild-easyconfigs/pull/566>`__), PP (`#405 <https://github.com/hpcugent/easybuild-easyconfigs/pull/405>`__), qtop (`#500 <https://github.com/hpcugent/easybuild-easyconfigs/pull/500>`__), TAMkin (`#566 <https://github.com/hpcugent/easybuild-easyconfigs/pull/566>`__), vsc-base (`#621 <https://github.com/hpcugent/easybuild-easyconfigs/pull/621>`__),
    vsc-mympirun (`#621 <https://github.com/hpcugent/easybuild-easyconfigs/pull/621>`__)

* added easyconfigs for new toolchains (`#545 <https://github.com/hpcugent/easybuild-easyconfigs/pull/545>`__, `#609 <https://github.com/hpcugent/easybuild-easyconfigs/pull/609>`__, `#629 <https://github.com/hpcugent/easybuild-easyconfigs/pull/629>`__):

  * gcccuda/2.6.10, gompic/2.6.10, goolfc/2.6.10, ictce/6.0.5, ictce/6.1.5

* added additional easyconfigs for various supported software packages: version updates, different toolchains, ...

  * new versions of icc, ifort, imkl, impi (`#609 <https://github.com/hpcugent/easybuild-easyconfigs/pull/609>`__, `#629 <https://github.com/hpcugent/easybuild-easyconfigs/pull/629>`__)
  * large collection of ictce/5.3.0 easyconfigs (`#627 <https://github.com/hpcugent/easybuild-easyconfigs/pull/627>`__)

* various enhancements, including:

  * extended list of Python packages as extensions to Python (`#625 <https://github.com/hpcugent/easybuild-easyconfigs/pull/625>`__)
  * add MPI-enabled version of GROMACS + easyconfigs using ictce (`#606 <https://github.com/hpcugent/easybuild-easyconfigs/pull/606>`__, `#636 <https://github.com/hpcugent/easybuild-easyconfigs/pull/636>`__)
  * clean up templating of ``source_urls`` (`#637 <https://github.com/hpcugent/easybuild-easyconfigs/pull/637>`__)

* various bug fixes, including:

  * provide alternative download URL for Mesa (`#532 <https://github.com/hpcugent/easybuild-easyconfigs/pull/532>`__)
  * add Python versionsuffix in OpenBabel filenames (`#566 <https://github.com/hpcugent/easybuild-easyconfigs/pull/566>`__)
  * apply no-gets patch in all M4 v1.4.16 easyconfigs (`#623 <https://github.com/hpcugent/easybuild-easyconfigs/pull/623>`__)
  * fix patching of Python w.r.t. ``libffi``/``_ctypes`` issues (`#625 <https://github.com/hpcugent/easybuild-easyconfigs/pull/625>`__, `#642 <https://github.com/hpcugent/easybuild-easyconfigs/pull/642>`__)
  * bug fixes in GROMACS easyconfigs (`#606 <https://github.com/hpcugent/easybuild-easyconfigs/pull/606>`__)

    * change versionsuffix for non-MPI GROMACS easyconfigs to ``-mt``
    * stop using 'CMakeMake' easyblock for GROMACS now that there's a dedicated GROMACS easyblock,
      which correctly specifies building against external BLAS/LAPACK libraries

  * fix Qt dependency for CGAL (`#642 <https://github.com/hpcugent/easybuild-easyconfigs/pull/642>`__)
  * fix libctl, libmatheval, Meep, PSI build issues caused by full paths in ``guile-config``/``python-config`` shebang (`#642 <https://github.com/hpcugent/easybuild-easyconfigs/pull/642>`__)
  * make sure HDF easyconfigs specify dedicated ``include/hdf`` include dir (`#642 <https://github.com/hpcugent/easybuild-easyconfigs/pull/642>`__)

    * this is required to avoid build issues with NCL, because HDF ships it's own ``netcdf.h``
    * this also triggered removal of patch files for NCL that rewrote ``include/hdf`` to ``include``

  * fix WPS v3.5.1 patch file after upstream source tarball was changed, supply checksum for verification (`#642 <https://github.com/hpcugent/easybuild-easyconfigs/pull/642>`__)

v1.9.0 (November 17th 2013)
---------------------------

feature + bugfix release

**framework**

* add support for Tcl environment modules (``modulecmd.tcl``) (`#728 <https://github.com/hpcugent/easybuild-framework/pull/728>`__, `#729 <https://github.com/hpcugent/easybuild-framework/pull/729>`__, `#739 <https://github.com/hpcugent/easybuild-framework/pull/739>`__)

  * special care was taken to make sure also the DEISA variant of ``modulecmd.tcl`` can be used

* code refactoring to prepare for supporting two formats for easyconfig files (`#693 <https://github.com/hpcugent/easybuild-framework/pull/693>`__, `#750 <https://github.com/hpcugent/easybuild-framework/pull/750>`__)

  * this prepares the codebase for supporting easyconfig format v2.0
  * some initial work on adding support for the new easyconfig format is included, but it's by no means complete yet
  * the current easyconfig format (now dubbed v1.0) is still the default and only supported format, for now
  * for more details, see https://github.com/hpcugent/easybuild/wiki/Easyconfig-format-two

* various other enhancements, including:

  * include a full version of vsc-base (see the ``vsc`` subdirectory) (`#740 <https://github.com/hpcugent/easybuild-framework/pull/740>`__)

    * this is a first step towards switching to using vsc-base as a proper dependency

  * implement get_avail_core_count function in systemtools module that takes cpusets and co into account (`#700 <https://github.com/hpcugent/easybuild-framework/pull/700>`__)

    * the ``get_core_count`` function is now deprecated

  * add ``impmkl`` toolchain definition (`#736 <https://github.com/hpcugent/easybuild-framework/pull/736>`__)
  * make regtest more robust: put holds on jobs without dependencies, release holds once all jobs are submitted (`#751 <https://github.com/hpcugent/easybuild-framework/pull/751>`__)
  * add support for specifying multiple alternatives for sanity check paths (`#753 <https://github.com/hpcugent/easybuild-framework/pull/753>`__)
  * add ``get_software_libdir`` function to modules.py (along with unit tests) (`#758 <https://github.com/hpcugent/easybuild-framework/pull/758>`__)
  * add support for more file extensions and constants w.r.t. sources (`#738 <https://github.com/hpcugent/easybuild-framework/pull/738>`__, `#760 <https://github.com/hpcugent/easybuild-framework/pull/760>`__, `#761 <https://github.com/hpcugent/easybuild-framework/pull/761>`__)
  * add MPICH2 support in ``mpi_cmd_for`` function (`#761 <https://github.com/hpcugent/easybuild-framework/pull/761>`__)

* various bug fixes, including:

  * fix checking of OS dependencies on Debian/Ubuntu that have ``rpm`` command available (`#732 <https://github.com/hpcugent/easybuild-framework/pull/732>`__)
  * make unit tests more robust w.r.t. non-writeable ``/tmp`` and loaded modules prior to starting unit tests (`#752 <https://github.com/hpcugent/easybuild-framework/pull/752>`__, `#756 <https://github.com/hpcugent/easybuild-framework/pull/756>`__)
  * also call ``EasyBlock``'s sanity check in ``ExtensionEasyblock`` if paths/commands are specified in easyconfig (`#757 <https://github.com/hpcugent/easybuild-framework/pull/757>`__)
  * set compiler family for dummy compiler, add definition of toolchain constant for dummy (`#759 <https://github.com/hpcugent/easybuild-framework/pull/759>`__)

* other

  * add build status badges for master/develop branches to ``README`` (`#742 <https://github.com/hpcugent/easybuild-framework/pull/742>`__)
  * add scripts for installing EasyBuild develop version or setting up git development environment (`#730 <https://github.com/hpcugent/easybuild-framework/pull/730>`__, `#755 <https://github.com/hpcugent/easybuild-framework/pull/755>`__)

**easyblocks**

* added support for **8** new software packages that require customized support:

  * Allinea DDT/MAP (`#279 <https://github.com/hpcugent/easybuild-easyblocks/pull/279>`__), ARB (`#291 <https://github.com/hpcugent/easybuild-easyblocks/pull/291>`__), GenomeAnalysisTK (`#278 <https://github.com/hpcugent/easybuild-easyblocks/pull/278>`__), OpenBabel (`#305 <https://github.com/hpcugent/easybuild-easyblocks/pull/305>`__, `#309 <https://github.com/hpcugent/easybuild-easyblocks/pull/309>`__), picard (`#278 <https://github.com/hpcugent/easybuild-easyblocks/pull/278>`__), PyQuante (`#297 <https://github.com/hpcugent/easybuild-easyblocks/pull/297>`__), Scalasca v1.x (`#304 <https://github.com/hpcugent/easybuild-easyblocks/pull/304>`__), Score-P (`#304 <https://github.com/hpcugent/easybuild-easyblocks/pull/304>`__)

    * the Score-P easyblock is also used for Cube 4.x, LWM2, OTF2, and Scalasca v2.x

* various enhancements, including:

  * add support building ScaLAPACK on top of MPICH2, required for gmpolf toolchain (`#274 <https://github.com/hpcugent/easybuild-easyblocks/pull/274>`__)
  * add support to ConfigureMake easyblock to customize configure ``--prefix`` option (`#287 <https://github.com/hpcugent/easybuild-easyblocks/pull/287>`__)
  * add support for specifying install command in Binary easyblock (`#288 <https://github.com/hpcugent/easybuild-easyblocks/pull/288>`__)
  * enhance CMakeMake easyblock to specify srcdir via easyconfig parameter, and to perform out-of-source builds (`#303 <https://github.com/hpcugent/easybuild-easyblocks/pull/303>`__)

* various bug fixes:

  * use correct configure flag for Szip in HDF5 easyblocks, should be ``--with-szlib`` (`#286 <https://github.com/hpcugent/easybuild-easyblocks/pull/286>`__, `#301 <https://github.com/hpcugent/easybuild-easyblocks/pull/301>`__)
  * add support for serial HDF5 builds (`#290 <https://github.com/hpcugent/easybuild-easyblocks/pull/290>`__, `#301 <https://github.com/hpcugent/easybuild-easyblocks/pull/301>`__)
  * enhance robustness of Qt easyblock w.r.t. interactive configure (`#295 <https://github.com/hpcugent/easybuild-easyblocks/pull/295>`__, `#302 <https://github.com/hpcugent/easybuild-easyblocks/pull/302>`__)
  * enhance support for picking up license specification via environment variables (`#298 <https://github.com/hpcugent/easybuild-easyblocks/pull/298>`__, `#307 <https://github.com/hpcugent/easybuild-easyblocks/pull/307>`__)
  * extend list of values for ``$CPATH`` in libint2 easyblock (`#300 <https://github.com/hpcugent/easybuild-easyblocks/pull/300>`__)
  * fix ``extra_options`` ``super`` call in Clang easyblock (`#306 <https://github.com/hpcugent/easybuild-easyblocks/pull/306>`__)
  * add support in Boost easyblock to specify toolset in easyconfig file (`#308 <https://github.com/hpcugent/easybuild-easyblocks/pull/308>`__)

* other:

  * add build status badges for master/develop branches to README (`#289 <https://github.com/hpcugent/easybuild-easyblocks/pull/289>`__)

**easyconfigs**

* added example easyconfig files for **58** new software packages:

  *  Allinea (`#468 <https://github.com/hpcugent/easybuild-easyconfigs/pull/468>`__), ARB + dependencies (`#396 <https://github.com/hpcugent/easybuild-easyconfigs/pull/396>`__, `#493 <https://github.com/hpcugent/easybuild-easyconfigs/pull/493>`__, `#495 <https://github.com/hpcugent/easybuild-easyconfigs/pull/495>`__), arpack-ng (`#451 <https://github.com/hpcugent/easybuild-easyconfigs/pull/451>`__, `#481 <https://github.com/hpcugent/easybuild-easyconfigs/pull/481>`__), CDO (`#484 <https://github.com/hpcugent/easybuild-easyconfigs/pull/484>`__, `#521 <https://github.com/hpcugent/easybuild-easyconfigs/pull/521>`__), Cube (`#505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/505>`__), ed (`#503 <https://github.com/hpcugent/easybuild-easyconfigs/pull/503>`__), FLTK (`#503 <https://github.com/hpcugent/easybuild-easyconfigs/pull/503>`__), GenomeAnalysisTK (`#467 <https://github.com/hpcugent/easybuild-easyconfigs/pull/467>`__), GIMPS (`#527 <https://github.com/hpcugent/easybuild-easyconfigs/pull/527>`__), GTI (`#511 <https://github.com/hpcugent/easybuild-easyconfigs/pull/511>`__), IPython (`#485 <https://github.com/hpcugent/easybuild-easyconfigs/pull/485>`__, `#519 <https://github.com/hpcugent/easybuild-easyconfigs/pull/519>`__), LWM2 (`#510 <https://github.com/hpcugent/easybuild-easyconfigs/pull/510>`__), MPICH2 (`#460 <https://github.com/hpcugent/easybuild-easyconfigs/pull/460>`__), MUST (`#511 <https://github.com/hpcugent/easybuild-easyconfigs/pull/511>`__), ncdf (`#496 <https://github.com/hpcugent/easybuild-easyconfigs/pull/496>`__, `#522 <https://github.com/hpcugent/easybuild-easyconfigs/pull/522>`__), OPARI2 (`#505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/505>`__), OpenBabel (`#504 <https://github.com/hpcugent/easybuild-easyconfigs/pull/504>`__, `#524 <https://github.com/hpcugent/easybuild-easyconfigs/pull/524>`__), OTF (`#505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/505>`__), OTF2 (`#505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/505>`__), PandaSEQ (`#475 <https://github.com/hpcugent/easybuild-easyconfigs/pull/475>`__), ParaView (`#498 <https://github.com/hpcugent/easybuild-easyconfigs/pull/498>`__, `#514 <https://github.com/hpcugent/easybuild-easyconfigs/pull/514>`__), ParFlow (`#483 <https://github.com/hpcugent/easybuild-easyconfigs/pull/483>`__, `#520 <https://github.com/hpcugent/easybuild-easyconfigs/pull/520>`__), PCC (`#486 <https://github.com/hpcugent/easybuild-easyconfigs/pull/486>`__, `#528 <https://github.com/hpcugent/easybuild-easyconfigs/pull/528>`__), PDT (`#505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/505>`__), picard (`#467 <https://github.com/hpcugent/easybuild-easyconfigs/pull/467>`__), PnMPI (`#511 <https://github.com/hpcugent/easybuild-easyconfigs/pull/511>`__), PyQuante (`#499 <https://github.com/hpcugent/easybuild-easyconfigs/pull/499>`__, `#523 <https://github.com/hpcugent/easybuild-easyconfigs/pull/523>`__), pysqlite (`#519 <https://github.com/hpcugent/easybuild-easyconfigs/pull/519>`__), Scalasca (`#505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/505>`__), Score-P (`#505 <https://github.com/hpcugent/easybuild-easyconfigs/pull/505>`__), SDCC (`#486 <https://github.com/hpcugent/easybuild-easyconfigs/pull/486>`__, `#528 <https://github.com/hpcugent/easybuild-easyconfigs/pull/528>`__), Silo (`#483 <https://github.com/hpcugent/easybuild-easyconfigs/pull/483>`__, `#520 <https://github.com/hpcugent/easybuild-easyconfigs/pull/520>`__), Stride (`#503 <https://github.com/hpcugent/easybuild-easyconfigs/pull/503>`__), SURF (`#503 <https://github.com/hpcugent/easybuild-easyconfigs/pull/503>`__), TCC (`#486 <https://github.com/hpcugent/easybuild-easyconfigs/pull/486>`__, `#528 <https://github.com/hpcugent/easybuild-easyconfigs/pull/528>`__)

  * ARB dependencies (23): fixesproto, imake, inputproto, kbproto, libICE, libSM, libX11, libXau, libXaw, libXext, libXfixes, libXi, libXmu, libXp, libXpm, libXt, lynx, motif, printproto, Sablotron, xbitmaps, xextproto, xtrans

* added easyconfigs for new gmpich2/1.4.8, gmpolf/1.4.8 and goolf/1.6.10 toolchains (`#460 <https://github.com/hpcugent/easybuild-easyconfigs/pull/460>`__, `#525 <https://github.com/hpcugent/easybuild-easyconfigs/pull/525>`__, `#530 <https://github.com/hpcugent/easybuild-easyconfigs/pull/530>`__)

* added additional easyconfigs for various software packages (list too long to include here)

  * version updates, different toolchains, ...

* various bug fixes, including:

  * enable building of shared libraries for MPICH (`#482 <https://github.com/hpcugent/easybuild-easyconfigs/pull/482>`__)
  * fix HDF configure option for Szip, should be ``--with-szlib`` (`#533 <https://github.com/hpcugent/easybuild-easyconfigs/pull/533>`__)

    * for HDF5, this issue is fixed in the HDF5 easyblock

* other

  * add build status badges for master/develop branches to README (`#490 <https://github.com/hpcugent/easybuild-easyconfigs/pull/490>`__)

v1.8.2 (October 18th 2013)
--------------------------

bugfix release

**framework**

* fix regular expression used for obtaining list of modules from ``module avail`` (`#724 <https://github.com/hpcugent/easybuild-framework/pull/724>`__)

  * modules marked as default were being hidden from EasyBuild, causing problems when they are used as dependency

**easyblocks**

* fix installing of EasyBuild with a loaded EasyBuild module (`#280 <https://github.com/hpcugent/easybuild-easyblocks/pull/280>`__)

  * this is important to make upgrading to the latest EasyBuild version possible with a bootstrapped EasyBuild

**easyconfigs**

* port thread pool patch to PSI 4.0b4 and include it to avoid hanging tests (`#471 <https://github.com/hpcugent/easybuild-easyconfigs/pull/471>`__)

v1.8.1 (October 14th 2013)
--------------------------

bugfix release

* various bug fixes, including:

  * fix bugs in regtest procedure (`#713 <https://github.com/hpcugent/easybuild-framework/pull/713>`__)

    * force 2nd and 3rd attempt of build in case 1st attempt failed

  * fix copying of install log to install directory (`#716 <https://github.com/hpcugent/easybuild-framework/pull/716>`__)
  * only create first source path if multiple paths are specified (`#718 <https://github.com/hpcugent/easybuild-framework/pull/718>`__)
  * detect failed PBS job submission by checking obtained job ID for ``None`` value (`#713 <https://github.com/hpcugent/easybuild-framework/pull/713>`__, `#717 <https://github.com/hpcugent/easybuild-framework/pull/717>`__, `#719 <https://github.com/hpcugent/easybuild-framework/pull/719>`__, `#720 <https://github.com/hpcugent/easybuild-framework/pull/720>`__)

**easyblocks**

* various bug fixes:

  * fix problems in PSI easyblock causing build to fail (`#270 <https://github.com/hpcugent/easybuild-easyblocks/pull/270>`__)
  * fix issues with running NWChem test cases, fail early in case broken symlink is present (`#275 <https://github.com/hpcugent/easybuild-easyblocks/pull/275>`__)

**easyconfigs**

* added additional easyconfigs for various software packages (`#457 <https://github.com/hpcugent/easybuild-easyconfigs/pull/457>`__):

  * Boost, bzip2, libreadline, ncurses, PSI, Python, zlib

* various bug fixes, including:

  * fix faulty easyconfig file names for HPCBIOS_Math, MUSCLE, XML-LibXML and YAML-Syck (`#459 <https://github.com/hpcugent/easybuild-easyconfigs/pull/459>`__, `#462 <https://github.com/hpcugent/easybuild-easyconfigs/pull/462>`__)
  * stop (re)specifying default maximum ratio for failed tests in NWChem easyconfig (`#457 <https://github.com/hpcugent/easybuild-easyconfigs/pull/457>`__)

v1.8.0 (October 4th 2013)
-------------------------

feature + bugfix release

**framework**

* add support for using alternative module naming schemes (`#679 <https://github.com/hpcugent/easybuild-framework/pull/679>`__, `#696 <https://github.com/hpcugent/easybuild-framework/pull/696>`__, `#705 <https://github.com/hpcugent/easybuild-framework/pull/705>`__, `#706 <https://github.com/hpcugent/easybuild-framework/pull/706>`__, `#707 <https://github.com/hpcugent/easybuild-framework/pull/707>`__)

  * see https://github.com/hpcugent/easybuild/wiki/Using-a-custom-module-naming-scheme for documentation
  * module naming scheme classes that derive from the 'abstract' ``ModuleNamingScheme`` class can be provided to EasyBuild

    * the Python module providing the class must be available in the ``easybuild.tools.module_naming_scheme`` namespace
    * a function named ``det_full_module_name`` must be implemented, that determines the module name in the form of an string based on the supplied dictionary(-like) argument

  * the active module naming scheme is determined by EasyBuild configuration option ``--module-naming-scheme``
  * for now, only the ``name``/``version``/``versionsuffix``/``toolchain`` easyconfig parameters are guaranteed to be provided

    * consistently providing all easyconfig parameters (i.e., also for dependencies) requires more work (see `#687 <https://github.com/hpcugent/easybuild-framework/pull/687>`__)

  * implementing this involved a number of intrusive changes:

    * the API of the modules.py module needed to be changed, breaking backward compatibility

      * the function for which the signatures were modified are considered to be internal to the framework,
        so this should have very minor impact w.r.t. easyblocks not included with EasyBuild
      * affected functions include: ``available``, ``exists``, ``show``, ``modulefile_path``, ``dependencies_for``

    * the format for specifying dependencies was extended, to allow for specifying a custom toolchain

      * this allows to fix inaccurate dependency specifications,
        for example: ``('OpenMPI', '1.6.4-GCC-4.7.2')" to "('OpenMPI', '1.6.4', '', ('GCC', '4.7.2'))``
      * see also `easyconfigs#431 <https://github.com/hpcugent/easybuild-easyconfigs/pull/431>`__

    * the recommended version for Lmod was bumped to v5.1.5

      * using earlier 5.x version still works, but may be very slow when 'available' is used, due to bugs and a missing
        feature in Lmod versions prior to v5.1.5 on which we rely

* various other enhancements, including:

  * only (try to) change group id if it is different from what is wanted (`#685 <https://github.com/hpcugent/easybuild-framework/pull/685>`__)
  * added toy build unit test (`#688 <https://github.com/hpcugent/easybuild-framework/pull/688>`__)
  * support for specifying a list of source paths in EasyBuild configuration (`#690 <https://github.com/hpcugent/easybuild-framework/pull/690>`__, `#702 <https://github.com/hpcugent/easybuild-framework/pull/702>`__)
  * add function to determine CPU clock speed in ``systemtools.py`` (`#694 <https://github.com/hpcugent/easybuild-framework/pull/694>`__, `#699 <https://github.com/hpcugent/easybuild-framework/pull/699>`__)

* various bug fixes, including:

  * avoid importing toolchain modules over and over again to make toolchain constants available in toolchain module (`#679 <https://github.com/hpcugent/easybuild-framework/pull/679>`)
  * only change the group id if current gid is different from what we want in ``adjust_permissions`` function (`#685 <https://github.com/hpcugent/easybuild-framework/pull/685>`)
  * restore original environment after running 'module purge' (`#698 <https://github.com/hpcugent/easybuild-framework/pull/698>`)

    * important sidenote: this results in resetting the entire environment, and has impact on the sanity check step;
    * any environment variables that are set before the EasyBlock.sanity_check_step method fires, are no longer there when the sanity check commands are run (cfr. `easyblocks#268 <https://github.com/hpcugent/easybuild-easyblocks/pull/268>`__)

**easyblocks**

* added **one** new `generic` easyblock: ``BinariesTarball`` (`#255 <https://github.com/hpcugent/easybuild-easyblocks/pull/255>`__)
* added support for **5** new software packages that require customized support:

  * DB (`#226 <https://github.com/hpcugent/easybuild-easyblocks/pull/226>`__), FDTD Solutions (`#239 <https://github.com/hpcugent/easybuild-easyblocks/pull/239>`__), FoldX (`#256 <https://github.com/hpcugent/easybuild-easyblocks/pull/256>`__), Mathematica (`#240 <https://github.com/hpcugent/easybuild-easyblocks/pull/240>`__), MUMPS (`#262 <https://github.com/hpcugent/easybuild-easyblocks/pull/262>`__)

* various enhancements, including:

  * support optionally running configure in generic ``MakeCp`` easyblock (`#252 <https://github.com/hpcugent/easybuild-easyblocks/pull/252>`__)
  * enhanced Clang easyblock to support building Clang 3.3 (`#248 <https://github.com/hpcugent/easybuild-easyblocks/pull/248>`__)
  * add support for ``$INTEL_LICENSE_FILE`` specifying multiple paths (`#251 <https://github.com/hpcugent/easybuild-easyblocks/pull/251>`__)
  * enhanced ATLAS easyblock to support building ATLAS 3.10.1 (`#258 <https://github.com/hpcugent/easybuild-easyblocks/pull/258>`__)

* various bug fixes:

  * add zlib lib dir in link path dirs for WPS (`#249 <https://github.com/hpcugent/easybuild-easyblocks/pull/249>`__)
  * stop using deprecated ``add_module`` function in imkl easyblock (`#250 <https://github.com/hpcugent/easybuild-easyblocks/pull/250>`__)
  * fixed PSI easyblock w.r.t. support for building plugins (`#254 <https://github.com/hpcugent/easybuild-easyblocks/pull/254>`__, `#269 <https://github.com/hpcugent/easybuild-easyblocks/pull/269>`__)
  * move OS check for Clang to ``check_readiness_step``, to allow a build job to be submitted from SL5 (`#263 <https://github.com/hpcugent/easybuild-easyblocks/pull/263>`__, `#264 <https://github.com/hpcugent/easybuild-easyblocks/pull/264>`__)
  * enable verbose build for DOLFIN, to allow for proper debugging if the build fails (`#265 <https://github.com/hpcugent/easybuild-easyblocks/pull/265>`__)
  * make sure ``$LDFLAGS`` and ``$INSTANT_*_DIR`` env vars are set for DOLFIN sanity check commands (`#268 <https://github.com/hpcugent/easybuild-easyblocks/pull/268>`__)

    *  this is required after resetting the environment after running module purge (see framework release notes)

  * don't try to load module in LAPACK test-only build (`#264 <https://github.com/hpcugent/easybuild-easyblocks/pull/264>`__, `#266 <https://github.com/hpcugent/easybuild-easyblocks/pull/266>`__)

**easyconfigs**

* added example easyconfig files for **9** new software packages:

  * BOINC (`#436 <https://github.com/hpcugent/easybuild-easyconfigs/pull/436>`__), DB (`#343 <https://github.com/hpcugent/easybuild-easyconfigs/pull/343>`__, `#449 <https://github.com/hpcugent/easybuild-easyconfigs/pull/449>`__), fastahack (`#374 <https://github.com/hpcugent/easybuild-easyconfigs/pull/374>`__), FDTD Solutions (`#387 <https://github.com/hpcugent/easybuild-easyconfigs/pull/387>`__), FoldX (`#440 <https://github.com/hpcugent/easybuild-easyconfigs/pull/440>`__, `#442 <https://github.com/hpcugent/easybuild-easyconfigs/pull/442>`__), Mathematica (`#394 <https://github.com/hpcugent/easybuild-easyconfigs/pull/394>`__),
    Mesquite (`#447 <https://github.com/hpcugent/easybuild-easyconfigs/pull/447>`__), MUMPS (`#447 <https://github.com/hpcugent/easybuild-easyconfigs/pull/447>`__), ParMGridGen (`#447 <https://github.com/hpcugent/easybuild-easyconfigs/pull/447>`__)

* added additional easyconfigs for goalf, gompi, ClangGCC, cgmvapich2, cgmvolf toolchains (`#350 <https://github.com/hpcugent/easybuild-easyconfigs/pull/350>`__, `#441 <https://github.com/hpcugent/easybuild-easyconfigs/pull/441>`__)

* added additional easyconfigs for various software packages:

  * ATLAS, Bison, bzip2, Clang, CMake, cURL, EasyBuild, expat, FFTW, GDB, gettext, git, HPL, LAPACK, libreadline,
    M4, METIS, MVAPICH2, Mercurial, ncurses, OpenBLAS, OpenMPI, ParMETIS, Python, ScaLAPACK, SCOTCH, Valgrind, zlib

* various 'bug' fixes, including:

  * fix source URL for lockfile in Python easyconfigs (`#428 <https://github.com/hpcugent/easybuild-easyconfigs/pull/428>`__)
  * correct dependency specifications w.r.t. versionsuffix and toolchain (`#431 <https://github.com/hpcugent/easybuild-easyconfigs/pull/431>`__)

    * this is required to support building the affected easyconfigs with a custom module naming scheme

  * correct PSI patch file to avoid errors w.r.t. memcpy not being in scope (`#446 <https://github.com/hpcugent/easybuild-easyconfigs/pull/446>`__)
  * fix gettext build with adding ``--without-emacs`` configure options, add gettext as dependency for a2ps (`#448 <https://github.com/hpcugent/easybuild-easyconfigs/pull/448>`__)
  * exclude EMACS support in a2ps because of build failures (`#452 <https://github.com/hpcugent/easybuild-easyconfigs/pull/452>`__)

v1.7.0 (September 2nd 2013)
---------------------------

feature + bugfix release

**framework**

* various enhancements, including:

  * also search for patch files in directory where easyconfig file is located (`#667 <https://github.com/hpcugent/easybuild-framework/pull/667>`__)
  * reduce false positives in reporting of possible errors messages (`#669 <https://github.com/hpcugent/easybuild-framework/pull/669>`__)
  * make module update ``$ACLOCAL`` if a share/aclocal subdir is found (`#670 <https://github.com/hpcugent/easybuild-framework/pull/670>`__)
  * add ``unwanted_env_vars`` easyconfig parameter to list environment variables to unset during install procedure (`#673 <https://github.com/hpcugent/easybuild-framework/pull/673>`__)
  * add support for updating list easyconfig values (next to string values) (`#676 <https://github.com/hpcugent/easybuild-framework/pull/676>`__)
  * add ``--dry-run`` command line option which prints installation overview for specified easyconfig files (`#677 <https://github.com/hpcugent/easybuild-framework/pull/677>`__)
* various bug fixes, including:
  * ensure that all extensions are listed in ``$EBEXTSLISTX`` set by module, also when using ``--skip`` (`#671 <https://github.com/hpcugent/easybuild-framework/pull/671>`__)
  * report reason for failed sanity check for extensions (`#672 <https://github.com/hpcugent/easybuild-framework/pull/672>`__, `#678 <https://github.com/hpcugent/easybuild-framework/pull/678>`__)
  * fix ``--list-toolchains`` command line option (`#675 <https://github.com/hpcugent/easybuild-framework/pull/675>`__)

**easyblocks**

* added support for **3** new software packages that require customized support:

  * Libint2 (`#236 <https://github.com/hpcugent/easybuild-easyblocks/pull/236>`__), Qt (`#210 <https://github.com/hpcugent/easybuild-easyblocks/pull/210>`__), Rosetta (`#218 <https://github.com/hpcugent/easybuild-easyblocks/pull/218>`__)

* various enhancements, including:

  * allow building OpenFOAM without 3rd party tools (`#230 <https://github.com/hpcugent/easybuild-easyblocks/pull/230>`__)
  * also add sitelib path to ``$PERL5LIB``, refactor code to add generic ``get_site_suffix`` function (`#232 <https://github.com/hpcugent/easybuild-easyblocks/pull/232>`__, `#233 <https://github.com/hpcugent/easybuild-easyblocks/pull/233>`__)
  * support building imkl FFT wrappers using MVAPICH2 MPI library (`#234 <https://github.com/hpcugent/easybuild-easyblocks/pull/234>`__)
  * remove libnpp from CUDA sanity check to support installing CUDA v5.5 (`#238 <https://github.com/hpcugent/easybuild-easyblocks/pull/238>`__)
  * pick up ``$INTEL_LICENSE_FILE`` for Intel tools, if it is set (`#243 <https://github.com/hpcugent/easybuild-easyblocks/pull/243>`__)
    * note: gets preference over ``license_file`` easyconfig parameter

* various bug fixes:

  * call WRF build script with '``tcsh <script>`` to ensure that tcsh available in ``$PATH`` is used (`#231 <https://github.com/hpcugent/easybuild-easyblocks/pull/231>`__)
  * make sure some environment variables that may disrupt the GCC install procedure are unset (`#237 <https://github.com/hpcugent/easybuild-easyblocks/pull/237>`__)
    * e.g., ``$CPATH``, ``$C_INCLUDE_PATH``, ``$CPLUS_INCLUDE_PATH``, ``$OBJC_INCLUDE_PATH``, ``$LIBRARY_PATH``

  * code cleanup in GEANT4 easyblock: use ``self.version`` (instead of ``self.get_installversion()``) (`#242 <https://github.com/hpcugent/easybuild-easyblocks/pull/242>`__)
  * enhance list of ``noqanda`` patterns for CUDA, to get less failing installations (`#244 <https://github.com/hpcugent/easybuild-easyblocks/pull/244>`__)

**easyconfigs**

* added example easyconfig files for **15** new software packages:

  * Glib (`#294 <https://github.com/hpcugent/easybuild-easyconfigs/pull/294>`__, `#400 <https://github.com/hpcugent/easybuild-easyconfigs/pull/400>`__), GLPK (`#400 <https://github.com/hpcugent/easybuild-easyconfigs/pull/400>`__), horton (`#413 <https://github.com/hpcugent/easybuild-easyconfigs/pull/413>`__), libint2 (`#413 <https://github.com/hpcugent/easybuild-easyconfigs/pull/413>`__), molmod (`#413 <https://github.com/hpcugent/easybuild-easyconfigs/pull/413>`__), Rosetta (`#336 <https://github.com/hpcugent/easybuild-easyconfigs/pull/336>`__), SCons (`#336 <https://github.com/hpcugent/easybuild-easyconfigs/pull/336>`__), Stacks (`#367 <https://github.com/hpcugent/easybuild-easyconfigs/pull/367>`__, `#377 <https://github.com/hpcugent/easybuild-easyconfigs/pull/377>`__), sympy (`#413 <https://github.com/hpcugent/easybuild-easyconfigs/pull/413>`__), Qt (`#294 <https://github.com/hpcugent/easybuild-easyconfigs/pull/294>`__), XML-LibXML (`#397 <https://github.com/hpcugent/easybuild-easyconfigs/pull/397>`__), XML-Simple (`#397 <https://github.com/hpcugent/easybuild-easyconfigs/pull/397>`__), yaff (`#413 <https://github.com/hpcugent/easybuild-easyconfigs/pull/413>`__), YAML-Syck (`#380 <https://github.com/hpcugent/easybuild-easyconfigs/pull/380>`__), zsh (`#376 <https://github.com/hpcugent/easybuild-easyconfigs/pull/376>`__)

* added additional easyconfigs for various software packages:

  * BLAST, BamTools, BioPerl, Bison, Boost, bzip2, CMake, Cython, CUDA, FFTW, FIAT, GCC, GMP, gettext, git, h5py,
    HDF5, libffi, libreadline, libxc, matplotlib, METIS, ncurses, Oases, Python, RAxML, ScientificPython, Szip,
    tcsh, imkl, MVAPICH2, TotalView, VTune, WRF, zlib

* added toolchain easyconfig files for HPCBIOS policies (`#402 <https://github.com/hpcugent/easybuild-easyconfigs/pull/402>`__, `#407 <https://github.com/hpcugent/easybuild-easyconfigs/pull/407>`__)

  * HPCBIOS_BioInfo, HPCBIOS_Debuggers, HPCBIOS_LifeSciences, HPCBIOS_Math, HPCBIOS_Profilers

* various enhancements, including:

  * added more XML Perl modules to non-bare Perl easyconfigs (`#375 <https://github.com/hpcugent/easybuild-easyconfigs/pull/375>`__)

* various 'bug' fixes, including:

  * fix website/description in scipy easyconfigs (`#399 <https://github.com/hpcugent/easybuild-easyconfigs/pull/399>`__)
  * specify OpenMPI libibverbs-dev(el) OS dependency in an OS-dependent way (`#403 <https://github.com/hpcugent/easybuild-easyconfigs/pull/403>`__)
  * add patch file for M4 to fix building on systems with recent glibc (>=2.16) (`#406 <https://github.com/hpcugent/easybuild-easyconfigs/pull/406>`__)
  * align moduleclass in R easyconfigs (`#411 <https://github.com/hpcugent/easybuild-easyconfigs/pull/411>`__)
  * fixed filename of Biopython/CD-HIT easyconfig files (`#407 <https://github.com/hpcugent/easybuild-easyconfigs/pull/407>`__)
  * disable parallel building of otcl (`#419 <https://github.com/hpcugent/easybuild-easyconfigs/pull/419>`__)

v1.6.0 (July 11th 2013)
-----------------------

feature + bugfix release

**framework**

* added support for using Lmod as module tool (`#645 <https://github.com/hpcugent/easybuild-framework/pull/645>`__)
* various other enhancements, including:

  * allow prepending to/appending to/overwriting list easyconfig parameters using ``--try-amend-X`` (`#658 <https://github.com/hpcugent/easybuild-framework/pull/658>`__, `#664 <https://github.com/hpcugent/easybuild-framework/pull/664>`__)

* various bug fixes, including:

  * add salt to temporary log file name (`#656 <https://github.com/hpcugent/easybuild-framework/pull/656>`__, `#665 <https://github.com/hpcugent/easybuild-framework/pull/665>`__)
  * fix determining CPU architecture on Rasberry Pi (ARM) systems (`#655 <https://github.com/hpcugent/easybuild-framework/pull/655>`__, `#662 <https://github.com/hpcugent/easybuild-framework/pull/662>`__)
  * fix support for determining base path of tarballs containing a single file (`#660 <https://github.com/hpcugent/easybuild-framework/pull/660>`__)

**easyblocks**

* added support for **2** new software packages that require customized support:

  * BamTools (`#224 <https://github.com/hpcugent/easybuild-easyblocks/pull/224>`__), BLAT (`#214 <https://github.com/hpcugent/easybuild-easyblocks/pull/214>`__)

* various enhancements, including:

  * update impi easyblock to allow installing impi v4.1.1, which features a slight change in build procedure (`#217 <https://github.com/hpcugent/easybuild-easyblocks/pull/217>`__)
  * enhance ``PackedBinary`` easyblock to copy both files and directories (`#212 <https://github.com/hpcugent/easybuild-easyblocks/pull/212>`__)
  * added get ``sitearch_suffix`` to Perl search path and use it in ``PerlModule`` easyblock (`#209 <https://github.com/hpcugent/easybuild-easyblocks/pull/209>`__)

* various bug fixes:

  * make sure EasyBuild configuration is initialized when running unit tests (`#220 <https://github.com/hpcugent/easybuild-easyblocks/pull/220>`__)
  * make Boost easyblock pick up configopts easyconfig parameter (`#221 <https://github.com/hpcugent/easybuild-easyblocks/pull/221>`__)
  * add ``-DMPICH_IGNORE_CXX_SEEK`` compiler flag for Mothur when MPI support is enabled (`#222 <https://github.com/hpcugent/easybuild-easyblocks/pull/222>`__)
  * fix Boost sanity check, only check for ``libboost_python.so`` if Python module is loaded (`#223 <https://github.com/hpcugent/easybuild-easyblocks/pull/223>`__)
  * enhance Trinity support w.r.t. jellyfish (`#225 <https://github.com/hpcugent/easybuild-easyblocks/pull/225>`__, `#227 <https://github.com/hpcugent/easybuild-easyblocks/pull/227>`__)
  * fix checking for ``beagle-lib`` dep (deprecate checking for BEAGLE) for MrBayes (`#228 <https://github.com/hpcugent/easybuild-easyblocks/pull/228>`__)

**easyconfigs**

* added example easyconfig files for **26** new software packages:

  * ALLPATHS-LG (`#359 <https://github.com/hpcugent/easybuild-easyconfigs/pull/359>`__), AutoMake (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__), BamTools (`#319 <https://github.com/hpcugent/easybuild-easyconfigs/pull/319>`__, `#338 <https://github.com/hpcugent/easybuild-easyconfigs/pull/338>`__), BLAT (`#340 <https://github.com/hpcugent/easybuild-easyconfigs/pull/340>`__), Biopython (`#356 <https://github.com/hpcugent/easybuild-easyconfigs/pull/356>`__), cairo (`#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__),
    CCfits (`#327 <https://github.com/hpcugent/easybuild-easyconfigs/pull/327>`__), CD-HIT (`#344 <https://github.com/hpcugent/easybuild-easyconfigs/pull/344>`__), CFITSIO (`#327 <https://github.com/hpcugent/easybuild-easyconfigs/pull/327>`__), Diffutils (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__), FASTA (`#358 <https://github.com/hpcugent/easybuild-easyconfigs/pull/358>`__, `#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__), findutils (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__),
    fontconfig (`#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__), gawk (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__), gettext (`#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__), GLIMMER (`#357 <https://github.com/hpcugent/easybuild-easyconfigs/pull/357>`__, `#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__), libidn (`#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__), LibTIFF (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__),
    libungif (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__), make (`#355 <https://github.com/hpcugent/easybuild-easyconfigs/pull/355>`__), MUSCLE (`#339 <https://github.com/hpcugent/easybuild-easyconfigs/pull/339>`__), Oases (`#354 <https://github.com/hpcugent/easybuild-easyconfigs/pull/354>`__), pixman (`#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__), PLINK (`#352 <https://github.com/hpcugent/easybuild-easyconfigs/pull/352>`__), RCS (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__), SQLite (`#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__)

* added additional easyconfigs for various software packages:

  * ant, Bash, Bison, bzip2, cURL, expat, GCC, EasyBuild, freetype, FFTW, GDB, git, HMMER, JUnit, libreadline, libpng,
    libtool, libxml2, libxslt, M4, makedepend, Mothur, MVAPICH2, Mercurial, ncurses, OpenBLAS, Python, ScaLAPACK, Tcl,
    tcsh, TopHat, Trinity, Valgrind, Velvet, VTune, zlib (see `#169 <https://github.com/hpcugent/easybuild-easyconfigs/pull/169>`__, `#297 <https://github.com/hpcugent/easybuild-easyconfigs/pull/297>`__, `#298 <https://github.com/hpcugent/easybuild-easyconfigs/pull/298>`__, `#301 <https://github.com/hpcugent/easybuild-easyconfigs/pull/301>`__, `#309 <https://github.com/hpcugent/easybuild-easyconfigs/pull/309>`__, `#323 <https://github.com/hpcugent/easybuild-easyconfigs/pull/323>`__, `#331 <https://github.com/hpcugent/easybuild-easyconfigs/pull/331>`__, `#332 <https://github.com/hpcugent/easybuild-easyconfigs/pull/332>`__, `#341 <https://github.com/hpcugent/easybuild-easyconfigs/pull/341>`__, `#347 <https://github.com/hpcugent/easybuild-easyconfigs/pull/347>`__, `#349 <https://github.com/hpcugent/easybuild-easyconfigs/pull/349>`__, `#351 <https://github.com/hpcugent/easybuild-easyconfigs/pull/351>`__, `#355 <https://github.com/hpcugent/easybuild-easyconfigs/pull/355>`__, `#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__)

* various enhancements, including:

  * added easyconfigs for ``ictce/5.4.0``, ``ictce/5.5.0`` and ``gmvolf/1.7.12`` toolchain modules (`#297 <https://github.com/hpcugent/easybuild-easyconfigs/pull/297>`__, `#332 <https://github.com/hpcugent/easybuild-easyconfigs/pull/332>`__, `#349 <https://github.com/hpcugent/easybuild-easyconfigs/pull/349>`__)
  * added a template sanity_check_paths as 'MUST' in TEMPLATE.eb (`#329 <https://github.com/hpcugent/easybuild-easyconfigs/pull/329>`__)
  * introduced biodeps 'toolchain' to ease keeping common dependencies for bio* software in sync (`#309 <https://github.com/hpcugent/easybuild-easyconfigs/pull/309>`__)
  * added collection of easyconfigs for ictce/5.3.0 (`#309 <https://github.com/hpcugent/easybuild-easyconfigs/pull/309>`__, `#323 <https://github.com/hpcugent/easybuild-easyconfigs/pull/323>`__)

    * bam2fastq, bbFTP, BLAST, Boost, DL_POLY Classic, EMBOSS, FFTW, libharu, libxml2, libxslt, libyaml, lxml,
      Mercurial, Mothur, mpi4py, ncurses, ns, orthomcl, otcl, PAML, Perl, PyYAML, pandas, problog, scikit-learn,
      TiCCutils, TiMBL, TinySVM, TopHat, tclcl, YamCha

  * added missing dependencies for various software packages (`#323 <https://github.com/hpcugent/easybuild-easyconfigs/pull/323>`__, `#328 <https://github.com/hpcugent/easybuild-easyconfigs/pull/328>`__, `#348 <https://github.com/hpcugent/easybuild-easyconfigs/pull/348>`__, `#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__)
  * style fixes in various easyconfigs (`#309 <https://github.com/hpcugent/easybuild-easyconfigs/pull/309>`__, `#323 <https://github.com/hpcugent/easybuild-easyconfigs/pull/323>`__, `#345 <https://github.com/hpcugent/easybuild-easyconfigs/pull/345>`__, `#349 <https://github.com/hpcugent/easybuild-easyconfigs/pull/349>`__, `#355 <https://github.com/hpcugent/easybuild-easyconfigs/pull/355>`__, `#361 <https://github.com/hpcugent/easybuild-easyconfigs/pull/361>`__)

* various 'bug' fixes, including:

  * added ``pic`` toolchain option for Perl goolf easyconfig (`#299 <https://github.com/hpcugent/easybuild-easyconfigs/pull/299>`__)
  * fixed source URLs for R (use correct template ``%(version_major)s``) (`#302 <https://github.com/hpcugent/easybuild-easyconfigs/pull/302>`__)
  * synced libreadline easyconfigs w.r.t. ncurses dependency (`#303 <https://github.com/hpcugent/easybuild-easyconfigs/pull/303>`__)
  * make sure EasyBuild configuration is initialized when running unit tests (`#334 <https://github.com/hpcugent/easybuild-easyconfigs/pull/334>`__)
  * specify ``lowopt`` (-O1) optimization level for OpenIFS, to avoid floating-point related issues (`#328 <https://github.com/hpcugent/easybuild-easyconfigs/pull/328>`__)
  * fix naming of 'beagle-lib' (used to be 'BEAGLE'), to avoid name clashes with other software package(s) (`#346 <https://github.com/hpcugent/easybuild-easyconfigs/pull/346>`__)

v1.5.0 (June 1st 2013)
----------------------

feature + bugfix release

**framework**

* various enhancements, including:

  * define ``SHLIB_EXT`` constant for shared library extension (``.so``, ``.dylib``), deprecate ``shared_lib_ext`` global var (`#630 <https://github.com/hpcugent/easybuild-framework/pull/630>`__)
  * enhance support for sanity checking extensions (`#632 <https://github.com/hpcugent/easybuild-framework/pull/632>`__, `#649 <https://github.com/hpcugent/easybuild-framework/pull/649>`__)
  * add support for ``modextrapaths`` easyconfig parameter (`#634 <https://github.com/hpcugent/easybuild-framework/pull/634>`__, `#637 <https://github.com/hpcugent/easybuild-framework/pull/637>`__)
  * allow ``source_urls`` to be templated for extensions (`#639 <https://github.com/hpcugent/easybuild-framework/pull/639>`__, `#646 <https://github.com/hpcugent/easybuild-framework/pull/646>`__, `#647 <https://github.com/hpcugent/easybuild-framework/pull/647>`__)
  * set ``OMPI_*`` environment variables for OpenMPI (`#640 <https://github.com/hpcugent/easybuild-framework/pull/640>`__)
  * make BLACS optional as toolchain element, depending on ScaLAPACK version (`#638 <https://github.com/hpcugent/easybuild-framework/pull/638>`__)

* various bug fixes, including:

  * fixed ``--list-toolchains``, avoid listing toolchains multiple times (`#628 <https://github.com/hpcugent/easybuild-framework/pull/628>`__)
  * fix templating dictionary after parsing easyconfig file (`#633 <https://github.com/hpcugent/easybuild-framework/pull/633>`__)
  * fix support for ACML as compiler toolchain element (`#632 <https://github.com/hpcugent/easybuild-framework/pull/632>`__)
  * make unit tests clean up after themselves more thoroughly (`#641 <https://github.com/hpcugent/easybuild-framework/pull/641>`__, `#642 <https://github.com/hpcugent/easybuild-framework/pull/642>`__, `#643 <https://github.com/hpcugent/easybuild-framework/pull/643>`__)

**easyblocks**

* added **one** new `generic` easyblock: ``MakeCp`` (`#208 <https://github.com/hpcugent/easybuild-easyblocks/pull/208>`__)
* added support for **5** new software packages that require customized support:

  * CBLAS (`#192 <https://github.com/hpcugent/easybuild-easyblocks/pull/192>`__), FreeSurfer (`#194 <https://github.com/hpcugent/easybuild-easyblocks/pull/194>`__), Mothur (`#206 <https://github.com/hpcugent/easybuild-easyblocks/pull/206>`__), OpenIFS (`#200 <https://github.com/hpcugent/easybuild-easyblocks/pull/200>`__), PSI (`#191 <https://github.com/hpcugent/easybuild-easyblocks/pull/191>`__)

* various enhancements, including:

  * add support for building ScaLAPACK 2.x on top of QLogic MPI (`#195 <https://github.com/hpcugent/easybuild-easyblocks/pull/195>`__)
  * support newer BWA versions (`#199 <https://github.com/hpcugent/easybuild-easyblocks/pull/199>`__)
  * explicitly list license server type in ABAQUS install options, required for correct installation of v6.12 (`#198 <https://github.com/hpcugent/easybuild-easyblocks/pull/198>`__)
  * update SCOTCH and OpenFOAM easyblock for recent versions (`#201 <https://github.com/hpcugent/easybuild-easyblocks/pull/201>`__)

* various bug fixes:

  * fix numpy easyblock to get an optimal build (w.r.t. ``numpy.dot`` performance) (`#192 <https://github.com/hpcugent/easybuild-easyblocks/pull/192>`__)
  * correct build procedure for MUMmer to yield a complete installation (`#196 <https://github.com/hpcugent/easybuild-easyblocks/pull/196>`__, `#197 <https://github.com/hpcugent/easybuild-easyblocks/pull/197>`__)
  * make unit tests clean up after themselves more thoroughly (`#203 <https://github.com/hpcugent/easybuild-easyblocks/pull/203>`__, `#204 <https://github.com/hpcugent/easybuild-easyblocks/pull/204>`__)
  * fix getting Perl version for extensions (`#205 <https://github.com/hpcugent/easybuild-easyblocks/pull/205>`__)

**easyconfigs**

* added example easyconfig files for **23** new software packages:

  * bam2fastq (`#287 <https://github.com/hpcugent/easybuild-easyconfigs/pull/287>`__), CBLAS (`#263 <https://github.com/hpcugent/easybuild-easyconfigs/pull/263>`__), EMBOSS (`#265 <https://github.com/hpcugent/easybuild-easyconfigs/pull/265>`__, `#290 <https://github.com/hpcugent/easybuild-easyconfigs/pull/290>`__), FCM (`#272 <https://github.com/hpcugent/easybuild-easyconfigs/pull/272>`__), FRC_align (`#273 <https://github.com/hpcugent/easybuild-easyconfigs/pull/273>`__), freeglut (`#271 <https://github.com/hpcugent/easybuild-easyconfigs/pull/271>`__),
    FreeSurfer (`#271 <https://github.com/hpcugent/easybuild-easyconfigs/pull/271>`__), FSL (`#271 <https://github.com/hpcugent/easybuild-easyconfigs/pull/271>`__), GATK (`#287 <https://github.com/hpcugent/easybuild-easyconfigs/pull/287>`__), libharu (`#290 <https://github.com/hpcugent/easybuild-easyconfigs/pull/290>`__), libxslt (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), MariaDB (`#292 <https://github.com/hpcugent/easybuild-easyconfigs/pull/292>`__), Mothur (`#265 <https://github.com/hpcugent/easybuild-easyconfigs/pull/265>`__)
    mpi4py (`#276 <https://github.com/hpcugent/easybuild-easyconfigs/pull/276>`__), OpenIFS (`#272 <https://github.com/hpcugent/easybuild-easyconfigs/pull/272>`__), orthomcl (`#265 <https://github.com/hpcugent/easybuild-easyconfigs/pull/265>`__), PAML (`#287 <https://github.com/hpcugent/easybuild-easyconfigs/pull/287>`__), pandas (`#262 <https://github.com/hpcugent/easybuild-easyconfigs/pull/262>`__), phonopy (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), problog (`#277 <https://github.com/hpcugent/easybuild-easyconfigs/pull/277>`__),
    PSI (`#258 <https://github.com/hpcugent/easybuild-easyconfigs/pull/258>`__), PyYAML (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), RAxML (`#277 <https://github.com/hpcugent/easybuild-easyconfigs/pull/277>`__)

* added additional example easyconfig files for:

  * ABINIT (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), ACML (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__), BLAST (`#275 <https://github.com/hpcugent/easybuild-easyconfigs/pull/275>`__), Boost (`#273 <https://github.com/hpcugent/easybuild-easyconfigs/pull/273>`__), BWA (`#270 <https://github.com/hpcugent/easybuild-easyconfigs/pull/270>`__), bzip2 (`#263 <https://github.com/hpcugent/easybuild-easyconfigs/pull/263>`__), Chapel (`#240 <https://github.com/hpcugent/easybuild-easyconfigs/pull/240>`__), CMake (`#290 <https://github.com/hpcugent/easybuild-easyconfigs/pull/290>`__),
    FFTW2 (`#247 <https://github.com/hpcugent/easybuild-easyconfigs/pull/247>`__, `#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__), flex (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__), freetype (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), grib_api (`#272 <https://github.com/hpcugent/easybuild-easyconfigs/pull/272>`__), gzip (`#265 <https://github.com/hpcugent/easybuild-easyconfigs/pull/265>`__), Java (`#279 <https://github.com/hpcugent/easybuild-easyconfigs/pull/279>`__), libpng (`#240 <https://github.com/hpcugent/easybuild-easyconfigs/pull/240>`__, `#279 <https://github.com/hpcugent/easybuild-easyconfigs/pull/279>`__),
    libreadline (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__), libxml2 (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), libxml (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), matplotlib (`#235 <https://github.com/hpcugent/easybuild-easyconfigs/pull/235>`__), MCL (`#265 <https://github.com/hpcugent/easybuild-easyconfigs/pull/265>`__), MUMmer (`#265 <https://github.com/hpcugent/easybuild-easyconfigs/pull/265>`__), ncurses (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__),
    numpy (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__), OpenFOAM (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__), Perl (`#265 <https://github.com/hpcugent/easybuild-easyconfigs/pull/265>`__), Python (`#276 <https://github.com/hpcugent/easybuild-easyconfigs/pull/276>`__, `#263 <https://github.com/hpcugent/easybuild-easyconfigs/pull/263>`__), R (`#240 <https://github.com/hpcugent/easybuild-easyconfigs/pull/240>`__, `#279 <https://github.com/hpcugent/easybuild-easyconfigs/pull/279>`__), SCOTCH (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__), ScaLAPACK (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__),
    TopHat (`#289 <https://github.com/hpcugent/easybuild-easyconfigs/pull/289>`__), Valgrind (`#255 <https://github.com/hpcugent/easybuild-easyconfigs/pull/255>`__), zlib (`#267 <https://github.com/hpcugent/easybuild-easyconfigs/pull/267>`__)

* various enhancements, including:

  * enhance unit test suite, include testing for module conflicts (`#256 <https://github.com/hpcugent/easybuild-easyconfigs/pull/256>`__) and presence of patch files (`#264 <https://github.com/hpcugent/easybuild-easyconfigs/pull/264>`__)
  * use provided constants and templates in easyconfig files where appropriate (`#248 <https://github.com/hpcugent/easybuild-easyconfigs/pull/248>`__, `#266 <https://github.com/hpcugent/easybuild-easyconfigs/pull/266>`__, `#281 <https://github.com/hpcugent/easybuild-easyconfigs/pull/281>`__)

* various 'bug' fixes, including:

  * get rid of hardcoded license_file paths for VTune, Inspector (`#253 <https://github.com/hpcugent/easybuild-easyconfigs/pull/253>`__)
  * assign proper moduleclass where they were missing (`#278 <https://github.com/hpcugent/easybuild-easyconfigs/pull/278>`__)
  * fix naming for LZO (`#280 <https://github.com/hpcugent/easybuild-easyconfigs/pull/280>`__)
  * make unit tests clean up after themselves more thoroughly (`#283 <https://github.com/hpcugent/easybuild-easyconfigs/pull/283>`__, `#284 <https://github.com/hpcugent/easybuild-easyconfigs/pull/284>`__, `#285 <https://github.com/hpcugent/easybuild-easyconfigs/pull/285>`__, `#286 <https://github.com/hpcugent/easybuild-easyconfigs/pull/286>`__)
  * fix TopHat dependencies (`#289 <https://github.com/hpcugent/easybuild-easyconfigs/pull/289>`__)
  * fix source URLs for XML (`#279 <https://github.com/hpcugent/easybuild-easyconfigs/pull/279>`__)
  * fix versions for all listed R extensions (`#279 <https://github.com/hpcugent/easybuild-easyconfigs/pull/279>`__)
  * fix CUDA easyconfig file for use on Debian Squeeze (`#291 <https://github.com/hpcugent/easybuild-easyconfigs/pull/291>`__)
  * correct easyconfig filename and module name mismatches (bbcp, DL_POLY Classic, ...) (`#295 <https://github.com/hpcugent/easybuild-easyconfigs/pull/295>`__)

v1.4.0 (May 2nd 2013)
---------------------

feature + bugfix release

**framework**

* the unit tests for easybuild-framework were moved to test/framework, to make things consistent with easybuild-easyblocks and easybuild-easyconfigs (`#611 <https://github.com/hpcugent/easybuild-framework/pull/611>`__, `#613 <https://github.com/hpcugent/easybuild-framework/pull/613>`__, `#624 <https://github.com/hpcugent/easybuild-framework/pull/624>`__)

  * running the framework unit tests should now be using ``python -m test.framework.suite``

* various other enhancements, including:

  * extend unit test suite (`#593 <https://github.com/hpcugent/easybuild-framework/pull/593>`__, `#599 <https://github.com/hpcugent/easybuild-framework/pull/599>`__, `#603 <https://github.com/hpcugent/easybuild-framework/pull/603>`__, `#618 <https://github.com/hpcugent/easybuild-framework/pull/618>`__, `#620 <https://github.com/hpcugent/easybuild-framework/pull/620>`__, `#622 <https://github.com/hpcugent/easybuild-framework/pull/622>`__, `#624 <https://github.com/hpcugent/easybuild-framework/pull/624>`__, ...)
  * extended list of constants and templates that can be used in easyconfig files (`#566 <https://github.com/hpcugent/easybuild-framework/pull/566>`__)
  * add support for additional compiler toolchains

    * CUDA-enabled toolchain: ``goolfc`` (`#603 <https://github.com/hpcugent/easybuild-framework/pull/603>`__, `#624 <https://github.com/hpcugent/easybuild-framework/pull/624>`__)
    * Clang(+GCC)-based toolchains: ``cgoolf``, ``cgmpolf``, ``cgmvolf`` (`#593 <https://github.com/hpcugent/easybuild-framework/pull/593>`__, `#598 <https://github.com/hpcugent/easybuild-framework/pull/598>`__, `#600 <https://github.com/hpcugent/easybuild-framework/pull/600>`__)
    * gmvolf (GCC+MVAPICH2+...) (`#585 <https://github.com/hpcugent/easybuild-framework/pull/585>`__)

  * properly decode easyblock to module name using ``decode_*`` functions (`#618 <https://github.com/hpcugent/easybuild-framework/pull/618>`__)

* various bug fixes, including:

  * fixed default value for ``--stop`` (`#601 <https://github.com/hpcugent/easybuild-framework/pull/601>`__)
  * remove useless ``sleep()`` calls in ``run_cmd``, ``run_cmd_qa`` (`#599 <https://github.com/hpcugent/easybuild-framework/pull/599>`__)
  * determine module path based on class name, not software name (`#606 <https://github.com/hpcugent/easybuild-framework/pull/606>`__)
  * remove unwanted characters in build dirs (`#591 <https://github.com/hpcugent/easybuild-framework/pull/591>`__, `#607 <https://github.com/hpcugent/easybuild-framework/pull/607>`__)
  * ignore some error codes spit out by modulecmd that are actually warnings (`#609 <https://github.com/hpcugent/easybuild-framework/pull/609>`__)
  * fix ``agithub.py`` w.r.t. changes in GitHub API (user-agent string is now obligatory for non-authenticated connections) (`#617 <https://github.com/hpcugent/easybuild-framework/pull/617>`__)
  * fix typo breaking the ``adjust_cmd`` decorator on SuSE (`#615 <https://github.com/hpcugent/easybuild-framework/pull/615>`__)
  * fix prepending paths with absolute paths in module file (`#621 <https://github.com/hpcugent/easybuild-framework/pull/621>`__)
  * clean up open file handles properly (`#620 <https://github.com/hpcugent/easybuild-framework/pull/620>`__, `#624 <https://github.com/hpcugent/easybuild-framework/pull/624>`__)
  * fix ``--search`` help and implementation (`#622 <https://github.com/hpcugent/easybuild-framework/pull/622>`__)

**easyblocks**

* added a unit test suite for easyblocks (`#175 <https://github.com/hpcugent/easybuild-easyblocks/pull/175>`__, `#177 <https://github.com/hpcugent/easybuild-easyblocks/pull/177>`__, `#178 <https://github.com/hpcugent/easybuild-easyblocks/pull/178>`__)

  * every easyblock is parsed and instantiated as a sanity check

* added **one** new `generic` easyblock: ``PerlModule`` (`#183 <https://github.com/hpcugent/easybuild-easyblocks/pull/183>`__)
* added support for **8** new software packages that require customized support:

  * ABAQUS (`#179 <https://github.com/hpcugent/easybuild-easyblocks/pull/179>`__), Bowtie (`#174 <https://github.com/hpcugent/easybuild-easyblocks/pull/174>`__, `#185 <https://github.com/hpcugent/easybuild-easyblocks/pull/185>`__, `#186 <https://github.com/hpcugent/easybuild-easyblocks/pull/186>`__), Clang (`#151 <https://github.com/hpcugent/easybuild-easyblocks/pull/151>`__), DL_POLY Classic (`#118 <https://github.com/hpcugent/easybuild-easyblocks/pull/118>`__), ESMF (`#171 <https://github.com/hpcugent/easybuild-easyblocks/pull/171>`__), Perl (`#183 <https://github.com/hpcugent/easybuild-easyblocks/pull/183>`__),
    Intel VTune and Intel Inspector (`#180 <https://github.com/hpcugent/easybuild-easyblocks/pull/180>`__)

* the ``CMakeMake.configure_step`` parameter ``builddir`` was renamed to ``srcdir``, because the name ``builddir`` is incorrect (`#151 <https://github.com/hpcugent/easybuild-easyblocks/pull/151>`__)

  * ``builddir`` will remain supported for legacy purposes up until v2.0

* various enhancements, including:

  * reverted back to hardcoding Python library path, since it's hardcoded by setuptools too (`#184 <https://github.com/hpcugent/easybuild-easyblocks/pull/184>`__)
  * added MPICH support in ScaLAPACK easyblock (`#172 <https://github.com/hpcugent/easybuild-easyblocks/pull/172>`__)
  * enhanced NCL easyblock: add support UDUNITS and ESMF dependencies (`#171 <https://github.com/hpcugent/easybuild-easyblocks/pull/171>`__)
  * enhanced MATLAB easyblock: avoid hardcoding Java options, make sure ``$DISPLAY`` is unset, extend list of sanity check paths (`#181 <https://github.com/hpcugent/easybuild-easyblocks/pull/181>`__)
  * enhanced TotalView easyblock: add support for license file (`#146 <https://github.com/hpcugent/easybuild-easyblocks/pull/146>`__)

**easyconfigs**

* added a unit test suite for easyconfigs (`#228 <https://github.com/hpcugent/easybuild-easyconfigs/pull/228>`__, `#230 <https://github.com/hpcugent/easybuild-easyconfigs/pull/230>`__)
* added example easyconfig files for **20** new software packages:
  * ABAQUS (`#231 <https://github.com/hpcugent/easybuild-easyconfigs/pull/231>`__), BioPerl (`#242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/242>`__), Bowtie (`#227 <https://github.com/hpcugent/easybuild-easyconfigs/pull/227>`__), Clang (`#177 <https://github.com/hpcugent/easybuild-easyconfigs/pull/177>`__), CRF++ (`#131 <https://github.com/hpcugent/easybuild-easyconfigs/pull/131>`__), DL_POLY Classic (`#132 <https://github.com/hpcugent/easybuild-easyconfigs/pull/132>`__), ESMF, GROMACS (`#165 <https://github.com/hpcugent/easybuild-easyconfigs/pull/165>`__), HH-suite (`#219 <https://github.com/hpcugent/easybuild-easyconfigs/pull/219>`__), Inspector (`#232 <https://github.com/hpcugent/easybuild-easyconfigs/pull/232>`__), likwid (`#131 <https://github.com/hpcugent/easybuild-easyconfigs/pull/131>`__), Perl (`#242 <https://github.com/hpcugent/easybuild-easyconfigs/pull/242>`__), scikit (`#133 <https://github.com/hpcugent/easybuild-easyconfigs/pull/133>`__), TiCCutils (`#131 <https://github.com/hpcugent/easybuild-easyconfigs/pull/131>`__), TiMBL (`#131 <https://github.com/hpcugent/easybuild-easyconfigs/pull/131>`__), TinySVM (`#131 <https://github.com/hpcugent/easybuild-easyconfigs/pull/131>`__), UDUNITS (`#167 <https://github.com/hpcugent/easybuild-easyconfigs/pull/167>`__), VTune (`#232 <https://github.com/hpcugent/easybuild-easyconfigs/pull/232>`__), YamCha (`#131 <https://github.com/hpcugent/easybuild-easyconfigs/pull/131>`__)

* add example easyconfigs for new compiler toolchains (use ``eb --list-toolchains`` for a full list of supported toolchains):

  * the newly added toolchains only differ in compilers/MPI library, and all feature OpenBLAS, LAPACK, ScaLAPACK and FFTW
  * `goolfc`: GCC, CUDA (co-compiler), OpenMPI (`#191 <https://github.com/hpcugent/easybuild-easyconfigs/pull/191>`__)

    * a goolfc easyconfig for GROMACS is inluded as proof-of-concept (`#165 <https://github.com/hpcugent/easybuild-easyconfigs/pull/165>`__)

  * `cgmpolf`: Clang (C/C++ compilers), GCC (Fortran compilers), MPICH (`#213 <https://github.com/hpcugent/easybuild-easyconfigs/pull/213>`__)
  * `cgmvolf`: Clang, GCC, MVAPICH2 (`#218 <https://github.com/hpcugent/easybuild-easyconfigs/pull/218>`__)
  * `cgoolf`: Clang, GCC, OpenMPI (`#213 <https://github.com/hpcugent/easybuild-easyconfigs/pull/213>`__)
  * `gmvolf`: GCC, MVAPICH (`#202 <https://github.com/hpcugent/easybuild-easyconfigs/pull/202>`__, `#222 <https://github.com/hpcugent/easybuild-easyconfigs/pull/222>`__)

* ported already available easyconfigs to new compiler toolchains:

  * `ictce-5.3.0`: 193 easyconfigs (`#229 <https://github.com/hpcugent/easybuild-easyconfigs/pull/229>`__)
  * `cgmpolf`: 11 easyconfigs (`#213 <https://github.com/hpcugent/easybuild-easyconfigs/pull/213>`__)
  * `cgmvolf`: 11 easyconfigs (`#218 <https://github.com/hpcugent/easybuild-easyconfigs/pull/218>`__)
  * `cgoolf`: 12 easyconfigs (`#213 <https://github.com/hpcugent/easybuild-easyconfigs/pull/213>`__)
  * `gmvolf`: 10 easyconfigs (`#215 <https://github.com/hpcugent/easybuild-easyconfigs/pull/215>`__)

* added additional example easyconfig files for:

  * CMake (`#163 <https://github.com/hpcugent/easybuild-easyconfigs/pull/163>`__), git (`#210 <https://github.com/hpcugent/easybuild-easyconfigs/pull/210>`__), Java (`#206 <https://github.com/hpcugent/easybuild-easyconfigs/pull/206>`__), `#221 <https://github.com/hpcugent/easybuild-easyconfigs/pull/221>`__, Mercurial (`#201 <https://github.com/hpcugent/easybuild-easyconfigs/pull/201>`__, `#215 <https://github.com/hpcugent/easybuild-easyconfigs/pull/215>`__), ncurses (`#225 <https://github.com/hpcugent/easybuild-easyconfigs/pull/225>`__), TotalView (`#160 <https://github.com/hpcugent/easybuild-easyconfigs/pull/160>`__)

* various enhancements, including:

  * added ESMF and UDUNITS dependencies to NCL easyconfigs (`#211 <https://github.com/hpcugent/easybuild-easyconfigs/pull/211>`__)
  * changed value of source_urls in R easyconfigs, to be generic enough for version 3.0 and possibly beyond (`#251 <https://github.com/hpcugent/easybuild-easyconfigs/pull/251>`__)

* various 'bug' fixes, including:

  * add ``--enable-mpirun-prefix-by-default`` configure option for all OpenMPI easyconfigs (#205)

v1.3.0 (April 1st 2013)
-----------------------

feature + bugfix release

**framework**

* added script to bootstrap EasyBuild with EasyBuild, see https://github.com/hpcugent/easybuild/wiki/Bootstrapping-EasyBuild (`#531 <https://github.com/hpcugent/easybuild-framework/pull/531>`__)
* reorganize framework/easyconfig.py module into framework/easyconfig package with modules (`#574 <https://github.com/hpcugent/easybuild-framework/pull/574>`__, `#580 <https://github.com/hpcugent/easybuild-framework/pull/580>`__)
* support EasyBuild configuration via command line, environment variables and configuration files (`#529 <https://github.com/hpcugent/easybuild-framework/pull/529>`__, `#552 <https://github.com/hpcugent/easybuild-framework/pull/552>`__, `#556 <https://github.com/hpcugent/easybuild-framework/pull/556>`__, `#558 <https://github.com/hpcugent/easybuild-framework/pull/558>`__, `#559 <https://github.com/hpcugent/easybuild-framework/pull/559>`__)
* various other enhancements, including:

  * extended set of unit tests for eb command line options and EasyBuild configuration (`#517 <https://github.com/hpcugent/easybuild-framework/pull/517>`__, `#556 <https://github.com/hpcugent/easybuild-framework/pull/556>`__, `#559 <https://github.com/hpcugent/easybuild-framework/pull/559>`__, `#571 <https://github.com/hpcugent/easybuild-framework/pull/571>`__)
  * made ``--search`` also useful when easybuild-easyconfigs package is not installed (`#524 <https://github.com/hpcugent/easybuild-framework/pull/524>`__)
  * extended set of default module classes (`#525 <https://github.com/hpcugent/easybuild-framework/pull/525>`__)
  * add support for license easyconfig parameter (which will be mandatory in v2.x) (`#526 <https://github.com/hpcugent/easybuild-framework/pull/526>`__, `#569 <https://github.com/hpcugent/easybuild-framework/pull/569>`__)
  * added ``setup.cfg`` for ``setup.py`` to allow creating RPMs (`#528 <https://github.com/hpcugent/easybuild-framework/pull/528>`__)
  * added support for obtaining system information, see ``get_os_*`` functions in ``easybuild/tools/systemtools.py`` (`#543 <https://github.com/hpcugent/easybuild-framework/pull/543>`__, `#546 <https://github.com/hpcugent/easybuild-framework/pull/546>`__, `#547 <https://github.com/hpcugent/easybuild-framework/pull/547>`__)
  * added support for iterated builds that require cycling over multiple sets of configure/build/install options, e.g. FFTW (`#549 <https://github.com/hpcugent/easybuild-framework/pull/549>`__)
  * added support for OpenBLAS as toolchain lib for linear algebra (`#537 <https://github.com/hpcugent/easybuild-framework/pull/537>`__, `#565 <https://github.com/hpcugent/easybuild-framework/pull/565>`__)
  * added support for tweaking prefix and separator for library toolchain variables (``LIB*``) (`#572 <https://github.com/hpcugent/easybuild-framework/pull/572>`__, `#576 <https://github.com/hpcugent/easybuild-framework/pull/576>`__)
  * skip already built modules in regression testing mode, to ease regression testing (`#582 <https://github.com/hpcugent/easybuild-framework/pull/582>`__)
* various bug fixes, including:
  * added ``zip_safe`` flag to ``setup.py``, to silence multitude of warnings (`#521 <https://github.com/hpcugent/easybuild-framework/pull/521>`__)
  * only define ``LIBFFT`` for Intel MKL if FFTW interface libraries are available (`#518 <https://github.com/hpcugent/easybuild-framework/pull/518>`__, `#567 <https://github.com/hpcugent/easybuild-framework/pull/567>`__, `#579 <https://github.com/hpcugent/easybuild-framework/pull/579>`__)
  * set POSIX group early in build process, make EasyBuild aware of consistent chmod/chown failures (`#527 <https://github.com/hpcugent/easybuild-framework/pull/527>`__)
  * properly order the name/version keys for the toolchain easyconfig parameter when using ``--try-toolchain`` (`#563 <https://github.com/hpcugent/easybuild-framework/pull/563>`__)
  * take the ``skipsteps`` easyconfig parameter into account in regression testing mode as well (`#583 <https://github.com/hpcugent/easybuild-framework/pull/583>`__)

**easyblocks**

* added support for **2** new software packages that require customized support:

  * CUDA (`#145 <https://github.com/hpcugent/easybuild-easyblocks/pull/145>`__), Ferret (`#160 <https://github.com/hpcugent/easybuild-easyblocks/pull/160>`__, `#163 <https://github.com/hpcugent/easybuild-easyblocks/pull/163>`__)

* remove ``license`` easyconfig parameter from ``IntelBase``, since it clashes with generic ``license`` parameter (`#153 <https://github.com/hpcugent/easybuild-easyblocks/pull/153>`__, `#158 <https://github.com/hpcugent/easybuild-easyblocks/pull/158>`__)

  * ``license_file`` should be used instead (see `framework#569 <https://github.com/hpcugent/easybuild-easyblocks/pull/569/files>`__)
  * using ``license`` instead of ``license_file`` will be supported until v2.x for legacy purposes

* various enhancements, including:

  * stop hardcoding Python site-packages library dir, obtain it via ``distutils.sysconfig`` instead (`#141 <https://github.com/hpcugent/easybuild-easyblocks/pull/141>`__, `#156 <https://github.com/hpcugent/easybuild-easyblocks/pull/156>`__, `#159 <https://github.com/hpcugent/easybuild-easyblocks/pull/159>`__, `#161 <https://github.com/hpcugent/easybuild-easyblocks/pull/161>`__)
  * stop hardcoding list of libraries for BLAS libs, ask toolchain modules or use ``$LIBBLAS`` instead (`#150 <https://github.com/hpcugent/easybuild-easyblocks/pull/150>`__, `#155 <https://github.com/hpcugent/easybuild-easyblocks/pull/155>`__)
  * enhanced CP2K easyblock, following Intel guidelines for ``ictce`` builds (`#138 <https://github.com/hpcugent/easybuild-easyblocks/pull/138>`__)
  * added ``setup.cfg`` for ``setup.py`` to allow creating RPMs (`#140 <https://github.com/hpcugent/easybuild-easyblocks/pull/140>`__)
  * clean up specifying BLAS/LAPACK libs for building numpy, check whether requires patch is being used for IMKL builds (`#155 <https://github.com/hpcugent/easybuild-easyblocks/pull/155>`__, `#161 <https://github.com/hpcugent/easybuild-easyblocks/pull/161>`__)

* various bug fixes, including:

  * added ``zip_safe`` flag to ``setup.py``, to silence multitude of warnings (`#135 <https://github.com/hpcugent/easybuild-easyblocks/pull/135>`__)
  * install EasyBuild packages in reversed order to avoid funky setuptools issues (`#139 <https://github.com/hpcugent/easybuild-easyblocks/pull/139>`__)
  * fixed a typo in the ScaLAPACK easyblock, and set CCFLAGS and FCFLAGS for v2.x (`#149 <https://github.com/hpcugent/easybuild-easyblocks/pull/149>`__, `#162 <https://github.com/hpcugent/easybuild-easyblocks/pull/162>`__)
  * fix sanity check for python-meep (`#159 <https://github.com/hpcugent/easybuild-easyblocks/pull/159>`__)
  * exclude Python tests from DOLFIN sanity check, since they hang sometimes (`#161 <https://github.com/hpcugent/easybuild-easyblocks/pull/161>`__)
  * add support in ALADIN easyblock for answering question on location of ``libgrib_api.a`` (`#165 <https://github.com/hpcugent/easybuild-easyblocks/pull/165>`__)

**easyconfigs**

* added example easyconfig files for **13** new software packages:

  * Bash, CUDA, ccache, Ferret, gzip, libxc, ns, numactl, OpenBLAS, otcl, Tar, tclcl, tcsh
  * several of these easyconfig files were contributed by attendees of the EasyBuild hackathon in Cyprus!

* added example easyconfigs for goolf toolchain (`#158 <https://github.com/hpcugent/easybuild-easyconfigs/pull/158>`__)
* added example easyconfigs for builds with goolf toolchain, i.e. for all goalf easyconfigs (`#189 <https://github.com/hpcugent/easybuild-easyconfigs/pull/189>`__)

  * for several software packages, a patch file was needed to get them to build with GCC 4.7:

    * AMOS, BEAGLE, Cufflinks, DOLFIN, GATE, ns, Pasha, Trilinos, Trinity

  * for PETSc, a patch file was required to make it build with a toolchain that doesn't include BLACS

* added additional example easyconfig files for:

  * gompi, hwloc, LAPACK, MVAPICH2, OpenMPI, ScaLAPACK

* various enhancements, including:

  * define a proper module class in `all` easyconfigs, cfr. default module classes defined in framework (`#150 <https://github.com/hpcugent/easybuild-easyconfigs/pull/150>`__, `#159 <https://github.com/hpcugent/easybuild-easyconfigs/pull/159>`__, `#161 <https://github.com/hpcugent/easybuild-easyconfigs/pull/161>`__, `#162 <https://github.com/hpcugent/easybuild-easyconfigs/pull/162>`__, `#179 <https://github.com/hpcugent/easybuild-easyconfigs/pull/179>`__, `#181 <https://github.com/hpcugent/easybuild-easyconfigs/pull/181>`__)
  * extend FFTW easyconfig to 'fat' builds that include single, double, long double and quad precision libraries in the same module

    * quad precision is disabled for Intel compiler based builds (it requires GCC v4.6+)

  * the imkl easyconfigs used for the ictce 3.2.2.u3 toolchain now also enable FFTW interfaces

* various 'bug' fixes, including:

  * fix filename for Mercurial and ROOT easyconfig files
  * fix homepage/description for Hypre
  * fix enabling OpenMP support in OpenMPI: use ``--enable-openmp``, not ``--with-openmp``
  * use correct configure flag for enabling OpenMPI threading support in v1.6 (`#186 <https://github.com/hpcugent/easybuild-easyconfigs/pull/186>`__)

    * ``--enable-mpi-thread-multiple`` instead of ``--enable-mpi-threads``

  * explicitely add ``--without-openib --without-udapl`` configure options in OpenMPI easyconfig using versionsuffix ``-no-OFED`` (`#168 <https://github.com/hpcugent/easybuild-easyconfigs/pull/168>`__)

    * this avoids that OpenMPI auto-detects that it can enable Infiniband (OpenIB) support, which doesn't fit the -no-OFED versionsuffix
    * Note: this makes goalf-1.1.0-no-OFED effectively not suitable to produce software builds that are IB-capable!

  * remove explicit ``--with-udapl`` from OpenMPI easyconfigs, does more harm than good (`#178 <https://github.com/hpcugent/easybuild-easyconfigs/pull/178>`__)
  * remove libibvers, libibmad, libibumad as explicit dependencies for OpenMPI/MVAPICH2 (`#173 <https://github.com/hpcugent/easybuild-easyconfigs/pull/173>`__, `#182 <https://github.com/hpcugent/easybuild-easyconfigs/pull/182>`__)

    * leave it up to the OS to provide these, since the required version is too much tied to the version of IB drivers

  * use ``license_file`` in Intel tools easyconfigs, as opposed to the new generic ``license`` parameter with a different meaning (`#180 <https://github.com/hpcugent/easybuild-easyconfigs/pull/180>`__)
  * modify patch for impi to avoid installation problems due to hardcoded path in /tmp (`#185 <https://github.com/hpcugent/easybuild-easyconfigs/pull/185>`__)

    * now uses ``$USER-$RANDOM`` subdir to avoid clashes between different users on the same system

  * the patch file for numpy was extended to also supporting ATLAS and other BLAS libraries spread across multiple directories

    * the extension for ATLAS is required because we now no longer rely on the automatic numpy mechanism to find the ATLAS libs

  * fixed dependencies:

    * libibumad as dependency for libibmad
    * ncurses as dependency for libreadline
    * ncurses and zlib as dependency for SAMtools (+ enhanced patch)
    * remove explicit FFTW dependency for Meep, ... since toolchain already provided FFTW

v1.2.0 (February 28th 2013)
---------------------------

feature + bugfix release

**framework**

* new backend module for option parsing: generaloption
* support for using constants and string templates in easyconfig files

  * currently disabled for ``exts_filter`` and ``exts_list`` easyconfig parameters, for backward compatibility

* various other enhancements, including:

  * support for iqacml and iiqmpi toolchains (Intel compilers + QLogic MPI based)
  * clearer errors messages when sanity check failed
  * unit tests for (about half of) the ``eb`` command line options
  * support for specifying build/install steps to skip in easyconfig file (``skipsteps``)
  * support for allowing certain dependencies to be resolved by the system instead of modules (``allow_system_deps``)
  * cache ppn value required by regtest, clean up temporary files let behind by ``--regtest``/``--job``
  * make sure MPD is used as process manager for Intel MPI (required for impi v4.1 and later)
  * rename template names ``name`` and ``version`` used in exts_filter to ``ext_name``, ``ext_version``

    * ``name`` and ``version`` are still supported for legacy reasons

  * cleaned up module docstrings w.r.t. list of authors

* various bug fixes, including:

  * print correct (lowercase) toolchain names with ``--list-toolchains``
  * correct easyconfig parameter name ``license_server_port``
  * fix string quoting in develop modules
  * ensure ``modulecmd`` is run with original ``$LD_LIBRARY_PATH`` value

    * to avoid breaking ``modulecmd``, see https://bugzilla.redhat.com/show_bug.cgi?id=719785

  * remove use of hardcoded files/dirs in unit tests
  * fix various inconsistencies w.r.t. paths considered with ``--robot``
  * various cleanup and fixes w.r.t. logging

    * use correct logger instance in main script
    * stop passing logger instances around
    * make module logging variables private

  * get rid of ``ModuleGenerator`` deconstructor, clean up via ``EasyBlock.clean_up_fake_module``
  * fix disabling of ``optarch`` toolchain option (and extend unit tests to check on this)

**easyblocks**

* added **one** new `generic` easyblock: ``Rpm``
* added support for **6** new software packages that require customized support:

  * EasyBuild, EPD (Enthought Python Distribution), freetype, MATLAB, QLogic MPI (RPM), TotalView
  * support for installing EasyBuild with EasyBuild enables bootstrapping an EasyBuild installation!

* various enhancements, including:

  * corrections in WRF/WPS to also enable building with iqacml toolchain

    * use ``mpi_cmd_for`` instead of hardcoding test commands, using correct Fortran compilers (F90)

  * fix NCL easyblock to also support v6.1.x

    * use correct Fortran compiler (F90), set correct lib/include paths for dependencies (netCDF-Fortran, GDAL)

  * cleanup sweep of license headers and authors list in easyblock module docstrings
  * use new ``ext_name`` template name in ``exts_filter`` in Python and R easyblocks

* various bug fixes, including:

  * general code cleanup

    * don't set ``sanityCheckOK`` in ``Toolchain`` easyblock
    * get rid of using ``os.putenv``

  * NEURON easyblock: don't hardcode number of processes used in test cases
  * make sure ``easybuild.easyblocks.generic`` namespace is extendable

**easyconfigs**

* added example easyconfig files for **41** new software packages:

  * a2ps, AnalyzeFMRI, aria, bbcp, bbFTP, bbftpPRO, binutils, Bonnie++, ccache, cflow, cgdb, Corkscrew, EasyBuild,
    Elinks, EPD, FLUENT, fmri, GDB, GDAL, gnuplot, gnutls, gperf, Iperf, lftp, libyaml, lzo, MATLAB, mc, nano, NASM,
    nettle, numexpr, parallel, pyTables, QLogic MPI, Stow, TotalView, Valgrind, VTK, Yasm, zsync

* added example easyconfigs for iqacml and iiqmpi toolchains
* added additional example easyconfig files for:

  * ABINIT, ABySS, ACML, BFAST, Bison, BLACS, Cython, cURL, Doxygen, FFTW, flex, g2clib, g2lib, GHC, h5py, HDF, HDF5,
    HMMER, JasPer, icc, ictce, ifort, imkl, impi, libpng, libreadline, M4, matplotlib, MCL, MEME, mpiBLAST, NCL,
    ncurses, netCDF, netCDF-Fortran, NWChem, R, ScaLAPACK, Tcl, Tk, WPS, WRF, zlib

* various enhancements, including:

  * fix version of xtable R library in list of extensions for R, to avoid installation failures

* various 'bug' fixes, including:

  * fix toolchain and file names for ABINIT easyconfigs
  * fix sanity check paths for cURL
  * don't disable ``optarch`` for WRF, it's not needed (only disable heavy optimizations is required)
  * fix homepage/description for ALADIN

v1.1.0 (January 27th 2013)
--------------------------

feature + bugfix release

**framework**

* improvements w.r.t. support for software extensions (tested on Python and R, see easyblocks package)

  * cleaned up support for building/installing extensions
  * define ``ExtensionEasyblock`` class that implements support for installing extensions as stand-alone module as well
  * return to build dir before building/installing each extension
  * define ``EBEXTSLIST<NAME>`` environment variable in module if ``exts_list`` was defined
  * make sure sanity check for extensions results in an error if it fails

* various enhancements, including:

  * log both framework and easyblocks versions
  * add support for ``gimkl``, ``gmacml``, ``iccifort``, ``iomkl`` and ``ismkl`` toolchains
  * define ``*_SEQ compiler`` variables for sequential compilers
  * add ``--list-toolchains`` command line option for listing supported toolchains
  * add support for customizing software and modules install path suffixes
  * support both setuptools and distutils installation methods for finding installed easyconfigs
  * also consider robot path in list of paths searched for patch files
  * allow skipping of default extension sanity check (by setting ``modulename`` to False in options)

* various bug fixes, including:

  * typos in toolchain Python modules w.r.t. ``imkl`` support, handling of ``i8``/``optarch``/``unroll`` options
  * purge before loading 'fake' module, unload 'fake' module before removing it, use original ``$MODULEPATH``
  * restore environment after unloading fake module, set variables that were incorrectly unset, i.e., that were defined before as well
  * unset ``$TMPDIR`` for builds submitted as jobs (required by ``IntelBase`` easyblock)
  * correctly track easyconfig parse error
  * always run all jobs in regtest, also if dependency jobs failed
  * cosmetic adjustments to default EasyBuild configuration file to avoid confusion between e.g. ``build_dir`` and ``build_path`` (only latter matters)
  * fix SuSe hack, only prefix command with sourcing of ``/etc/profile.d/modules.sh`` if it is there
  * leave build directory before it is removed during cleanup step
  * load generated module file before running test cases

**easyblocks**

* added **3** new `generic` easyblocks: ``CMakePythonPackage``, ``JAR``, ``RPackage``
* added support for **23** new software packages that require customized support:

  * ACML, ALADIN, ant, Bioconductor (R packages), Chapel, Cufflinks, ESPResSo, FLUENT, Geant4, GHC, Java, NEURON, NWChem, PyZMQ, QuantumESPRESSO, R, Rmpi, ROOT, Rserve, SCOOP, Trinity, VSC-tools, XML

* various enhancements, including:

  * clean up of ``python.py`` easyblock:

    * merge ``EB_DefaultPythonPackage`` and ``PythonPackage`` easyblocks into generic `easyblock` ``PythonPackage``,
      which derives from ``ExtensionEasyblock``
    * move ``EB_FortranPythonPackage`` into dedicated `generic` ``FortranPythonPackage`` easyblock module
    * split off support for building/installing ``nose``, ``numpy``, ``scipy`` into dedicated ``EB_*`` easyblock
      modules, which allows them to be built as stand-alone modules as well

  * clean up testing of Python packages (``PythonPackage`` easyblock)
  * make sure there is no ``site.cfg`` in home dir when building Python packages,
    because e.g. ``scipy`` will pick it up
  * added support for building Intel MKL wrappers with OpenMPI toolchain
  * cleaning up of fake module that was loaded for running tests
  * move calls to functions that rely on environment up in the chain of steps (mostly for cleanup reasons)
  * use better module name for UFC sanity check, minor change to sanity check paths for UFC

* various bug fixes, including:

  * only call ``make ptcheck`` for ATLAS when multi-threading support is enabled
  * use a symbolic link for $HOME/intel instead of a randomly suffixed subdirectory in home and patching of Intel install scripts

    * latter does not work anymore with recent versions of Intel tools (2013.x)

**easyconfigs**

* added example easyconfig files for **48** new software packages:

  * ABINIT, ABySS, ACML, ALADIN, ant, BFAST, BLAST, Chapel, CLHEP, Cufflinks, ESPRresSo, GATE, GHC, Geant4,
    Greenlet, google-sparsehash, grib_api, HMMER, Java, JUnit, libibmad, libibumad, libibverbs, MCL, MDP,
    MEME, mpiBLAST, NCBI Toolkit, NEURON, NWChem, numpy, MDP, Oger, OpenPGM, paycheck, PyZMQ, QuantumESPRESSO,
    R, ROOT, SCOOP, scipy, Tophat, Trinity, util-linux, VSC-tools, wiki2beamer, XML, ZeroMQ

* added example easyconfigs for gmacml, gmvapich2, iccifort, ictce, iomkl toolchains
* added additional example easyconfig files for:

  * ATLAS, BLACS, Boost, Bowtie2, bzip2, CP2K, Doxygen, FFTW, GCC, HDF5, hwloc, icc, ifort, imkl, impi,
    JasPer, Libint, libreadline, libsmm, libxml, ncurses, netCDF, M4, Meep, MVAPICH2, OpenMPI, Python,
    ScaLAPACK, Szip, zlib

* various enhancements, including:

  * major style cleanup of all example easyconfig file (PEP008 compliance)
  * added setuptools to list of Python extensions
  * get rid of ``parallel`` versionsuffix for HDF5, as its meaningless (MPI-enabled build is always parallel)

* various 'bug' fixes, i.e. added missing dependencies or replaced OS dependencies with proper dependencies

v1.0.2 (December 8th 2012)
--------------------------

bugfix release

**framework**

* properly catch failing sanity check commands
* fix bug in toolchain support which cause linking environment variables set by toolchain to include too many libraries

  * elements in toolchain variables were being passed by reference instead of by value

* fix selecting a compiler toolchain for a specified software package (``--software-name``) if only a template is a viable option
* fix passing command line parameters with ``--job``
* fix list of valid stops (``-s``/``--stop``)
* fix minor issues in help messages (``-h``/``--help``)

**easyblocks**

* fix typos in WIEN2k easyblock (missing commas after list elements)

**easyconfigs**

* fixed source URL for ligtextutils (toolchain refactoring error)

v1.0.1 (November 24th 2012)
---------------------------

bugfix release

**framework**

* fix support for installing with ``distutils`` (broken import in ``setup.py``)
* fix support for ACML as a toolchain element (``toolchains/linalg/acml.py``)
* add name to aggregated regtest XML so that is parsed correctly by Jenkins
* reorder code in ``main.py`` so that regtest also works with incomplete easyconfig paths
* add bash script for running regression test and sending a trigger to Jenkins to pull in the XML with results
* get rid of assumption that loaded modules should have name like ``foo/bar``, make it more flexible
* retry failed builds in regtest twice to ignore fluke errors
* report leaf nodes in dependency graph when regtest is submitted

  * this is required for setting job dependencies in the regtest script for the Jenkins trigger job

* implement and use rmtree2 as more (NFS) robust replacement for ``shutil.rmtree``
* bump max hit count for ``run_cmd_qa`` from 20 to 50, to make false positives of unasnwered questions less likely

**easyblocks**

* fix support for installing with ``distutils`` (broken import in ``setup.py``)
* only build GMP/CLooG/PPL libraries during GCC build in parallel, don't install in parallel

  * ``make -j N install`` doesn't work consistently for GMP

* fix GCC build on OS X

  * location of libraries is slightly different (``lib`` vs ``lib64`` dir)

* add support to ``ConfigureMake`` easyblock for pre-passing tar options to configure

  * see ``tar_config_opts`` easyconfig parameter
  * workaround for issue with pax hanging ``configure`` with an interactive prompt

* enhance Q&A for WRF and WIEN2k by adding entries to ``qa`` dict and ``no_qa`` list
* use ``rmtree2`` from ``tools/filetools.py`` as more (NFS) robust replacement for ``shutil.rmtree``

**easyconfigs**

* remove patch file for OpenMPI to resolve issue with pax hanging configure

  * ``tar_config_opts`` should be enabled as needed

* disable parallel build for PAPI, seems to be causing problems

v1.0 (November 13th 2012)
-------------------------

* split up EasyBuild across three repositories: framework, easyblocks and easyconfigs
* packaged EasyBuild, different parts can now be installed easily using ``easy_install``

**framework**

* various changes to both internal and external API:

  * renamed main script to main.py (from ``build.py``)
  * file and directory organisation
  * module, class, function and function argument renaming and reorganisation
  * split up ``Application`` into ``EasyBlock`` and ``ConfigureMake`` (see easybuild-easyblocks for the latter)
  * created ``EasyConfig`` class for handling easyconfig files
  * renaming of EasyBuild configuration parameters (non-camelCase)
  * renaming of various easyconfig parameters (non-camelCase)
  * rename ``SOFTROOT`` and ``SOFTVERSION`` environment variables set in generated module files to ``EBROOT`` and ``EBVERSION``
  * use 'extension' as generic terminology for Python packages, R libraries, Perl modules, ...

* added support for building software packages in parallel via PBS jobs
* added unit testing framework and initial set of unit tests for basic functionality

  * and run them in Jenkins continuous integration service, see https://jenkins1.ugent.be/view/EasyBuild/

* implement single-command regression test (e.g. to test building all supported software)

  * eb ``--regtest`` --robot

* switch to new style Python classes
* replaced ``toolkit`` module with ``toolchain`` package (total rewrite), providing modular support for toolchains
* adjust default EasyBuild configuration to only use ``$HOME/.local/easybuild`` by default
* added support for running EasyBuild without supplying an easyconfig file

  * make EasyBuild search for a matching easyconfig file
  * support automatic rewriting of an existing partially-matching easyconfig file (use this with care!)
  * support for automatically generating an easyconfig file according to given specifications (best effort!)

* add support for looking for easyconfig file in Python search path if it can't be found on specified (relative) path
  (that way, easyconfig files available in the easybuild-easyconfigs package can be used easily)
* various other enhancements and bug fixes, e.g.:

  * extended sanity check capabilities
  * cleaned up logging
  * creating of devel module which allows to mimic environment that was used by EasyBuild to build the software
  * support for creating dependency graphs for a set of easyconfig files
  * grouped options in help output and categorised available easyconfig parameters
  * more consistent code style

**easyblocks**

* implement class name encoding scheme, see wiki http://github.com/hpcugent/easybuild/wiki/Encode-class-names

  * (non-generic) easyblock class names are now prefixed with ``EB_`` and non-alphanumeric characters are escaped

* split off generic easyblocks into separate package ``easyblocks.generic``
* added custom support for **39** software packages:

  * Armadillo, BiSearch, Boost, Bowtie2, BWA, bzip2, CGAL, CPLEX, DOLFIN, Eigen, flex, FSL, Hypre, libxml2, MetaVelvet,
    METIS, MTL4, MUMmer, ncurses, OpenFOAM, OpenSSL, ParMETIS, Pasha, PETSc, Primer3, python-meep, SAMtools, SCOTCH,
    SHRiMP, SLEPc, SOAPdenovo, SuiteSparse, SWIG, Tornado, Trilinos, UFC, Velvet, WIEN2k, XCrySDen

* various enhancements and bug fixes to existing easyblocks

**easyconfigs**

* added example easyconfig files for **106** new software packages:

  * AMOS, Armadillo, ASE, Autoconf, BiSearch, Boost, Bowtie2, BWA, byacc, bzip2, CGAL, ClustalW2, CMake,
    CPLEX, cURL, CVXOPT, Cython, Docutils, DOLFIN, ECore, Eigen, expat, FASTX-Toolkit, FFC, FIAT,
    freetype, FSL, GEOS, git, glproto, GMP, gmvapich2, gompi, GPAW, GSL, guile, h5py, h5utils, Harminv,
    hwloc, Hypre, Infernal, Instant, Jinja2, libctl, libdrm, libffi, libgtextutils, libmatheval,
    libpciaccess, libpthread-stubs, libreadline, libtool, libunistring, libxcb, libxml2, makedepend,
    matplotlib, Meep, Mercurial, Mesa, MetaVelvet, METIS, MPFR, MTL4, MUMmer, ncurses, OpenFOAM, OpenSSL,
    ORCA, PAPI, ParMETIS, Pasha, PCRE, PETSc, petsc4py, pkg-config, Primer3, python-meep, RNAz, SAMtools,
    ScientificPython, SCOTCH, setuptools, Shapely, SHRiMP, SLEPc, SOAPdenovo, Sphinx, SuiteSparse, SWIG,
    Tcl, Theano, Tk, Tornado, Trilinos, UFC, UFL, Velvet, ViennaRNA, Viper, WIEN2k, xcb-proto, XCrySDen,
    xorg-macros, xproto

* added additional example easyconfig files (versions, builds) for several software packages

  * Bison, BLACS, Doxygen, flex, GCC, HDF5, icc, ifort, libpng, M4, MVAPICH2, OpenMPI, Szip, tbb, zlib

* replaced GCC/OpenMPI based easyconfig files with equivalents using the `gompi` toolchain
  * ATLAS, BLACS, FFTW, LAPACK, ScaLAPACK

* enhanced Python example easyconfig files (more dependencies required for features, e.g. libreadline, bzip2, zlib, ...)
* corrected file name of easyconfig files to adher to standard as followed by EasyBuild robot dependency resolver
* style cleanup in existing easyconfig files

v0.8 (June 29th 2012)
---------------------

* added support for building/installing 17 additional software packages:

  * BEAGLE, Doxygen, g2clib, g2lib, HDF, HDF5, JasPer, libpng, Maple,
    MrBayes, NCL, netCDF, netCDF-Fortran, Szip, WPS, WRF, zlib

* the build procedure for WRF and WPS includes running the tests available for these packages
* various bug fixes and enhancements:

  * made support for interactive installers (``run_cmd_qa``) more robust
  * fixed Python git package check
  * implemented toolkit functions for determine compiler family, MPI type, MPI run command, ...

v0.7 (June 18th 2012)
---------------------

* fixed BLACS build

  * diagnostic tools to determine ``INTERFACE`` and ``TRANSCOMM`` values are now used

* added support for building Bison, CP2K, flex

  * with regression test enabled for CP2K as part of build process
  * note: BLACS built with EasyBuild prior to v0.7 needs to be rebuilt for CP2K to work correctly

* added ``--enable-mpi-threads`` to OpenMPI example easyconfigs

  * required for correct CP2K psmp build

* adjusted libsmm example easyconfig for lower build time

  * to make the full regression test finish in a reasonable amount of time

* added script to make porting of easyblocks from old to new EasyBuild codebase easier

  * takes care of refactoring, checks for PyLint warnings/errors, ...

* fixed several small bugs
* prefixed EasyBuild messages with ``==``
* full regression test passed (58 easyconfigs tested)

v0.6 (May 11th 2012)
--------------------

* added support for Intel compiler toolkit (ictce)

  * which included the Intel compilers, Intel Math Kernel Library (imkl) and Intel MPI library (impi)

* added support for building Python with nose/numpy/scipy packages
* added simple regression test
* this version is able to build all supplied example easyconfigs

v0.5 (April 6th 2012)
---------------------

* first public release of EasyBuild

  * after a thorough cleanup of the EasyBuild framework of the in-house version

* supports building HPL with goalf compiler toolkit

  * the goalf toolkit consists of the GCC compilers, and the OpenMPI, ATLAS, LAPACK, FFTW and ScaLAPACK libraries

* also support build and installation of MVAPICH2
