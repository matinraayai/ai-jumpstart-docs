
Using ROCm on AMD Nodes
=======================

Loading ROCm Modules on Discovery
+++++++++++++++++++++++++++++++++
The ROCm stack version 4.2 is available as a module for AMD nodes of AI Jumpstart. To load it on an AMD node, run::

  module load rocm

To check if the ``rocm`` module is correctly loaded, run ``rocm-smi`` to view the GPUs attached to the system.

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

Use ``spack info <rocm_package>`` to view information on each ROCm package, including the versions available, and then
run ``spack install <rocm_package>@<package_version>`` to install it. After installation, run ``spack load <rocm_package>``
to load the default version of the package installed. Make sure that **no ROCm modules from Discovery are not loaded**
to avoid conflicts.

.. attention::
   ``Spack`` compiles each package from scratch, and compilation of the ROCm stack requires a compiler with support for the
   C++17 standard, not supported by the default ``gcc`` compiler on the Discovery cluster. It is recommended to
   first install the latest ``gcc`` via spack and register it as the compiler of choice for ``spack`` by running
   ``spack compiler find``. Compiling with pre-installed compiler modules is possible, but need to be loaded each time
   prior to using the ROCm package manually, and therefore is not recommended.