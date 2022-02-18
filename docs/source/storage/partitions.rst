Storage Systems on AI Jumpstart
================================

All users of the Discovery cluster, including the users of AI Jumpstart,
have access to two main storage systems: ``/home`` and ``/scratch``.
For AI Jumpstart users, a folder under ``/work/ai-jumpstart/`` is also available as an additional storage option. Each
option has specific quotas and limitations that are listed below:


* ``/home/$USER`` is the home directory available to each Discovery account. It should be used for storing relatively
  small files such as script files, source code, software installation files, and other small files to work with the cluster.
  It only as a **75 GB** qouta, and is not performant. It is however, backed up and replicated frequently.
  For running jobs and directing output files, you should use your ``/scratch`` directory.

.. tip::
  Use the ``du -h <dir>`` to list the storage usage of each file in ``<dir>`` and find big unnecessary files to remove.

* ``/scratch/$USER`` is the scratch space allocated to each user of the Discovery cluster. Scratch is shared with all
  users, and there is a total of 1.8PB available on scratch. It is performant, and users should use it to run their jobs.
  It is however, for temporary use only and **is not backed up**. Data on ``/scratch`` should be either downloaded
  from Discovery or stored in the ``/work`` partition, or else it could potentially be purged after 28 days. For more
  information on the ``/scratch`` policy, visit RC's `policy page <https://rc.northeastern.edu/policy/>`_.

* ``/work/ai-jumpstart/$USER`` is additional permanent storage allocated for users of AI Jumpstart. Persistent data required
  for running jobs or obtained from jobs should be moved here after usage of ``/scratch``.