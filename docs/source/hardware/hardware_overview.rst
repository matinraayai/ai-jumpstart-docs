Overview of Hardware Available on AI Jumpstart
==============================================
The AI Jumpstart cluster has the following machines available:

+---------------+----------------------------------+-----------------+---------------------+--------------------+----------+-----------------+
| CPU           | Number of CPUs/CPU Cores/Threads |    GPUs (#)     |   GPU Interconnect  | Node Interconnect  |   RAM    | Node Names (#)  |
+===============+==================================+=================+=====================+====================+==========+=================+
| AMD EPYC 7302 | 1 CPU / 16 cores / 32 threads    | AMD MI-50 (8)   | AMD Infinity Fabric | HDR 200 Infiniband |  1 TB    | d31(46-50) (5)  |
+---------------+----------------------------------+-----------------+---------------------+--------------------+----------+-----------------+
| AMD EPYC 7742 | 2 CPUs/ 128 cores / 128 threads  | Nvidia A100 (8) |   Nvidia NVSwitch   | HDR 200 Infiniband | 512 GB   | d31(51-64) (14) |
+---------------+----------------------------------+-----------------+---------------------+--------------------+----------+-----------------+

These machines reside inside a partition named ``ai-jumpstart`` inside the Discovery cluster. In the usage sections
:doc:`../usage/sbatch`, :doc:`../usage/slurm`, and :doc:`../usage/srun` it is described in detail how to use this to allocate
a job on the AI Jumpstart cluster.

.. note::
   Besides the ``ai-jumpstart`` partition, your Discovery account can also use the general access partitions.
   Run the convenience script ``partition-info`` to list the partitions your account has access to,
   and run ``partition-info <partition-name>`` to list the nodes and resources available to each node inside the partition.
   It is **highly recommended** for external users to only use general access compute nodes for light tasks as the
   resources and the computational power of these nodes are limited.
   See :external:doc:`hardware/hardware_overview` and :external:doc:`hardware/partitions` for more details.


