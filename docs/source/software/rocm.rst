
Using ROCm on AMD Nodes
=======================

Loading ROCm Modules on Discovery
+++++++++++++++++++++++++++++++++
The ROCm stack version 4.2 is available as a module for AMD nodes of AI Jumpstart. To load it on an AMD node, run::

  module load rocm

To check if the ``rocm`` module is correctly loaded, run ``rocm-smi`` to view the GPUs attached to the system. For more
information on modules, see :external:doc:`software/modules`.

Installing ROCm via ``spack``
+++++++++++++++++++++++++++++
The pre-loaded ROCm module is stable and should be enough for running deep-learning based tasks. If you require a
different version of the ROCm stack, use ``spack`` to install your ROCm version of choice locally.
To learn how to use ``spack`` on Discovery, see :external:doc:`software/spack`.
Below are some of ROCm tools provided through `spack <https://www.reddit.com/r/ROCm/comments/kcq5ax/spack_v0160_install_package/>`_:

* **Base ROCm Packages** ``hsakmt``, ``hsakmt-roct``, ``llvm-amdgpu``, ``rocm-cmake``, ``rocm-smi``, ``rocm-smi-lib``.

* **ROCm APIS and Tools** ``hsa-rocr-dev``, ``rccl``, ``rocm-bandwidth-test`` ``rocm-clang-ocl``, ``rocm-device-libs``,
  ``rocm-opencl``, ``rocminfo``.

* **ROCm Developer Tools** ``hip``, ``hip-rocclr``, ``hipify-clang``, ``rocm-dbgapi``, ``rocm-debug-agent``,
  ``rocm-gdb``, ``rocm-validation-suite``, ``rocprofiler-dev``, ``roctracer-dev``.

* **ROCm Software Platform and GPUOpen Professional Compute Packages** ``hipblas``, ``hipcub``, ``hipfort``,
  ``hipsparse``, ``migraphx``, ``miopen-hip``, ``miopen-opencl``, ``rocblas``, ``rocfft``, ``rocprim``, ``rocrand``,
  ``rocsolver``, ``rocsparse``, ``rocthrust``.

To install a ``spack`` ROCm stack package locally:

1. Use ``spack info <rocm_package>`` to view information on each ROCm package, including the versions available and
required dependencies.
2. If a dependency is available as a module on Discovery, first load it via ``module load <module_name>/<module_version>``
   first, and then run ``spack external find`` to register it with ``spack``, or let ``spack`` install them locally if it is not able to find them.
   Notable dependencies for the ROCm stack are ``cmake`` and ``gcc``.
3. Finally, run ``spack install <rocm_package>@<package_version>`` to install it.

To use the Installed ROCm package, run ``spack load <rocm_package>`` to load the default version of the package
installed. If a **pre-installed Discovery module** was used to install a package, make sure to **load it** via
``module load``. Make sure that **no ROCm modules from Discovery are not loaded** to avoid conflicts.

.. attention::
   ``Spack`` compiles each package from scratch, and compilation of the ROCm stack requires a compiler with support for the
   C++17 standard, not supported by the default ``gcc`` compiler on the Discovery cluster. Be sure to load a newer version
   of ``gcc`` via ``module load`` before installing a ROCm package via ``spack``.

.. caution::
   If ``spack`` is not able to find a dependency available on your system (in ROCm's case, ``gcc`` or ``cmake``),
   it will revert to compiling it from scratch and storing it in your storage quota.
   Storage on the Discovery cluster is limited, and locally installed ``spack`` packages will reduce your storage quota.
   Only install software locally if it's justified for your use case. If you install packages locally, leverage the
   available modules on the Discovery cluster to minimize ``spack``'s disk usage.