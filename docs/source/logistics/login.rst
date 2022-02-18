Logging In to Discovery From Command Line
=========================================

Windows and Mac
---------------
The process of logging in to the Discovery cluster for Mac and Windows operating systems is documented by in the
following pages provided by `Northeastern Research Computing <https://rc-docs.northeastern.edu/en/latest/>`_:

* :external:doc:`first_steps/connect_windows`
* :external:doc:`first_steps/connect_mac`

Linux
-----
A Discovery account is required to be able access the Discovery cluster. If you already don't have one see :doc:`create`.

The process of logging in to the Discovery cluster with Linux is very similar to Mac listed in :external:doc:`first_steps/connect_mac`:

1. Make sure that an SSH client is installed on your machine. Some popular examples are
   the `Openssh Client <https://www.openssh.com/>`_ and `Putty <https://www.putty.org/>`_.
2. Login to the Discovery cluster using the command ``ssh <username>@login.discovery.neu.edu`` where the
   ``<username>`` is your Northeastern username.
3. Type your Northeastern password and press enter.

This will connect you to a login node on the Discovery cluster.


.. _using_x11:

Using X11
++++++++++
You can use software with graphical user interface (GUI) on the Discovery cluster from the command line via X11 forwarding.
X11 forwarding is disabled by default. To enable it for your session simply add the ``-X`` option to the login command.

.. tip::
   You can test if X11 forwarding is working properly by running ``xeyes``. This will run a small program that makes
   a pair of eyes appear to follow your cursor.

.. _port_forwarding:

Remote Port Forwarding
++++++++++++++++++++++
To forward traffic from a remote login node on Discovery to your local machine (also known as remote port forwarding),
pass the ``-L <local_port>:localhost:<remote_port>`` option to the login command. ``<local_port>`` is a free
port on your local machine, and ``<remote_port>`` is a free port on the Discovery login node.
This comes in handy for running remote software like Jupyter Lab to access via your local web browser.

Passwordless SSH
+++++++++++++++++
Password-less SSH can be used to login to Discovery without entering your password. It can also be used for
password-less authentication in-between compute nodes on the AI-Jumpstart, given you have active jobs on them.
This becomes useful in scenarios like multi-node training of deep learning models.
Password-less SSH might also ensure that some GUI-based applications will launch without any issues.

The process of setting up password-less SSH is covered in :external:doc:`first_steps/connect_mac` for Mac OS and is
identical for a Linux machine.

.. note::
   Steps 1 to 7 of password-less SSH section in :external:doc:`first_steps/connect_mac` is for password-less access
   from your local machine to a login node. Steps 8 - 12 is for ensuring password-less access between login nodes and
   any compute nodes running your jobs.



.. attention::
   Login nodes are only for connecting to the Discovery cluster. They are not meant to run any kind of compute jobs or
   transferring files. See :doc:`../storage/data-transfer` for instructions on how to transfer data
   on Windows and Mac(Unix) to and from the Discovery cluster.

Working with Bash on Discovery
++++++++++++++++++++++++++++++
The Discovery cluster runs on CentOS Linux, with Bash as its default Shell. See :external:doc:`first_steps/bashrc` for
useful tips for configuring your Bash environment on Discovery.
