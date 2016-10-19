Lab 1: Run a container 
======================

All commands from this lab will also be provided as a text file.  You may want to download this file first and copy-and-paste the following commands. the commands are in a file on your desktop called *Intro to Docker.sh*. You may edit it by doing a right click on edit and select *Edit with Notepad++*

.. image: ../images/Intro-docker-cmds.png
   :scale: 50 %
   :align: center

The first lab is an example of migrating an application to run in a container. 

Goals of the lab

1. Learn how to launch an existing container
2. Create your own container
3. Distribute your container 

The legacy Application
----------------------

One of the use-cases for utilizing containers is to migrate an existing on-premises application to first run in a container and eventually migrate the container to run in a public cloud environment.  The first lab will migrate the existing app that is running at: http://mesos-agent01/

Launch Chrome and visit **http://mesos-agent01** (make sure to enter *http://*)

.. image:: ../images/www-legacy-app.png
   :scale: 50%
   :align: center

10.1.20.101 is one of agent01 IP addresses. You can check this by typing **ifconfig eth1** in your putty session

.. image:: ../images/ifconfig-eth1.png
   :scale: 50%
   :align: center

The first step of this lab is to download a container that has a more recent version of PHP.  Note that PHP 5.5 is already an End of Life version of PHP!

Docker Pull
-----------

Normally you would run the command **docker pull [image]:[tag]** to pull down a public image of a container.  This is similar to going to the F5 Downloads site to grab the latest vLab or ISO, but it doesn't require any authentication.  This is an example of a low-friction method of obtaining software that is appealing to Mode 2 users.

The *Docker Hub* (transition to *Store*) has a listing of community images that are available.  Visit **https://hub.docker.com/** and search for *php*.

.. image:: ../images/docker-hub.png
   :scale: 50 %
   :align: center

You'll see a long list of available versions of PHP that can be downloaded.

In this lab, we have already downloaded the required containers.  You can view the available containers by running the command::

  docker images


.. image:: ../images/lab1-docker-image-cmd.png
   :scale: 50 %
   :align: center

For the lab we have retrieved *php:5.6-apache* and *php:7-apache*.  These represent containers that can run PHP 5.6 / 7 running on the Apache web server (httpd).

.. warning:: 
   |For your information, if the user doesn't have the proper privileges, you'll see something like this: 
   |*Cannot connect to the Docker daemon. Is the docker daemon running on this host?*
   |In case of this error, you can either run as root or use the sudo command, i.e. **sudo docker images**
   |In this lab, it should not be the case.  We have added the user *user*  to the docker unix group to enable it to be able to run these commands as a non-root user.



