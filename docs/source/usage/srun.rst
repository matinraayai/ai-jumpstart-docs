Using ``srun``
==============

``srun`` is a Slurm utility for allocating parallel jobs on a partition. :extern:doc:`using-discovery/srun` and
:extern:doc:`using-discovery/workingwithgpu` include examples usages of ``srun`` both with and without a GPU.
Usage of GPUs with Tensorflow and Pytorch is covered in :doc:`../software/tensorflow` and :doc:`../software/pytorch`,
respectively.
Here we cover ``srun`` commands specific to the ``ai-jumpstart`` partition.

Using Nvidia DGX Nodes
++++++++++++++++++++++
To run an interactive shell on the ``ai-jumpstart`` cluster exclusively with all the resources available to a single node,
run the following on a Discovery login node::

  srun --pty --export=ALL -t 1-0 --exclusive --partition=ai-jumpstart --nodes 1 -c 256 --constraint=dgx --gres=gpu:a100:8  --mem=1024Gb /bin/bash

The above command:
   * Creates an interactive job by using the option ``--pty`` and specifying ``/bin/bash`` as the program of choice.
   * Exports all the environment variables of the calling environment (the login node) via the ``--export=ALL`` option.
   * Sets a time limit of one day on the job via the ``-t 1-0`` option, which after that, the job terminates automatically.
   * Creates the job in exclusive mode with ``--exclusive``.
   * Allocates the job on the AI Jumpstart partition with ``--partition=ai-jumpstart``, constraining it only to the NVIDIA
     DGX nodes with ``--constraint=dgx``.
   * Allocates a single node for the job with ``--nodes 1``.
   * Allocates all the cores available to a single DGX node with ``-c 256``
   * Specifies 8 Nvidia A100 GPUs for the job using the ``--gres:gpu:a100:8`` flag.
   * Requests all 1 TB memory via ``--mem=1024Gb``.

This allocation is usually (very) overkill for most tasks, and takes away one out of 5 DGX nodes available to the users
of the AI Jumpstart partition. Therefore, out of courtesy,
allocate only about half the resources available to each DGX node or less, without the ``--exclusive`` option to allow
for 2 people or more to use each DGX node.

Using AMD ROCm Nodes
++++++++++++++++++++++
Similar to the DGX node command, use the following command to allocate all the resources available to a single ROCm
node::

   srun --pty --export=ALL --exclusive -t 1-0 --partition=ai-jumpstart --nodes 1 --constraint=rocm  --mem=512Gb /bin/bash

Keep in mind that unlike the DGX nodes, there is no ``gres`` specification and a single node automatically takes over
the resources of the whole node. This is not a big problem as we have 14 of these nodes available to our users.

.. tip::
   The ``srun`` utility is great for allocating interactive jobs for active usage and prototyping,
   or short-lived jobs that run quickly. For longer-lived tasks like training a Deep Learning model,
   it is recommended to use ``sbatch`` instead of ``srun`` to save the standard output and error streams of the
   program into files on the file system to be monitored separately to avoid premature killing of your job due to
   connectivity issues and better documentation.