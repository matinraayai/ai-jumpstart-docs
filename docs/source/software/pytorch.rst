Using Pytorch on the AI Jumpstart Cluster
=========================================
Pytorch can be run on both AMD ROCm nodes and NVIDIA DGX nodes to carry out training of deep learning models with single
and multiple GPUs. The following sections explain the requirements to get Pytorch working on the AI-Jumpstart partition.
For more information on working with Pytorch, visit Pytorch's `documentation <https://pytorch.org/docs/stable/index.html>`.

AMD ROCm Nodes
++++++++++++++
To run Pytorch on an AMD ROCm node:

  1. Allocate a ROCm node via Slurm. See :doc:`../usage/sbatch` and :doc:`../usage/srun` for more information.
  2. Load the ROCm stack via ``module load``. See :doc:`rocm` for more information.
  3. Create a conda environment and activate it. See :external:doc:`software/conda` for details.
  4. Install Pytorch with the ROCm version matching the one loaded using ``module load``. Instructions on how to install
     Pytorch with ROCm support is available on the `Pytorch website <https://pytorch.org/>`_.
  5. Run the following command to confirm HIP support is available ``python -c'import torch; print(torch.cuda.is_available(), torch.cuda.device_count());'``

Which should return ``True, 8``, indicating that GPU support is available and all 8 GPUs on the node are detected.
Note that Pytorch reuses the CUDA interface for its HIP support for easier porting of existing code.No other step should
be required to do multi-GPU training on the node. See
`Pytorch's HIP usage webpage <https://pytorch.org/docs/stable/notes/hip.html>`_ for more information on using HIP
with Pytorch, and `PyTorch Distributed Overview <https://pytorch.org/tutorials/beginner/dist_overview.html>`_ for
information on distributed training on multiple GPUs.


NVIDIA DGX Nodes
++++++++++++++++
To run Pytorch on an NVIDIA DGX node:

  1. Allocate a DGX node via Slurm. See :doc:`../usage/sbatch` and :doc:`../usage/srun` for more information.
  2. Load the latest compatible CUDA version via ``module load``. See :doc:`cuda` for more information.
  3. Create a conda environment and activate it. See :external:doc:`software/conda` for details.
  4. Install Pytorch with a version compatible with the CUDA version loaded in the previous step. Instructions on how to install
     Pytorch with CUDA support is available on the `Pytorch website <https://pytorch.org/>`_.
  5. Run the following command to confirm CUDA support is available: ``python -c'import torch; print(torch.cuda.is_available(), torch.cuda.device_count());'``

Which should return ``True,`` followed by the number of GPUs allocated with Slurm.
No other step should be required to do multi-GPU training on the node. See `PyTorch Distributed Overview <https://pytorch.org/tutorials/beginner/dist_overview.html>`_ for
information on distributed training on multiple GPUs.

