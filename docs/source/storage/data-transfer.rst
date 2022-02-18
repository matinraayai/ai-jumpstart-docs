Data Transfer on AI Jumpstart
=============================
There are two primary options for transferring data between the Discovery cluster and your local machine:

* For small to medium-sized file, use the data transfer nodes on the Discovery cluster available at ``xfer.discovery.neu.edu``.
  See :external:doc:`using-discovery/transferringdata` for more information on how to use it.
* For large data files, use `Globus <https://www.globus.org/globus-connect>`_. See :external:doc:`using-discovery/globus` for
  more information.

.. attention::
   Login nodes are only for connecting to the Discovery cluster. They are not meant to run any kind of compute jobs or
   transferring files. Use the the methods above for transferring files between your local machine and the Discover
   cluster.