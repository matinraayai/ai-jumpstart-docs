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
Port Forwarding
++++++++++++++++


Passwordless ssh
+++++++++++++++++
Passwordless SSH can be used to login to Discovery without entering your password. Passwordless SSH might
also ensure that GUI-based applications will launch without any issues.


.. caution::
   Login nodes are only for connecting to the Discovery cluster. They are not meant to run any kind of compute jobs or
   transferring files bigger than 100 MBs.