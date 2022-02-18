Software Usage
===============

Loading and Installing Software
+++++++++++++++++++++++++++++++
By default every allocated compute node with Slurm comes with only essential system software.
The software required to run the compute job needs to be loaded explicitly by the user. The following are available
options for getting a piece of software to run on the AI Jumpstart partition:

1. Use the ``module`` command to view the available pre-packaged software provided by the RC Discovery team, and load
   it. For more information on modules, see :external:doc:`software/modules`.
2. If the desired software is not installed, look it up in ``spack`` repository and install it if available. See
   :external:doc:`software/spack` for more information.
3. If the desired software is not packaged with ``spack``, check the software provider's documentation to see if
   local installation is available; Or see if a containerized version of the software is available to
   use with **Singularity**. Singularity is available as a module on the Discovery cluster. Use ``module avail singularity``
   to view available versions, and use ``module load singularity`` to load the default version. For more information
   on how to build, download, or run containers on Singularity, visit Singularity's
   `documentation page <https://sylabs.io/guides/3.5/user-guide/index.html>`_.

.. caution::
    If opting for a local installation option like ``spack`` or a Singularity container, be mindful of the installation
    location as storage on the cluster is limited. See :external:doc:`storage/discovery_storage` for more information.

.. attention::
    As of right now the Open OnDemand (OOD) service cannot run GUI jobs on the AI Jumpstart cluster.
    Jobs scheduled with OOD will run on public partitions of Discovery, not the AI Jumpstart partition.


Information on Frequently Used Software on Discovery
+++++++++++++++++++++++++++++++++++++++++++++++++++++
The Northeastern RC Documentation page also has documentation for running popular software on the Discovery cluster.
See :external:doc:`software/r`, :external:doc:`software/matlab`, :external:doc:`software/conda`, and
:external:doc:`software/mpi`.

