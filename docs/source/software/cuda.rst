Using CUDA on DGX Nodes
=======================

Loading CUDA Modules on Discovery
+++++++++++++++++++++++++++++++++
Several versions of CUDA come pre-installed as modules that can be loaded for use on the DGX nodes. Use ``module avail cuda``
to view available versions of CUDA and load them using ``module load cuda/<cuda_version>``. To check if the module has
been loaded, run ``nvcc --version`` to check if you have access to the NVCC compiler, and if its version matches the loaded
CUDA version. For more information on modules, see :external:doc:`software/modules`.

Installing CUDA via ``spack``
+++++++++++++++++++++++++++++
The Discovery cluster has the most recent and stable versions of CUDA installed. If the desired version is not available,
local installation via ``spack`` is possible. To learn how to use ``spack`` on Discovery, see :external:doc:`software/spack`.
Use ``spack info cuda`` to look for available versions of CUDA, and install the desired version via
``spack install cuda@<cuda_version>``. After installation, load it via ``spack load cuda``.

.. attention::
   The DGX nodes only support the CUDA version equals or less than what the node's NVIDIA Driver supports. Run
   ``nvidia-smi`` on a DGX node to check the CUDA version supported by the driver. It is still possible to install a
   higher CUDA version via ``spack`` and even use the development tools of the higher version. However,
   applications compiled for it will not run.

Using CuDNN
+++++++++++
CuDNN is available with the latest CUDA installation on the Discovery cluster. Loading the latest CUDA module will automatically
make CuDNN available to its user. For older versions of CUDA, however, CuDNN might not be available in the CUDA module. In
that scenario users are recommended to install it locally via ``spack``.

To install CuDNN locally with ``spack``:
1. Load the desired CUDA version with ``module load cuda/<cuda_version>``.
2. Register the loaded ``cuda`` package with ``spack`` by running ``spack external find cuda``. Confirm that the CUDA
version found by ``spack`` is the same as the one loaded.
3. Run ``spack info cudnn`` to find the available versions of CuDNN. Select the version of CuDNN that is supported by
the loaded CUDA version; For example, the latest version of CuDNN supported by CUDA 11.3 is ``8.2.0.53-11.3``.
4. Install the target CuDNN package by running ``spack install cudnn@<cudnn_version>``. ``spack`` should automatically
use the external CUDA as the dependency.

To load the locally installed CuDNN, run ``spack load cudnn@<cudnn_version>``. Be sure to load the external CUDA module
beforehand via ``module load cuda/<cuda_version>``.


Using NCCL
++++++++++
NCCL is not provided as a module on the Discovery cluster and users must install it locally either using ``spack`` or
manually form the `NVIDIA Developer Website <https://developer.nvidia.com/nccl/>`_.

To install NCCL via ``spack``:
1. Load the desired CUDA version with ``module load cuda/<cuda_version>``.
2. Register the loaded ``cuda`` package with ``spack`` by running ``spack external find cuda``. Confirm that the CUDA
version found by ``spack`` is the same as the one loaded.
3. Run ``spack info nccl`` to find the available versions of NCCL. Select the version of NCCL that is supported by
the loaded CUDA version; For example, the latest version of NCCL supported by CUDA 11.4 is ``2.11.4-1``.
4. Install the target NCCL package by running ``spack install nccl@<nccl_version>``. ``spack`` should automatically
use the external CUDA as a dependency.

To load the locally installed NCCL, run ``spack load nccl@<nccl_version>``. Be sure to load the external CUDA module
beforehand via ``module load cuda/<cuda_version>``.