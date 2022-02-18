Accessing the Discovery Cluster via Open OnDemand (OOD)
=======================================================

Open OnDemand (OOD) is a web portal to the Discovery cluster. See :external:doc:`first_steps/connect_ood` for more information.

.. note::
   OOD is currently unable to launch GUI applications or XFCE sessions on the AI Jumpstart cluster. Any
   interactive GUI job requested with OOD will use non-exclusive partitions other than AI Jumpstart
   (e.g. ``short``, ``express`` if no GPU is specified, and ``gpu`` if a GPU is requested with the job).
   Other functionality (excluding course-specific jobs for Northeastern students)
   available via OOD should work as intended for AI Jumpstart users. For more details see
   :external:doc:`using-ood/introduction`, :external:doc:`using-ood/fileexplore`, and
   :external:doc:`using-ood/interactiveapps`.

