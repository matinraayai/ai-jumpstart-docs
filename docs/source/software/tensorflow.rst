Using Tensorflow on the AI Jumpstart Cluster
============================================

Tensorflow can be run on NVIDIA DGX nodes to carry out training of deep learning models with single
and multiple GPUs. The following sections explain the requirements to get Tensorflow working on the AI-Jumpstart partition.
For more information on working with Tensorflow, visit Tensorflow's `documentation <https://pytorch.org/docs/stable/index.html>`.


NVIDIA DGX Nodes
++++++++++++++++
To run Pytorch on an NVIDIA DGX node:

  1. Allocate a DGX node via Slurm. See :doc:`../usage/sbatch` and :doc:`../usage/srun` for more information.
  2. Load the latest compatible CUDA version via ``module load``. See :doc:`cuda` for more information.
  3. Create a conda environment and activate it. See :external:doc:`software/conda` for details.
  4. Install Tensorflow using pip: ``pip install tensorflow``. Instructions on how to install
     Tensorflow with CUDA support is available on the `Tensorflow website <https://www.tensorflow.org/install/gpu>`_.
  5. If the loaded CUDA module does not include CuDNN (versions prior to 11.4), install CuDNN locally on your machine.
     See :doc:`cuda` for more details.
  5. Run the following command to confirm CUDA support is available: ``python -c'import tensorflow as tf;  print(tf.test.gpu_device_name());'``

Which should list the GPUs available on your machine, allocated via Slurm.

