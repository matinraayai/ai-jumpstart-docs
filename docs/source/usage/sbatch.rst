Using ``sbatch``
================================

Much like ``srun``, ``sbatch`` is also a utility for allocating parallel jobs on a partition; In contrast to ``srun``,
however, ``sbatch``'s resource specification is done inside a bash script instead of the command line.
:external:doc:`using-discovery/srun` and :external:doc:`using-discovery/workingwithgpu` include examples usages of ``sbatch``
both with and without a GPU. Usage of GPUs with Tensorflow and Pytorch is covered in :doc:`../software/tensorflow`
and :doc:`../software/pytorch`, respectively.
Here we cover ``sbatch`` commands specific to the ``ai-jumpstart`` partition.

Using Nvidia DGX Nodes
++++++++++++++++++++++
To specify all the available resources to a single DGX node for a script to run on the ``ai-jumpstart`` partition via
``sbatch``, prepend the following to the beginning of the script::

  #SBATCH --export=ALL
  #SBATCH -t 1-0
  #SBATCH --exclusive
  #SBATCH --job-name=MyAIJumpstartJob
  #SBATCH --partition=ai-jumpstart
  #SBATCH --nodes 1
  #SBATCH -c 256
  #SBATCH --constraint=dgx
  #SBATCH --gres-gpu:a100:8
  #SBATCH --mem=1024Gb
  #SBATCH -o my_ai_jumpstart_job_%j.out
  #SBATCH -e my_ai_jumpstart_job_%j.err
  <your bash script commands here>

The above epilogue is exactly the same as what was covered in :doc:`srun`, except that every option is now
listed with ``#SBATCH`` prepended to it. A few notable differences are:
   * Addition of redirection of standard output and error using the ``-o`` and ``-e`` flags. the ``%j`` specifier
     will be replaced by the job id. Note that these options can also be used by ``srun`` too, but are rarely used that way.
   * Absence of ``--pty``, which means the requested job will not be interactive. ``sbatch`` scripts can
     have the interactive option specified, in which case the redirection of standard output and error should be removed
     for it to work properly.

To review what the other options do in the above script, see :doc:`srun`.

It is still worth iterating that the above allocation is usually more than enough for most tasks, and AI Jumpstart
users are recommended to use about half the resources available to each DGX node or less, without the ``--exclusive`` option to allow
for 2 people or more to use each DGX node.

Using AMD ROCm Nodes
++++++++++++++++++++++
Similar to the DGX node command, prepend the following to the beginning of your script to allocate all the resources
available to a single ROCm node for your job::

  #SBATCH --export=ALL
  #SBATCH -t 1-0
  #SBATCH --exclusive
  #SBATCH --job-name=MyAIJumpstartJob
  #SBATCH --partition=ai-jumpstart
  #SBATCH --nodes 1
  #SBATCH -c 32
  #SBATCH --constraint=rocm
  #SBATCH --mem=512Gb
  #SBATCH -o my_ai_jumpstart_job_%j.out
  #SBATCH -e my_ai_jumpstart_job_%j.err
  <your bash script commands here>


Again, keep in mind that unlike the DGX nodes, there is no ``gres`` specification and a single node automatically takes over
the resources of the whole node.
